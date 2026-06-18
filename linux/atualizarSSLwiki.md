---
layout: default
title: Atualização de Certificado SSL da Wiki Infraero
---

# Atualização de Certificado SSL da Wiki Infraero (WikiJS + Docker + Nginx)

## Objetivo

Atualizar o certificado SSL utilizado pela Wiki Infraero (`wiki.infraero.gov.br`) hospedada em containers Docker utilizando Nginx como proxy reverso.

---

# Ambiente

Servidor:

```bash
s-sesu200.infraero.gov.br
```

Containers:

```bash
wikijs_nginx
wikijs
wikijs_db
```

Arquivos de certificado utilizados pelo Nginx:

```bash
/opt/wikijs/certs/wiki.crt
/opt/wikijs/certs/wiki.key
```

Mapeamento Docker:

```bash
/opt/wikijs/certs:/etc/nginx/certs:ro
```

---

# 1. Verificar validade do certificado atual

Executar:

```bash
docker exec -it wikijs_nginx openssl x509 \
-in /etc/nginx/certs/wiki.crt \
-noout -dates -issuer -subject
```

Exemplo:

```text
notBefore=May 9 21:27:04 2025 GMT
notAfter=Jun 7 18:52:08 2026 GMT
subject=CN=*.infraero.gov.br
issuer=GlobalSign RSA OV SSL CA 2018
```

Caso a data `notAfter` esteja expirada, realizar a atualização.

---

# 2. Localizar novo certificado

Exemplo de diretório recebido da equipe responsável:

```bash
/tmp/cert2026
```

Conteúdo:

```text
0_Infraero_OrganizationSSL_2026.cer
cadeia_completa_globalsign.pem
infraero.gov.br.pem
infraero_certificado_2026.key
```

Verificar validade:

```bash
openssl x509 \
-in /tmp/cert2026/infraero.gov.br.pem \
-noout -dates -subject -issuer
```

Exemplo:

```text
notBefore=Apr 28 17:54:04 2026 GMT
notAfter=Nov 13 17:54:04 2026 GMT
subject=CN=*.infraero.gov.br
```

---

# 3. Validar se certificado e chave correspondem

Verificar hash do certificado:

```bash
openssl x509 -noout -modulus \
-in /tmp/cert2026/infraero.gov.br.pem | openssl md5
```

Verificar hash da chave:

```bash
openssl rsa -noout -modulus \
-in /tmp/cert2026/infraero_certificado_2026.key | openssl md5
```

Os hashes devem ser idênticos.

Exemplo:

```text
MD5(stdin)= 851dbad6e7a519412df992c58f7c01e5
MD5(stdin)= 851dbad6e7a519412df992c58f7c01e5
```

---

# 4. Realizar backup do certificado atual

```bash
cd /opt/wikijs/certs

cp wiki.crt wiki.crt.bkp-$(date +%F)
cp wiki.key wiki.key.bkp-$(date +%F)
```

---

# 5. Atualizar arquivos

Substituir o certificado antigo:

```bash
cp /tmp/cert2026/infraero.gov.br.pem \
/opt/wikijs/certs/wiki.crt

cp /tmp/cert2026/infraero_certificado_2026.key \
/opt/wikijs/certs/wiki.key
```

Ajustar permissões caso necessário:

```bash
chmod 644 /opt/wikijs/certs/wiki.crt
chmod 600 /opt/wikijs/certs/wiki.key
```

---

# 6. Validar configuração do Nginx

Executar:

```bash
docker exec wikijs_nginx nginx -t
```

Resultado esperado:

```text
syntax is ok
test is successful
```

---

# 7. Recarregar Nginx

Sem necessidade de reiniciar os containers:

```bash
docker exec wikijs_nginx nginx -s reload
```

---

# 8. Validar novo certificado publicado

Executar:

```bash
openssl s_client \
-connect wiki.infraero.gov.br:443 \
</dev/null 2>/dev/null | \
openssl x509 -noout -dates -subject
```

Resultado esperado:

```text
notBefore=Apr 28 17:54:04 2026 GMT
notAfter=Nov 13 17:54:04 2026 GMT
subject=CN=*.infraero.gov.br
```

---

# 9. Verificar cadeia de certificação

Executar:

```bash
openssl s_client \
-connect wiki.infraero.gov.br:443 \
-servername wiki.infraero.gov.br
```

Resultado esperado:

```text
Verify return code: 0 (ok)
```

---

# Troubleshooting

## Certificado e chave incompatíveis

Erro:

```text
certificate and private key do not match
```

Verificar novamente os hashes MD5 do certificado e da chave.

---

## Certificado expirado

Verificar:

```bash
openssl x509 -in wiki.crt -noout -dates
```

---

## Navegador exibindo "Inseguro"

Validar:

* Certificado atualizado.
* Cadeia completa da GlobalSign instalada.
* Cache do navegador limpo.
* Ausência de conteúdo misto (HTTP dentro de página HTTPS).

---

# Evidência de sucesso

```bash
curl -kI https://wiki.infraero.gov.br
```

Resultado:

```text
HTTP/1.1 200 OK
```

```bash
openssl s_client -connect wiki.infraero.gov.br:443
```

Resultado:

```text
Verify return code: 0 (ok)
```

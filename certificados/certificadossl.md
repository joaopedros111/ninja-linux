# Atualização de Certificado SSL no Harbor (Docker) - Rocky Linux

## Objetivo

Realizar a atualização do certificado SSL do Harbor executado em containers Docker, validando a cadeia de certificados, a chave privada e o funcionamento do serviço após a troca.

---

## Ambiente

* Sistema Operacional: Rocky Linux
* Harbor: 2.13.2
* Docker Compose
* Nginx (Proxy do Harbor)
* Certificado Wildcard GlobalSign

Hostname:

```text
harbor.infraero.gov.br
```

---

## 1. Identificar os certificados configurados

Verificar o arquivo de configuração do Harbor:

```bash
grep -A5 -B2 "https:" harbor.yml
```

Exemplo:

```yaml
https:
  port: 443
  certificate: /etc/pki/tls/certs/infraero.gov.br.pem
  private_key: /etc/pki/tls/private/infraero.gov.br.key
```

---

## 2. Criar backup dos certificados atuais

```bash
mkdir -p /root/bkp-cert-harbor-$(date +%F)

cp -p /etc/pki/tls/certs/infraero.gov.br.pem \
/root/bkp-cert-harbor-$(date +%F)/

cp -p /etc/pki/tls/private/infraero.gov.br.key \
/root/bkp-cert-harbor-$(date +%F)/
```

Verificar:

```bash
ls -lah /root/bkp-cert-harbor-$(date +%F)/
```

---

## 3. Arquivos recebidos

```text
0_Infraero_OrganizationSSL_2026.cer
cadeia_completa_globalsign.pem
infraero_certificado_2026.key
```

Copiar para um diretório temporário:

```bash
mkdir -p /tmp/cert2026
```

---

## 4. Validar o certificado do site

```bash
openssl x509 -in 0_Infraero_OrganizationSSL_2026.cer \
-noout -subject -issuer -dates
```

Resultado esperado:

```text
subject=C=BR, ST=DISTRITO FEDERAL, L=BRASILIA, O=INFRAERO, CN=*.infraero.gov.br
```

---

## 5. Validar certificado e chave privada

Certificado:

```bash
openssl x509 -noout -modulus \
-in 0_Infraero_OrganizationSSL_2026.cer | md5sum
```

Chave:

```bash
openssl rsa -noout -modulus \
-in infraero_certificado_2026.key | md5sum
```

Os hashes devem ser idênticos.

Exemplo:

```text
851dbad6e7a519412df992c58f7c01e5
851dbad6e7a519412df992c58f7c01e5
```

---

## 6. Criar o arquivo PEM completo

Montar o certificado do site + cadeia da GlobalSign:

```bash
cat 0_Infraero_OrganizationSSL_2026.cer > infraero.gov.br.pem

echo "" >> infraero.gov.br.pem

cat cadeia_completa_globalsign.pem >> infraero.gov.br.pem
```

Validar:

```bash
openssl x509 -in infraero.gov.br.pem \
-noout -subject -issuer -dates
```

Resultado esperado:

```text
CN=*.infraero.gov.br
```

---

## 7. Atualizar os certificados do sistema

```bash
cp infraero.gov.br.pem \
/etc/pki/tls/certs/infraero.gov.br.pem

cp infraero_certificado_2026.key \
/etc/pki/tls/private/infraero.gov.br.key
```

---

## 8. Atualizar certificados utilizados pelo Harbor

```bash
cp infraero.gov.br.pem \
/data/secret/cert/server.crt

cp infraero_certificado_2026.key \
/data/secret/cert/server.key
```

Verificar:

```bash
ls -lah /data/secret/cert/
```

---

## 9. Executar o prepare do Harbor

```bash
cd /root/harbor

./prepare
```

---

## 10. Identificar os serviços do Docker Compose

```bash
docker compose config --services
```

Resultado:

```text
log
postgresql
redis
registry
core
portal
proxy
jobservice
registryctl
```

Observação:

O serviço responsável pelo Nginx é chamado **proxy**.

---

## 11. Recriar o serviço proxy

```bash
docker compose up -d --force-recreate proxy
```

Verificar:

```bash
docker ps
```

---

## 12. Validar a configuração do Nginx

```bash
docker exec nginx nginx -t
```

Resultado esperado:

```text
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

---

## 13. Validar o certificado publicado

```bash
openssl s_client \
-connect harbor.infraero.gov.br:443 \
-servername harbor.infraero.gov.br \
</dev/null 2>/dev/null \
| openssl x509 -noout -subject -issuer -dates
```

Resultado esperado:

```text
subject=C=BR, ST=DISTRITO FEDERAL, L=BRASILIA, O=INFRAERO, CN=*.infraero.gov.br
issuer=C=BE, O=GlobalSign nv-sa, CN=GlobalSign RSA OV SSL CA 2018
notAfter=Nov 13 17:54:04 2026 GMT
```

---

## 14. Teste HTTPS

```bash
curl -Iv https://harbor.infraero.gov.br
```

Pontos importantes da saída:

### Certificado apresentado

```text
subject: CN=*.infraero.gov.br
```

### Emissor

```text
issuer: GlobalSign RSA OV SSL CA 2018
```

### Validação da cadeia

```text
SSL certificate verify ok.
```

### Compatibilidade do host

```text
host "harbor.infraero.gov.br" matched cert's "*.infraero.gov.br"
```

### Resposta HTTP

```text
HTTP/1.1 200 OK
```

---

## Validações finais

Checklist:

* [x] Backup realizado
* [x] Certificado validado
* [x] Chave privada validada
* [x] Hashes conferidos
* [x] PEM criado corretamente
* [x] Certificados copiados para o Harbor
* [x] Prepare executado
* [x] Serviço proxy recriado
* [x] Nginx validado
* [x] HTTPS validado
* [x] Certificado novo em produção

---

## Lições Aprendidas

* Sempre validar certificado e chave através do modulus.
* Nem sempre o nome do container é o nome do serviço do Docker Compose.
* O comando `curl -Iv` é excelente para validação HTTPS.
* O comando `openssl s_client` permite validar exatamente qual certificado está sendo publicado.
* Após troca de certificado, o navegador pode exibir informações antigas devido ao cache.
* Sempre validar por linha de comando e pelo navegador.

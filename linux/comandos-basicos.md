---
layout: default
title: Comandos Básicos do Linux
---

# Comandos Básicos do Linux

Este guia apresenta alguns dos comandos mais utilizados no dia a dia de administração e suporte em sistemas Linux.

---

# Navegação entre diretórios

Verificar o diretório atual:

```bash
pwd
```

Listar arquivos e diretórios:

```bash
ls
```

Listar com detalhes:

```bash
ls -l
```

Listar incluindo arquivos ocultos:

```bash
ls -la
```

Entrar em um diretório:

```bash
cd /etc
```

Voltar um nível:

```bash
cd ..
```

Ir para o diretório pessoal:

```bash
cd
```

---

# Manipulação de arquivos

Criar um arquivo vazio:

```bash
touch arquivo.txt
```

Criar um diretório:

```bash
mkdir documentos
```

Criar diretórios recursivamente:

```bash
mkdir -p projetos/linux/scripts
```

Copiar arquivos:

```bash
cp arquivo.txt /tmp/
```

Copiar diretórios:

```bash
cp -r diretorio/ backup/
```

Mover ou renomear arquivos:

```bash
mv arquivo.txt novo_nome.txt
```

Remover arquivos:

```bash
rm arquivo.txt
```

Remover diretórios:

```bash
rm -rf diretorio/
```

---

# Visualização de arquivos

Exibir conteúdo:

```bash
cat arquivo.txt
```

Visualizar página por página:

```bash
less arquivo.txt
```

Exibir início do arquivo:

```bash
head arquivo.txt
```

Exibir final do arquivo:

```bash
tail arquivo.txt
```

Acompanhar logs em tempo real:

```bash
tail -f /var/log/messages
```

---

# Pesquisa

Pesquisar arquivos:

```bash
find / -name arquivo.txt
```

Pesquisar texto dentro de arquivos:

```bash
grep "erro" arquivo.log
```

Pesquisar ignorando maiúsculas:

```bash
grep -i "erro" arquivo.log
```

---

# Gerenciamento de usuários

Ver usuário atual:

```bash
whoami
```

Exibir informações do usuário:

```bash
id
```

Criar usuário:

```bash
useradd joao
```

Definir senha:

```bash
passwd joao
```

Remover usuário:

```bash
userdel joao
```

---

# Permissões

Visualizar permissões:

```bash
ls -l
```

Alterar permissões:

```bash
chmod 755 script.sh
```

Alterar proprietário:

```bash
chown usuario:grupo arquivo.txt
```

---

# Processos

Listar processos:

```bash
ps aux
```

Monitorar processos:

```bash
top
```

Encerrar processo:

```bash
kill PID
```

Encerrar processo à força:

```bash
kill -9 PID
```

---

# Serviços (systemd)

Verificar status:

```bash
systemctl status sshd
```

Iniciar serviço:

```bash
systemctl start sshd
```

Parar serviço:

```bash
systemctl stop sshd
```

Reiniciar serviço:

```bash
systemctl restart sshd
```

Habilitar no boot:

```bash
systemctl enable sshd
```

---

# Rede

Verificar interfaces:

```bash
ip a
```

Verificar rotas:

```bash
ip route
```

Testar conectividade:

```bash
ping 8.8.8.8
```

Consultar DNS:

```bash
nslookup google.com
```

Verificar portas abertas:

```bash
ss -tulpn
```

---

# Armazenamento

Verificar uso de disco:

```bash
df -h
```

Verificar utilização de diretórios:

```bash
du -sh *
```

Listar discos:

```bash
lsblk
```

Exibir UUID dos dispositivos:

```bash
blkid
```

---

# Logs

Visualizar logs do sistema:

```bash
journalctl
```

Logs de um serviço:

```bash
journalctl -u sshd
```

Logs em tempo real:

```bash
journalctl -fu sshd
```

---

# Informações do sistema

Ver hostname:

```bash
hostname
```

Ver versão do sistema:

```bash
cat /etc/os-release
```

Ver utilização de memória:

```bash
free -h
```

Ver tempo ligado:

```bash
uptime
```

Ver informações do kernel:

```bash
uname -r
```

---

## Conclusão

Esses comandos fazem parte do dia a dia de administradores Linux e profissionais de infraestrutura. Dominar essas ferramentas é um passo importante para troubleshooting, administração de servidores e preparação para certificações como LPIC-1 e LPIC-2.


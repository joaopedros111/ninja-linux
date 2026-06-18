---
layout: default
title: Active Directory
---

# 🏢 Active Directory - Comandos Úteis para Suporte e Infraestrutura

## Verificar informações de um usuário

```powershell
Get-ADUser t034691811
```

Exibir propriedades adicionais:

```powershell
Get-ADUser t034691811 -Properties *
```

Exibir nome, e-mail e departamento:

```powershell
Get-ADUser t034691811 -Properties mail,department |
Select Name,SamAccountName,Mail,Department
```

---

## Verificar grupos de um usuário

```powershell
Get-ADPrincipalGroupMembership t034691811
```

Somente os nomes:

```powershell
Get-ADPrincipalGroupMembership t034691811 |
Select Name
```

Ordenado:

```powershell
Get-ADPrincipalGroupMembership t034691811 |
Sort Name |
Select Name
```

---

## Verificar membros de um grupo

```powershell
Get-ADGroupMember "ProxySEDEAcessoPadrao"
```

Exibir apenas logins:

```powershell
Get-ADGroupMember "ProxySEDEAcessoPadrao" |
Select SamAccountName
```

Procurar usuário dentro do grupo:

```powershell
Get-ADGroupMember "ProxySEDEAcessoPadrao" |
Where-Object {$_.SamAccountName -eq "t034691811"}
```

---

## Adicionar usuário a um grupo

```powershell
Add-ADGroupMember `
-Identity "ProxySEDEAcessoPadrao" `
-Members "t034691811"
```

---

## Remover usuário de um grupo

```powershell
Remove-ADGroupMember `
-Identity "ProxySEDEAcessoPadrao" `
-Members "t034691811"
```

Sem confirmação:

```powershell
Remove-ADGroupMember `
-Identity "ProxySEDEAcessoPadrao" `
-Members "t034691811" `
-Confirm:$false
```

---

## Verificar se usuário está bloqueado

```powershell
Get-ADUser t034691811 -Properties LockedOut |
Select Name,LockedOut
```

---

## Desbloquear usuário

```powershell
Unlock-ADAccount t034691811
```

---

## Verificar data da última troca de senha

```powershell
Get-ADUser t034691811 -Properties PasswordLastSet |
Select Name,PasswordLastSet
```

---

## Forçar troca de senha no próximo logon

```powershell
Set-ADUser `
-Identity "t034691811" `
-ChangePasswordAtLogon $true
```

---

## Redefinir senha

```powershell
Set-ADAccountPassword `
-Identity "t034691811" `
-Reset `
-NewPassword (ConvertTo-SecureString "NovaSenha123" -AsPlainText -Force)
```

---

## Verificar computadores no domínio

```powershell
Get-ADComputer -Filter *
```

Listar somente nomes:

```powershell
Get-ADComputer -Filter * |
Select Name
```

---

## Procurar computador específico

```powershell
Get-ADComputer -Identity SE10499779
```

---

## Verificar informações do computador

```powershell
Get-ADComputer SE10499779 -Properties *
```

---

## Pesquisar usuário por nome

```powershell
Get-ADUser -Filter 'Name -like "*Joao*"'
```

---

## Pesquisar computador por nome

```powershell
Get-ADComputer -Filter 'Name -like "*SE104*"'
```

---

## Descobrir em qual OU está o usuário

```powershell
Get-ADUser t034691811 |
Select DistinguishedName
```

Exemplo:

```text
CN=Joao Pedro dos Santos,
OU=TODOS,
OU=Usuarios,
OU=SEDE,
DC=infraero,
DC=gov,
DC=br
```

---

## Verificar usuário logado na máquina local

```cmd
whoami
```

---

## Verificar grupos recebidos no logon

```cmd
whoami /groups
```

Filtrar por Proxy:

```cmd
whoami /groups | findstr /i Proxy
```

---

## Atualizar tickets Kerberos

Visualizar:

```cmd
klist
```

Limpar:

```cmd
klist purge
```

---

## Verificar informações do domínio

```cmd
systeminfo | findstr /B /C:"Domínio"
```

---

## Verificar controladores de domínio

```cmd
nltest /dclist:infraero.gov.br
```

---

## Verificar conectividade com o AD

```cmd
nltest /dsgetdc:infraero.gov.br
```

---

## Verificar replicação do AD (Admins)

```cmd
repadmin /replsummary
```

---

## Comandos RSAT

Verificar se o módulo AD está carregado:

```powershell
Get-Module ActiveDirectory
```

Importar:

```powershell
Import-Module ActiveDirectory
```

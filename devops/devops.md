# Azure DevOps, Jenkins, Harbor e Kubernetes

## Introdução

Em ambientes modernos de desenvolvimento e infraestrutura, é comum encontrar ferramentas que trabalham juntas para automatizar a entrega de aplicações.

Um fluxo típico é:

```text
Desenvolvedor
      ↓
Azure DevOps
      ↓
Jenkins
      ↓
Harbor
      ↓
Kubernetes
      ↓
Aplicação em produção
```

Cada ferramenta possui uma função específica dentro desse processo.

---

# Azure DevOps

## O que é?

Azure DevOps é uma plataforma da Microsoft utilizada para gerenciamento do ciclo de desenvolvimento de software.

## Principais funções

* Hospedar repositórios Git
* Controle de versões
* Gerenciamento de tarefas e projetos
* Controle de branches
* Pull Requests
* Integração com pipelines

## Exemplo

Um desenvolvedor realiza alterações no código e envia para o repositório:

```bash
git add .
git commit -m "Correção de erro"
git push origin main
```

O código fica armazenado no Azure DevOps.

## Resumo

```text
Azure DevOps = Guarda o código-fonte
```

---

# Jenkins

## O que é?

Jenkins é uma ferramenta de automação utilizada para executar processos de Integração Contínua (CI) e Entrega Contínua (CD).

## Principais funções

* Baixar código do Git
* Compilar aplicações
* Executar testes
* Criar imagens Docker
* Publicar imagens
* Realizar deploy

## Exemplo

Quando um novo código é enviado para o Azure DevOps, o Jenkins pode:

1. Baixar o código
2. Compilar a aplicação
3. Criar uma imagem Docker
4. Fazer deploy automaticamente

## Resumo

```text
Jenkins = Automatiza o processo de build e deploy
```

---

# Harbor

## O que é?

Harbor é um repositório privado de imagens Docker e Podman.

Seu papel é armazenar as imagens criadas pelo Jenkins.

## Exemplo

Após a criação da imagem:

```bash
docker build -t conecta-siso:73764 .
```

A imagem é enviada para o Harbor:

```bash
docker push harbor.infraero.gov.br/library/conecta-siso:73764
```

## O que o Harbor armazena?

```text
conecta-siso:73764
conecta-siso:73765
conecta-siso:73766
```

Cada versão fica armazenada para uso futuro.

## Resumo

```text
Harbor = Guarda as imagens dos containers
```

---

# Kubernetes

## O que é?

Kubernetes é uma plataforma de orquestração de containers.

Sua função é executar e gerenciar aplicações containerizadas.

## Principais funções

* Executar containers
* Escalar aplicações
* Reiniciar containers com falha
* Atualizar versões sem indisponibilidade
* Balancear carga

## Exemplo

Quando o Jenkins executa:

```bash
kubectl set image deployment/conecta-siso \
conecta-siso=harbor.infraero.gov.br/library/conecta-siso:73764 \
-n conecta
```

O Kubernetes:

1. Baixa a nova imagem do Harbor
2. Cria novos containers
3. Remove os antigos
4. Mantém a aplicação disponível

## Resumo

```text
Kubernetes = Executa e gerencia os containers
```

---

# Fluxo Completo

```text
1. Desenvolvedor altera o código
           ↓
2. Código é enviado para o Azure DevOps
           ↓
3. Jenkins baixa o código
           ↓
4. Jenkins compila a aplicação
           ↓
5. Jenkins cria uma imagem Docker
           ↓
6. Jenkins envia a imagem para o Harbor
           ↓
7. Kubernetes baixa a imagem do Harbor
           ↓
8. Kubernetes atualiza a aplicação
```

---

# Resumo Geral

| Ferramenta   | Função                          |
| ------------ | ------------------------------- |
| Azure DevOps | Armazenar o código-fonte        |
| Jenkins      | Automatizar build e deploy      |
| Harbor       | Armazenar imagens Docker/Podman |
| Kubernetes   | Executar e gerenciar containers |

## Frase para memorizar

```text
Azure DevOps guarda o código.
Jenkins automatiza.
Harbor guarda as imagens.
Kubernetes executa as aplicações.
```
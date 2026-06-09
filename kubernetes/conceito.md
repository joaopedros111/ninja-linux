---
layout: default
title: O que é Kubernetes
---

# ☸ O que é Kubernetes?

## Introdução

O Kubernetes (K8s) é uma plataforma de orquestração de containers de código aberto criada originalmente pelo Google e atualmente mantida pela Cloud Native Computing Foundation.

Seu objetivo é automatizar a implantação, escalabilidade, monitoramento e gerenciamento de aplicações executadas em containers.

Em vez de administrar containers individualmente, o Kubernetes gerencia todo o ambiente de forma centralizada e automatizada.

---

## Por que utilizar Kubernetes?

Em ambientes modernos, aplicações geralmente são executadas em containers.

Administrar poucos containers manualmente é simples, porém, quando o ambiente cresce, surgem desafios como:

* Escalabilidade
* Alta disponibilidade
* Balanceamento de carga
* Atualizações sem indisponibilidade
* Recuperação automática de falhas
* Gerenciamento centralizado

O Kubernetes resolve esses problemas de forma automática.

---

## Como funciona?

O Kubernetes organiza os recursos em uma estrutura hierárquica:

```text
Cluster
 ├── Node
 │    ├── Pod
 │    │    └── Container
 │    └── Pod
 │
 └── Node
      └── Pod
```

### Cluster

É o conjunto de servidores que executam o Kubernetes.

Um cluster pode possuir um ou vários servidores (Nodes).

---

### Node

Um Node é uma máquina física ou virtual participante do cluster.

Cada Node executa Pods e disponibiliza recursos de CPU, memória e armazenamento.

---

### Pod

É a menor unidade de execução do Kubernetes.

Um Pod normalmente contém um único container, embora seja possível executar múltiplos containers dentro do mesmo Pod.

Exemplo:

```text
Pod
 └── Container Nginx
```

---

### Container

O container é onde a aplicação realmente é executada.

Exemplos:

* Nginx
* Apache
* PostgreSQL
* Redis
* Aplicações Java
* Aplicações Python

---

## Principais Componentes

### Deployment

Responsável por gerenciar Pods.

Permite:

* Criar Pods
* Escalar aplicações
* Atualizar versões
* Recuperar falhas

Exemplo:

```text
Deployment
 ├── Pod 1
 ├── Pod 2
 └── Pod 3
```

Caso um Pod falhe, o Deployment cria outro automaticamente.

---

### Service

Fornece um endereço estável para acesso aos Pods.

Como os Pods podem ser recriados e receber novos IPs, o Service garante um ponto de acesso permanente.

```text
Service
   ↓
Pod 1
Pod 2
Pod 3
```

---

### Ingress

Permite publicar aplicações para acesso externo.

Exemplo:

```text
https://wiki.empresa.com.br
```

Fluxo:

```text
Usuário
   ↓
Ingress
   ↓
Service
   ↓
Pods
```

---

## Benefícios

### Alta Disponibilidade

Se um Pod falhar, outro é criado automaticamente.

### Escalabilidade

Permite aumentar ou reduzir a quantidade de Pods conforme a demanda.

### Atualizações Sem Interrupção

Novas versões podem ser implantadas sem indisponibilidade do serviço.

### Automação

Grande parte das tarefas operacionais é realizada automaticamente.

### Portabilidade

O mesmo ambiente pode ser executado em:

* Servidores físicos
* Máquinas virtuais
* Nuvens públicas
* Ambientes híbridos

---

## Kubernetes e Docker

O Docker é utilizado para criar e executar containers.

O Kubernetes é utilizado para gerenciar esses containers em larga escala.

```text
Docker
 └── Cria Containers

Kubernetes
 └── Gerencia Containers
```

Os dois são tecnologias complementares.

---

## Onde o Rancher se encaixa?

O Rancher é uma plataforma de gerenciamento para Kubernetes.

Ele fornece uma interface gráfica que facilita a administração de clusters.

Com o Rancher é possível:

* Visualizar Pods
* Gerenciar Nodes
* Acompanhar Deployments
* Consultar Logs
* Monitorar aplicações

Sem Rancher:

```bash
kubectl get pods
kubectl get nodes
kubectl logs
```

Com Rancher:

```text
Interface Web
 ├── Clusters
 ├── Nodes
 ├── Pods
 ├── Logs
 └── Workloads
```

---

## Resumo

O Kubernetes é uma plataforma de orquestração de containers que automatiza a implantação, escalabilidade e gerenciamento de aplicações.

Conceitos fundamentais:

* Cluster
* Node
* Pod
* Container
* Deployment
* Service
* Ingress

Dominar esses conceitos é o primeiro passo para trabalhar com Kubernetes e Rancher em ambientes corporativos.


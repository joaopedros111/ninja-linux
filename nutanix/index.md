---
layout: default
title: Nutanix 
---

# 🥜 Nutanix

## Introdução

O Nutanix é uma plataforma de infraestrutura hiperconvergente (HCI - Hyper-Converged Infrastructure) que integra computação, armazenamento, virtualização e gerenciamento em uma única solução.

Seu objetivo é simplificar a administração de ambientes virtualizados, eliminando a necessidade de infraestruturas tradicionais compostas por servidores, storages SAN e softwares de gerenciamento separados.

Atualmente é uma das principais alternativas ao VMware em ambientes corporativos.

---

## Conceitos Fundamentais

### Infraestrutura Tradicional

Em um ambiente tradicional, normalmente existem:

* Servidores físicos
* Storage SAN
* Switches Fibre Channel
* Hipervisor
* Ferramentas de gerenciamento

Exemplo:

Servidor → SAN → Hipervisor → Máquinas Virtuais

Esse modelo costuma demandar maior complexidade de administração e manutenção.

---

### Infraestrutura Hiperconvergente

No modelo hiperconvergente, cada servidor contribui com:

* Processamento (CPU)
* Memória RAM
* Armazenamento local (SSD/NVMe)
* Rede

Todos os recursos são agrupados em um único cluster.

Benefícios:

* Escalabilidade simplificada
* Alta disponibilidade
* Menor complexidade operacional
* Redução de custos

---

## Principais Componentes

### AOS (Acropolis Operating System)

É o sistema operacional da plataforma Nutanix.

Responsável por:

* Gerenciamento do armazenamento distribuído
* Replicação de dados
* Balanceamento de carga
* Snapshots
* Recuperação de falhas

---

### AHV (Acropolis Hypervisor)

Hipervisor nativo da Nutanix.

Características:

* Baseado em KVM
* Gratuito para clientes Nutanix
* Gerenciamento integrado ao Prism
* Alta disponibilidade nativa

Principais concorrentes:

* VMware ESXi
* Microsoft Hyper-V

---

### Prism

Interface de gerenciamento da plataforma.

Permite:

* Criar máquinas virtuais
* Monitorar desempenho
* Gerenciar clusters
* Realizar upgrades
* Visualizar alertas
* Administrar armazenamento

O Prism é considerado um dos principais diferenciais da solução.

---

## Estrutura de um Cluster Nutanix

Um cluster é formado por múltiplos nós.

Exemplo:

Cluster Nutanix

* Nó 1
* Nó 2
* Nó 3
* Nó 4

Cada nó possui:

* CPU
* Memória
* SSD/NVMe
* Rede

O armazenamento local de todos os nós é consolidado em um único pool distribuído.

---

## Alta Disponibilidade

O Nutanix distribui os dados entre os nós do cluster.

Caso um servidor apresente falha:

* As máquinas virtuais continuam disponíveis
* Os dados permanecem acessíveis
* O ambiente mantém sua operação

Esse mecanismo reduz significativamente o impacto de falhas de hardware.

---

## Escalabilidade

A expansão do ambiente ocorre através da adição de novos nós ao cluster.

Exemplo:

* Cluster com 3 nós
* Adição de 1 novo nó
* Cluster passa a possuir 4 nós

Os recursos são automaticamente incorporados ao ambiente.

---

## Funcionalidades Comuns

### Snapshots

Permitem criar pontos de recuperação das máquinas virtuais.

Utilizados para:

* Backup
* Atualizações
* Testes
* Recuperação rápida

---

### Replicação

Permite replicar máquinas virtuais para outro cluster Nutanix.

Utilizada para:

* Disaster Recovery (DR)
* Continuidade de negócio
* Ambientes de contingência

---

### Monitoramento

Através do Prism é possível acompanhar:

* Uso de CPU
* Uso de memória
* Consumo de armazenamento
* Desempenho das VMs
* Eventos e alertas

---

## Vantagens

* Administração simplificada
* Alta disponibilidade nativa
* Escalabilidade horizontal
* Menor dependência de storages SAN
* Interface intuitiva
* Integração entre computação e armazenamento
* Menor complexidade operacional

---

## Desvantagens

* Investimento inicial elevado
* Dependência da plataforma Nutanix
* Menor flexibilidade em comparação com ambientes totalmente customizados

---

## Casos de Uso

O Nutanix é amplamente utilizado para:

* Virtualização de servidores
* Infraestrutura corporativa
* Ambientes de homologação
* Bancos de dados
* VDI (Virtual Desktop Infrastructure)
* Nuvem privada
* Disaster Recovery

---

## Comandos e Acesso

Em ambientes Nutanix é comum acessar:

### AHV Host

```bash
ssh root@ip_do_host
```

### CVM (Controller VM)

```bash
ssh nutanix@ip_da_cvm
```

### Verificar status do cluster

```bash
cluster status
```

### Verificar informações do cluster

```bash
ncli cluster info
```

### Listar máquinas virtuais

```bash
acli vm.list
```

---

## Resumo

O Nutanix é uma plataforma de infraestrutura hiperconvergente que combina computação, armazenamento, virtualização e gerenciamento em uma única solução.

Seu principal objetivo é simplificar a administração de ambientes virtualizados, oferecendo alta disponibilidade, escalabilidade e gerenciamento centralizado através do Prism.


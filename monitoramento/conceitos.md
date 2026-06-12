---
layout: default
title: Conceitos de Monitoramento
---

# 📊 Conceitos de Monitoramento

## O que é Monitoramento?

Monitoramento é o processo de coletar, analisar e acompanhar informações sobre servidores, aplicações, serviços e dispositivos de rede para garantir disponibilidade, desempenho e estabilidade do ambiente.

O monitoramento permite identificar falhas, antecipar problemas e gerar alertas para a equipe responsável.

---

## Objetivos do Monitoramento

* Detectar falhas rapidamente
* Acompanhar a disponibilidade dos serviços
* Medir desempenho dos sistemas
* Gerar alertas automáticos
* Auxiliar na análise de incidentes
* Apoiar decisões de capacidade e crescimento

---

## Métricas

Métricas são informações coletadas periodicamente para medir o estado de um recurso.

Exemplos:

* Uso de CPU
* Consumo de memória
* Espaço em disco
* Tráfego de rede
* Tempo de resposta
* Número de conexões

---

## Eventos

Eventos representam ocorrências registradas durante o funcionamento do ambiente.

Exemplos:

* Reinicialização de servidor
* Queda de serviço
* Falha de autenticação
* Alteração de configuração

---

## Alertas

Alertas são notificações geradas quando uma condição pré-definida é atendida.

Exemplos:

* CPU acima de 90%
* Disco com mais de 85% de utilização
* Serviço indisponível
* Falha de comunicação com host

---

## Disponibilidade

Disponibilidade representa o tempo em que um serviço permanece operacional.

Exemplo:

| Disponibilidade | Tempo de indisponibilidade anual |
| --------------- | -------------------------------- |
| 99%             | 3,65 dias                        |
| 99,9%           | 8,76 horas                       |
| 99,99%          | 52 minutos                       |
| 99,999%         | 5 minutos                        |

---

## SLA

SLA (Service Level Agreement) é o acordo de nível de serviço estabelecido entre fornecedor e cliente.

Exemplo:

```text
Disponibilidade mínima: 99,9%
Tempo máximo de atendimento: 30 minutos
Tempo máximo de solução: 4 horas
```

---

## Monitoramento Ativo

O sistema de monitoramento realiza testes periódicos para verificar se um serviço está funcionando.

Exemplos:

* Ping
* HTTP
* HTTPS
* SSH
* DNS

---

## Monitoramento Passivo

Os dispositivos ou aplicações enviam informações para a ferramenta de monitoramento.

Exemplos:

* Logs
* SNMP Traps
* Agentes de monitoramento
* Syslog

---

## Observabilidade

Observabilidade é a capacidade de entender o comportamento de um sistema através dos dados gerados por ele.

Baseia-se em três pilares:

### Métricas

Informações numéricas coletadas ao longo do tempo.

### Logs

Registros detalhados de eventos.

### Traces

Rastreamento completo de uma transação entre sistemas.

---

## Ferramentas de Monitoramento

### Zabbix

Ferramenta de monitoramento de infraestrutura, servidores e aplicações.

### Grafana

Ferramenta de visualização de dados e criação de dashboards.

### Prometheus

Sistema de coleta e armazenamento de métricas.

---

> 💡 Um monitoramento eficiente deve coletar métricas, gerar alertas e fornecer informações que permitam identificar rapidamente a causa de um problema.

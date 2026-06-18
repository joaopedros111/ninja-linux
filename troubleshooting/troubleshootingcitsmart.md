---
layout: default
title: Troubleshooting CITSmart
---

# Troubleshooting – Indisponibilidade do CITSmart

---

## Solução de Contorno

Reiniciar os serviços do CITSmart.

Observação: a reinicialização restabelece o funcionamento da aplicação, porém não corrige a causa raiz do problema.

---

## Sintoma

Usuários relatam indisponibilidade ou lentidão no acesso ao CITSmart.

---

## Verificar status dos containers

```bash
docker ps
```

Verificar se todos os containers do ambiente estão em execução.

---

## Verificar consumo de recursos

```bash
docker stats --no-stream runITSM
```

Validar consumo de CPU e memória do container principal do CITSmart.

---

## Verificar erros de memória

```bash
docker logs runITSM 2>&1 | grep -i "OutOfMemoryError"
```

Caso exista retorno semelhante ao abaixo:

```text
java.lang.OutOfMemoryError: Java heap space
```

A aplicação apresentou esgotamento da memória Java (Heap).

---

## Identificar processo Java

```bash
docker exec -it runITSM ps -ef | grep java
```

Anotar o PID do processo Java.

Exemplo:

```text
itsm 1101 java ...
```

---

## Verificar utilização da Heap

```bash
docker exec -it runITSM jcmd 1101 GC.heap_info
```

Exemplo:

```text
garbage-first heap total 25067520K
used 1387139K
```

---

## Verificar parâmetros da JVM

```bash
docker exec -it runITSM jcmd 1101 VM.flags
```

Verificar principalmente os parâmetros:

```text
-XX:InitialHeapSize
-XX:MaxHeapSize
```

---

## Coletar logs da aplicação

Acessar:

```text
Sistema → Informações do Sistema → Download Log do JBoss
```

Salvar o arquivo para análise posterior.

---

## Verificar trilha de auditoria

Acessar:

```text
Sistema → Trilha de Auditoria → Auditoria de Dados
```

Filtrar pelo horário da indisponibilidade.

Exemplo:

```text
Data Inicial: 12/06/2026 11:40
Data Final:   12/06/2026 11:50
```

---

## Evidências encontradas no incidente de 12/06/2026

Foi identificado:

```text
java.lang.OutOfMemoryError: Java heap space
```

A stack trace apontou para:

```text
com.citsmart.audit.service.impl.AuditServiceImpl
org.javers.core.JaversCore.compare
```

Após o erro foram observadas falhas de comunicação internas:

```text
ActiveMQConnectionTimedOutException
AMQ219014
Channel is closed
```

## Conclusão Preliminar

Os indícios apontam para falha relacionada ao módulo de auditoria da aplicação, resultando em esgotamento da memória Java (OutOfMemoryError) e consequente degradação dos serviços internos do CITSmart.

---
layout: default
title: Troubleshooting
---

# Troubleshooting - Problema de Caracteres Especiais (UTF-8) no WildFly

## 📌 Sintoma
Caracteres especiais (acentos como ç, ã, é) apareciam corrompidos na interface web e logs da aplicação Java (WildFly), exemplo:

- ação → aÃ§Ã£o
- informação → informaÃ§Ã£o

---

## 🔍 Diagnóstico

### 1. Locale do sistema inconsistente
Inicialmente o sistema estava configurado como:

```
LANG=en_US.UTF-8
LC_ALL= (vazio)
LC_* = POSIX
```

➡️ Isso gerava inconsistência de encoding no ambiente de execução Java.

---

### 2. JVM já estava correta
A JVM já possuía:

```
-Dfile.encoding=UTF-8
```

➡️ Portanto o problema NÃO era na JVM.

---

### 3. Sistema operacional
Sistema baseado em EL9 (RHEL/CentOS-like), com UTF-8 disponível, porém sem locale consistente aplicado na sessão.

---

## 🛠️ Correção aplicada

Foi aplicado ajuste de ambiente:

```bash
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
```

---

## ✅ Resultado

Após a correção:

- Interface web passou a exibir caracteres corretamente
- Logs do WildFly ficaram consistentes
- Encoding UTF-8 padronizado no ambiente de execução
- Problema de corrupção de caracteres eliminado

---

## 🧠 Causa raiz

Inconsistência de locale no sistema operacional afetando a herança de encoding pela JVM.

---

## 📌 Conclusão

O problema não estava na aplicação nem no container, mas sim no ambiente Linux onde o processo Java estava sendo executado.

A padronização do locale para UTF-8 resolveu completamente o incidente.

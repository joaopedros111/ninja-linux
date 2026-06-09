---

layout: default
title: Kubernetes
---

# ☸ Kubernetes

Documentação e anotações relacionadas ao Kubernetes, Rancher e orquestração de containers.

Aqui serão registrados conceitos, comandos, procedimentos, troubleshooting e atividades realizadas no ambiente corporativo.

---

## 📚 Conceitos

➡️ [O que é Kubernetes](conceito.md)

➡️ [Arquitetura do Cluster](conceitos/arquitetura.md)

➡️ [Pods, Nodes e Namespaces](conceitos/pods-nodes-namespaces.md)

➡️ [Deployments e Services](conceitos/deployments-services.md)

➡️ [Ingress](conceitos/ingress.md)

---

## ☸ Kubectl

➡️ [Comandos Básicos](kubectl/comandos-basicos.md)

➡️ [Gerenciamento de Pods](kubectl/pods.md)

➡️ [Logs e Troubleshooting](kubectl/logs.md)

➡️ [Describe e Eventos](kubectl/describe.md)

---

## 🐄 Rancher

➡️ [Acesso ao Ambiente](rancher/acesso.md)

➡️ [Navegação no Rancher](rancher/navegacao.md)

➡️ [Workloads](rancher/workloads.md)

➡️ [Visualização de Logs](rancher/logs.md)

---

## 🚀 Deployments

➡️ [Criando um Deployment](deployments/criando-deployment.md)

➡️ [Escalando Aplicações](deployments/scale.md)

➡️ [Rollback](deployments/rollback.md)

➡️ [Atualizações](deployments/update.md)

---

## 🌐 Rede

➡️ [Services](network/services.md)

➡️ [Ingress](network/ingress.md)

➡️ [DNS Interno](network/dns.md)

➡️ [Balanceamento de Carga](network/loadbalancer.md)

---

## 🚨 Troubleshooting

➡️ [Pod em CrashLoopBackOff](troubleshooting/crashloopbackoff.md)

➡️ [Pod Não Inicia](troubleshooting/pod-nao-inicia.md)

➡️ [Erro de Imagem](troubleshooting/imagepullbackoff.md)

➡️ [Problemas de Rede](troubleshooting/rede.md)

➡️ [Coleta de Logs](troubleshooting/logs.md)

---

## 📖 Referência Rápida

### Listar Pods

```bash
kubectl get pods -A
```

### Listar Nodes

```bash
kubectl get nodes
```

### Listar Namespaces

```bash
kubectl get ns
```

### Ver Logs

```bash
kubectl logs <pod>
```

### Descrever um Pod

```bash
kubectl describe pod <pod>
```

---

🐧 Base de conhecimento em constante evolução, acompanhando os estudos e atividades práticas com Kubernetes e Rancher.


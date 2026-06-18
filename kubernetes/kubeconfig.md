---

layout: default
title: KUBECONFIG
-----------------

# ☸️ KUBECONFIG - Guia Rápido

## Introdução

O KUBECONFIG é um arquivo utilizado pelo Kubernetes para armazenar informações de acesso aos clusters.

Ele contém dados como:

* Endereço da API do cluster
* Certificados
* Contextos
* Usuários
* Tokens de autenticação

Sem um KUBECONFIG válido, o `kubectl` não consegue se conectar ao cluster.

---

## Estrutura de um KUBECONFIG

Exemplo simplificado:

```yaml
apiVersion: v1
kind: Config

clusters:
- name: infraero-hml
  cluster:
    server: https://cluster.exemplo.com

contexts:
- name: infraero-hml
  context:
    cluster: infraero-hml
    user: infraero-hml

current-context: infraero-hml
```

---

## Definindo o KUBECONFIG

### NKE

#### Desenvolvimento

```bash
export KUBECONFIG=/home/operador/infraero-det.yaml
```

#### Homologação

```bash
export KUBECONFIG=/home/operador/infraero-hml.yaml
```

#### Produção

```bash
export KUBECONFIG=/home/operador/infraero-prd.yaml
```

#### Infraestrutura

```bash
export KUBECONFIG=/home/operador/infraero-infra.yaml
```

---

### RKE

#### Desenvolvimento

```bash
export KUBECONFIG=/home/operador/desenvolvimentorke.yaml
```

#### Homologação

```bash
export KUBECONFIG=/home/operador/homologacaorke.yaml
```

#### Produção

```bash
export KUBECONFIG=/home/operador/producaorke.yaml
```

---

## Verificando o contexto atual

```bash
kubectl config current-context
```

Exemplo:

```text
infraero-hml
```

---

## Listando os contextos

```bash
kubectl config get-contexts
```

Exemplo:

```text
CURRENT   NAME
*         infraero-hml
          infraero-prd
          infraero-det
```

---

## Testando acesso ao cluster

Listar namespaces:

```bash
kubectl get ns
```

Listar nodes:

```bash
kubectl get nodes
```

Verificar versão:

```bash
kubectl version
```

---

## Comandos úteis

Listar pods de todos os namespaces:

```bash
kubectl get pods -A
```

Listar serviços:

```bash
kubectl get svc -A
```

Listar ingress:

```bash
kubectl get ingress -A
```

Descrever um pod:

```bash
kubectl describe pod <pod>
```

Visualizar logs:

```bash
kubectl logs <pod>
```

Acessar um container:

```bash
kubectl exec -it <pod> -- bash
```

---

## Troubleshooting

### Verificar KUBECONFIG carregado

```bash
echo $KUBECONFIG
```

---

### Erro: Forbidden

Exemplo:

```text
Error from server (Forbidden)
```

Possíveis causas:

* Token inválido
* Token expirado
* Permissões insuficientes
* Usuário sem acesso ao cluster

---

### Erro: system:unauthenticated

Exemplo:

```text
User "system:unauthenticated" cannot get resource
```

#### Causa

O cluster recebeu uma requisição sem autenticação válida.

#### Caso real

Durante um deploy via Jenkins foi retornado:

```text
User "system:unauthenticated" cannot get resource "clusters"
```

A causa foi uma credencial/token incorreto configurado no Jenkins.

#### Solução

* Gerar novo token no Rancher
* Atualizar a credencial utilizada pelo Jenkins
* Executar novamente o pipeline

---

## Referências

Documentação oficial Kubernetes:

https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/

---

> 💡 Sempre valide o KUBECONFIG carregado antes de iniciar qualquer operação em homologação ou produção.

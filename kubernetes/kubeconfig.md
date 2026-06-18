# KUBECONFIG - Guia Rápido

## O que é o KUBECONFIG?

O KUBECONFIG é um arquivo utilizado pelo Kubernetes para armazenar informações de acesso aos clusters.

Ele contém:

* URL da API do cluster
* Certificados
* Contextos
* Usuários
* Tokens de autenticação

Sem um KUBECONFIG válido, o kubectl não consegue se conectar ao cluster.

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

## Verificar cluster atual

```bash
kubectl config current-context
```

Exemplo:

```text
infraero-hml
```

---

## Listar contextos disponíveis

```bash
kubectl config get-contexts
```

---

## Verificar conectividade

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

## Consultar Pods

```bash
kubectl get pods -A
```

Listar pods de um namespace:

```bash
kubectl get pods -n <namespace>
```

---

## Troubleshooting

### Verificar variável carregada

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

Causa identificada em ambiente corporativo:

* Token incorreto configurado no Jenkins ou Rancher

Solução:

* Gerar novo token
* Atualizar credenciais
* Executar novamente o deploy

---

## Comandos úteis

```bash
kubectl get ns
kubectl get nodes
kubectl get pods -A
kubectl get svc -A
kubectl get ingress -A
kubectl describe pod <pod>
kubectl logs <pod>
kubectl exec -it <pod> -- bash
```

---

## Referências

Documentação oficial:

https://kubernetes.io/docs/concepts/configuration/organize-cluster-access-kubeconfig/

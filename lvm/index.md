---
layout: default
title: LVM
---

# LVM

## Tutoriais

### Expandindo um Volume Lógico no Rocky Linux 8

Verificar discos:

```bash
lsblk
```

Verificar volumes:

```bash
pvs
vgs
lvs
```

Expandir o Logical Volume:

```bash
lvextend -l +100%FREE /dev/mapper/rl-root
```

Expandir o sistema de arquivos XFS:

```bash
xfs_growfs /
```

Verificar o resultado:

```bash
df -h
```

### Referências

- Rocky Linux
- Red Hat Enterprise Linux

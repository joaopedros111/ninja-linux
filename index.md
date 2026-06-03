---

layout: default
title: Ninja Linux
------------------

<p align="center">
  <img src="images/capacete.png" width="260">
</p>

<h1 align="center">Ninja Linux</h1>

<p align="center">
Linux • Infraestrutura • Red Hat • Squid • LVM • Redes
</p>

---

## Sobre o projeto

Este site é meu laboratório de estudos em Linux e infraestrutura.

Aqui vou documentar comandos, testes, erros, soluções e anotações práticas do dia a dia como sysadmin.

<div style="display: flex; gap: 15px; flex-wrap: wrap;">

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <h3>🐧 Linux</h3>
    <p>Comandos, permissões, serviços, logs e troubleshooting.</p>
    <a href="linux/">Acessar →</a>
  </div>

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <h3>🔧 LVM</h3>
    <p>Gerenciamento de volumes, discos e expansão de storage.</p>
    <a href="lvm/">Acessar →</a>
  </div>

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <h3>🦑 Squid</h3>
    <p>Proxy, ACLs, cache e troubleshooting.</p>
    <a href="squid/">Acessar →</a>
  </div>

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <h3>🌐 Redes</h3>
    <p>TCP/IP, DNS, Gateway, VLAN e análise de tráfego.</p>
    <a href="redes/">Acessar →</a>
  </div>

</div>

## Conteúdos

* [Linux básico](linux/)
* [Rocky Linux](rocky-linux/)
* [LVM](lvm/)
* [Squid Proxy](squid/)
* [WatchGuard](watchguard/)
* [Redes](redes/)
* [Scripts Shell](scripts/)

## Últimos estudos

* Instalação e configuração do Squid
* Expansão de disco com LVM
* Comandos úteis no Rocky Linux
* Troubleshooting com `journalctl`
* Laboratório de redes

## Comandos úteis

```bash
journalctl -u squid
df -h
lsblk
ip a
systemctl status squid
```


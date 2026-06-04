---
layout: default
title: Ninja Linux
---

<p align="center">
  <img src="images/capacete01.png" width="260">
</p>

<h1 align="center">Ninja Linux</h1>

<p align="center">
Linux • Infraestrutura • Red Hat • Squid • LVM • Redes
</p>

<hr>

## Sobre o projeto

Este site é meu laboratório de estudos em Linux e infraestrutura.

Aqui vou documentar comandos, testes, erros, soluções e anotações práticas do dia a dia como sysadmin.

<div style="display: flex; gap: 15px; flex-wrap: wrap;">

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <div style="display: flex; align-items: center;">
      <h3 style="margin: 0;">🐧 Linux</h3>
      <a href="linux/" style="margin-left: auto;">Acessar →</a>
    </div>
  </div>

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <div style="display: flex; align-items: center;">
      <h3 style="margin: 0;">
        <img src="images/zabbix-logo.png" width="24" style="vertical-align: middle;">
        Zabbix
      </h3>
      <a href="zabbix/" style="margin-left: auto;">Acessar →</a>
    </div>
  </div>

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <div style="display: flex; align-items: center;">
      <h3 style="margin: 0;">🦑 Squid</h3>
      <a href="squid/" style="margin-left: auto;">Acessar →</a>
    </div>
  </div>

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <div style="display: flex; align-items: center;">
      <h3 style="margin: 0;">🌐 Redes</h3>
      <a href="redes/" style="margin-left: auto;">Acessar →</a>
    </div>
  </div>

  <div style="border-left: 5px solid #cc0000; background: #f8f8f8; padding: 15px; border-radius: 8px; width: 250px;">
    <div style="display: flex; align-items: center;">
      <h3 style="margin: 0;">
        <img src="images/shellscript.png" width="24" style="vertical-align: middle;">
        Script Shell
      </h3>
      <a href="scripts/" style="margin-left: auto;">Acessar →</a>
    </div>
    <p>Shell Script básico.</p>
  </div>

</div>

## Conteúdos

* [Linux básico](linux/)
* [Zabbix](zabbix/)
* [Rocky Linux](rocky-linux/)
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

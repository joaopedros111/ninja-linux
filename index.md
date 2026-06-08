---
layout: default
title: Ninja Linux
---

<style>
body {
    background: #000000;
    color: #e0e0e0;
}

a {
    color: #ff5555;
}

hr {
    border-color: #333;
}

h1, h2, h3 {
    color: #ffffff;
}

.card {
    border-left: 5px solid #cc0000;
    background: #161616;
    color: #e0e0e0;
    padding: 15px;
    border-radius: 8px;
    width: 250px;
    box-shadow: 0 2px 8px rgba(255, 0, 0, 0.15);
    transition: 0.2s;
}

.card:hover {
    transform: translateY(-3px);
    box-shadow: 0 4px 14px rgba(255, 0, 0, 0.25);
}

.card h3 {
    margin: 0;
    color: #ffffff;
}

.card a {
    text-decoration: none;
    font-weight: bold;
    color: #ff5555;
}

pre {
    background: #0d0d0d;
    color: #00ff88;
    border: 1px solid #333;
    border-radius: 8px;
    padding: 12px;
}

code {
    color: #00ff88;
}

.card {
    border-left: 5px solid #cc0000;
    background: #2b2b2b;
    color: #e0e0e0;
    padding: 15px;
    border-radius: 8px;
    width: 250px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.4);
}

.card h3 {
    margin: 0;
    color: #ffffff;
}

.card a {
    text-decoration: none;
    font-weight: bold;
    color: #ff5555;
}

pre {
    background: #111;
    color: #00ff88;
    border: 1px solid #333;
    border-radius: 8px;
    padding: 12px;
}

code {
    color: #00ff88;
}
</style>

<p align="center">
  <img src="images/capacete01.png" width="260">
</p>

<h1 align="center">🐧 Ninja Linux</h1>

<p align="center">
Linux • Infraestrutura • Red Hat • Squid • LVM • Redes
</p>

<hr>

## Sobre o projeto

Este site é meu laboratório de estudos em Linux e infraestrutura.

Aqui documento comandos, testes, erros, soluções e procedimentos utilizados no dia a dia como Analista de Infraestrutura.

<div style="display: flex; gap: 15px; flex-wrap: wrap;">

  <div class="card">
    <div style="display: flex; justify-content: space-between; align-items: center;">
      <h3>🐧 Linux</h3>
      <a href="linux/">Acessar →</a>
    </div>
  </div>

  <div class="card">
    <div style="display: flex; justify-content: space-between; align-items: center;">
      <h3>
        <img src="images/zabbix-logo.png" width="24" style="vertical-align: middle;">
        Zabbix
      </h3>
      <a href="zabbix/">Acessar →</a>
    </div>
  </div>

  <div class="card">
    <div style="display: flex; justify-content: space-between; align-items: center;">
      <h3>🦑 Squid</h3>
      <a href="squid/">Acessar →</a>
    </div>
  </div>

  <div class="card">
    <div style="display: flex; justify-content: space-between; align-items: center;">
      <h3>🌐 Redes</h3>
      <a href="redes/">Acessar →</a>
    </div>
  </div>

  <div class="card">
    <div style="display: flex; justify-content: space-between; align-items: center;">
      <h3>
        <img src="images/shellscript.png" width="24" style="vertical-align: middle;">
        Script Shell
      </h3>
      <a href="scripts/">Acessar →</a>
    </div>
  </div>

</div>

---

## 📚 Conteúdos

- [Linux Básico](linux/)
- [Zabbix](zabbix/)
- [Rocky Linux](rocky-linux/)
- [Squid Proxy](squid/)
- [WatchGuard](watchguard/)
- [Redes](redes/)
- [Scripts Shell](scripts/)

---

## 🚀 Últimos Estudos

- Instalação e configuração do Squid
- Expansão de disco com LVM
- Comandos úteis no Rocky Linux
- Troubleshooting com journalctl
- Laboratórios de Redes
- Docker e Harbor
- Atualização de certificados SSL

---

## 💻 Comandos Úteis

```bash
journalctl -u squid

df -h

lsblk

ip a

systemctl status squid

👨‍💻 Sobre o Autor

Meu nome é João Pedro dos Santos e atuo como Analista de Infraestrutura, com foco em ambientes Linux.

Este site reúne laboratórios, procedimentos e anotações desenvolvidos durante meus estudos e atividades profissionais.

Tecnologias
Linux
Rocky Linux
Docker
Ansible
LVM
Redes
Squid
Zabbix
Harbor
WatchGuard

📞 Contato
🔗 GitHub
💼 LinkedIn
=======

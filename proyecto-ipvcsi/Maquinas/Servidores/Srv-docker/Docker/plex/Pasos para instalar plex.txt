# Instalación de Plex Media Server en `srv-docker` (sin Docker)

> Fuente: https://gist.github.com/jc-torresp/fa303e1888e93cb51a407273d7636dda

## Objetivo

Instalar Plex Media Server directamente sobre Ubuntu Server 22.04 para ofrecer un servicio de streaming multimedia interno desde la sede de Castellón.

---

## Pasos de instalación

### 1. Instalar transporte seguro para APT
```bash
sudo apt install apt-transport-https


### 2 -Añadir la clave GPG del repositorio de paquetes de Plex: 

curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add - 

### 3 - Añadir el repositorio de paquetes de Plex a la lista de fuentes de APT: 

echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list 

### 4 - Actualizar la lista de paquetes: 

sudo apt update 

### 5 - Instalar Plex Media Server: 

sudo apt install plexmediaserver 

### 6 - Modificar usuario de Plex Media Server: 

sudo nano /usr/lib/plexmediaserver/lib/plexmediaserver.default 

### 7 - Reiniciar Plex Media Server: 

sudo systemctl restart plexmediaserver 

### 8 - Conocer IP de Plex Media Server: 

hostname -I 

### 9 - Fijar IP de Plex Media Server: 

sudo nano /boot/cmdline.txt 

*Añadir: ip=[IP obtenida en el paso anterior] 

### 10 - Reiniciar Raspberry Pi: 

sudo reboot 

---

## Acceso a la interfaz web

### Accede desde un navegador web:

    http://10.20.10.12:32400/web

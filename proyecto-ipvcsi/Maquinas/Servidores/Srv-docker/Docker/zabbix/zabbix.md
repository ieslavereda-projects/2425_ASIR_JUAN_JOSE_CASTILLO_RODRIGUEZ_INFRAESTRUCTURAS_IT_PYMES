# Instalación de Zabbix en `srv-docker` (sin contenedor)

## Objetivo

Instalar Zabbix en el propio sistema (sin Docker) para monitorizar servidores y servicios críticos de la infraestructura IPVCSI.

---

## Componentes instalados

- Zabbix server
- Frontend web (Apache)
- Base de datos MySQL
- Zabbix Agent (para monitorizar el propio servidor)

---

## Pasos principales

1. Añadir repositorio oficial de Zabbix:

   ```bash
   wget https://repo.zabbix.com/zabbix/6.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_6.0-2+ubuntu22.04_all.deb
   dpkg -i zabbix-release_6.0-2+ubuntu22.04_all.deb
   apt update

2. Instalar paquetes:
   ```bash
   apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent mariadb-server

3. Crear base de datos:
   ```bash
   CREATE DATABASE zabbix CHARACTER SET utf8mb4 COLLATE utf8mb4_bin;
   
   CREATE USER zabbix@localhost IDENTIFIED BY 'clave_segura';
   
   GRANT ALL PRIVILEGES ON zabbix.* TO zabbix@localhost;

5. Importar el esquema y datos iniciales:
   ```bash
   zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql -uzabbix -p zabbix

6. Configurar /etc/zabbix/zabbix_server.conf:

   DBPassword=clave_segura

7. Iniciar servicios:
   ```bash
   systemctl enable zabbix-server zabbix-agent apache2
   systemctl start zabbix-server zabbix-agent apache2

---

## Acceso web:

   URL: http://10.20.10.12/zabbix
   Usuario por defecto: Admin
   Contraseña: zabbix



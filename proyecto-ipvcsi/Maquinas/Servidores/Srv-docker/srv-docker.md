# Servidor `srv-docker` – Servicios empresariales y multimedia

## Información general

- **Nombre del servidor:** `srv-docker`
- **Dirección IP:** `10.20.10.12`
- **Sistema operativo:** Ubuntu Server 22.04 LTS
- **Ubicación:** Sede Castellón
- **Funciones:** alojamiento de servicios dockerizados y herramientas instaladas manualmente

---

## Servicios dockerizados desplegados

| Servicio        | Puerto local | Descripción                                  |
|-----------------|--------------|----------------------------------------------|
| Nextcloud       | 8088         | Nube privada para documentos y multimedia    |
| Pi-hole         | 53(UDP),9095 | Filtro de DNS y bloqueo de publicidad        |
| Plex            | 32400        | Servidor multimedia de vídeo                 |
| WG-Easy         | 51821        | Interfaz web para WireGuard VPN              |
| Watchtower      | —            | Actualización automática de contenedores     |
| Speedtest       | 9090         | Monitor de velocidad de conexión             |
| MySQL(Nextcloud)| 3306         | Base de datos de Nextcloud                   |

---

## Servicios instalados manualmente

- `Zabbix Server + Frontend + MySQL`: monitorización de infraestructura
- `Plex Media Server`: organización y reproducción de archivos multimedia

Para más información, consulta los archivos `zabbix.md` y `plex.md`.

---

## Backups y mantenimiento

- Duplicati configurado para realizar copias locales y programadas
- Volúmenes de Docker montados en `/srv/docker_data`
- Watchtower revisa y actualiza contenedores automáticamente (excepto Zabbix y Plex)

---

## Pruebas realizadas

- Acceso a todos los servicios desde navegador interno 
- Nextcloud operativo con usuarios de ejemplo 
- Zabbix visualizando métricas del dominio y red  
- Plex funcionando en la red local
- Copias automatizadas con Duplicati

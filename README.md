# Infraestructura IT para PYMES con Virtualización, Contenedores y Seguridad Integral

**Autor:** Juan José Castillo Rodríguez  
**Centro:** IES La Vereda  
**Ciclo Formativo:** 2º ASIR  
**Curso académico:** 2024–2025  
**Tutora:** Andrea Jordán Jordán  

## Descripción del proyecto

Este proyecto tiene como objetivo el diseño e implementación de una infraestructura IT simulada para una empresa ficticia llamada **IPVCSI (Infraestructura Profesional Virtualizada y Cibersegura S.L.)**, dedicada a la gestión de contenido multimedia.

La solución se basa en tecnologías actuales como:
- Virtualización con VirtualBox
- Contenedores Docker
- Seguridad mediante firewall y VPN
- Alta disponibilidad y copias de seguridad
- Monitorización y automatización

Se ha creado una red con dos sedes (Castellón y Madrid) conectadas por VPN para simular un entorno real de producción.

## Tecnologías utilizadas

- **Windows Server 2019/2022** (Active Directory, DNS, GPOs)
- **Ubuntu Server 22.04** (Docker, Nextcloud, Plex, etc.)
- **Docker + Portainer**
- **pfSense** (Firewall, DHCP, VPN WireGuard)
- **Duplicati + Veeam Agent** (Backups)
- **Zabbix + Speedtest Tracker** (Monitorización)
- **Watchtower** (Actualizaciones automáticas)
- **DuckDNS + WG-Easy** (VPN dinámica)

## Topología

- **Sede Castellón**: Red 10.20.10.0/24  
- **Sede Madrid**: Red 10.30.10.0/24  
- **VPN WireGuard**: Red 10.99.99.0/24  
- **Red NAT compartida para WAN**: 10.0.0.0/16

## Servidores desplegados

| Nombre        | Rol                                      | IP            |
|---------------|-------------------------------------------|---------------|
| `srv-ad`      | Controlador de dominio principal          | 10.20.10.11   |
| `srv-ad2`     | Controlador de dominio secundario         | 10.20.10.21   |
| `srv-docker`  | Servidor principal con contenedores       | 10.30.10.11   |
| `srv-docker2` | Réplica del servidor docker (Madrid)      | 10.30.10.12   |

## Seguridad implementada

- Cortafuegos con reglas específicas en pfSense
- Red interna segmentada y controlada
- VPN segura con WireGuard
- Backups cifrados y automáticos
- Servicios expuestos con puertos personalizados

## Alta disponibilidad

- Controlador de dominio secundario (`srv-ad2`)
- Réplica del servidor de servicios (`srv-docker2`)
- Comprobaciones de restauración completas
- Documentación de emergencia para fallos críticos

## Servicios desplegados en Docker

- Nextcloud (nube privada)
- Plex (streaming multimedia)
- Pi-hole (bloqueador DNS)
- WG-Easy (VPN sencilla)
- Duplicati (backup cifrado)
- Speedtest Tracker (test de red)
- Zabbix (monitorización)
- Watchtower (auto-updates)
- MySQL y otros

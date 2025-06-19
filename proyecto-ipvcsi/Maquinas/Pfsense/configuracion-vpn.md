# Configuración VPN WireGuard entre sedes – pfSense Castellón ↔ Madrid

## Objetivo

Conectar dos redes LAN remotas como si fueran una sola, mediante VPN site-to-site con WireGuard.

## Datos generales

- **Red sede Castellón (LAN):** 10.20.10.0/24  
- **Red sede Madrid (LAN):** 10.30.10.0/24  
- **Red VPN WireGuard:** 10.99.99.0/24  
- **Puerto WireGuard personalizado:** 51420 UDP

---

## Servidor VPN – pfSense Castellón

- IP WAN: `10.0.2.15` (NAT VirtualBox)
- IP LAN: `10.20.10.1`
- IP VPN (túnel): `10.99.99.1`
- Puerto: `51420/UDP`
- Clave pública: `[clave pública Castellón]`
- Clave privada: `[privada – no se publica]`

### Allowed IPs para el peer (Madrid):

- 10.99.99.2/32
- 10.30.10.0/24

---

## Cliente VPN – pfSense Madrid

- IP WAN: `10.0.20.15` (NAT VirtualBox)
- IP LAN: `10.30.10.1`
- IP VPN (túnel): `10.99.99.2`
- Clave pública: `[clave pública Madrid]`
- Clave privada: `[privada – no se publica]`

### Allowed IPs para el peer (Castellón):

- 10.99.99.1/32
- 10.20.10.0/24

---

## Rutas estáticas añadidas

En ambos pfSense:

- En Castellón: ruta estática → `10.30.10.0/24` → gateway: `WG0`
- En Madrid: ruta estática → `10.20.10.0/24` → gateway: `WG0`

---

## Estado y verificación

- `Status > WireGuard` muestra handshake activo
- Ping entre:
  - `10.20.10.11` (srv-ad) y `10.30.10.22` (srv-docker2) → OK
  - `10.20.10.1` ↔ `10.30.10.1` → OK


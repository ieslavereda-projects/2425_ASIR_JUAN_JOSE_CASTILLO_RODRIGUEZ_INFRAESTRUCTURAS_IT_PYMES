# Reglas de Firewall – pfSense (Sede Castellón y Madrid)

## Interfaz LAN – pfSense Castellón (red 10.20.10.0/24)

| # | Descripción                               | Fuente           | Destino          | Protocolo | Acción |
|---|-------------------------------------------|------------------|------------------|-----------|--------|
| 1 | Permitir todo el tráfico LAN              | LAN net          | any              | any       | Pass   |
| 2 | Permitir tráfico hacia VPN (Madrid)       | 10.20.10.0/24    | 10.30.10.0/24    | any       | Pass   |

## Interfaz WAN – pfSense Castellón

| # | Descripción                               | Fuente           | Puerto destino | Protocolo | Acción |
|---|-------------------------------------------|------------------|----------------|-----------|--------|
| 1 | Permitir conexión VPN WireGuard           | any              | 51420          | UDP       | Pass   |

## Interfaz WG0 – VPN Castellón

| # | Descripción                               | Fuente           | Destino          | Protocolo | Acción |
|---|-------------------------------------------|------------------|------------------|-----------|--------|
| 1 | Permitir tráfico desde Madrid por VPN     | 10.99.99.2       | 10.20.10.0/24    | any       | Pass   |

---

## Interfaz LAN – pfSense Madrid (red 10.30.10.0/24)

| # | Descripción                               | Fuente           | Destino          | Protocolo | Acción |
|---|-------------------------------------------|------------------|------------------|-----------|--------|
| 1 | Permitir todo el tráfico LAN              | LAN net          | any              | any       | Pass   |
| 2 | Permitir tráfico hacia VPN (Castellón)    | 10.30.10.0/24    | 10.20.10.0/24    | any       | Pass   |

## Interfaz WG0 – VPN Madrid

| # | Descripción                               | Fuente           | Destino          | Protocolo | Acción |
|---|-------------------------------------------|------------------|------------------|-----------|--------|
| 1 | Permitir tráfico desde Castellón por VPN  | 10.99.99.1       | 10.30.10.0/24    | any       | Pass   |

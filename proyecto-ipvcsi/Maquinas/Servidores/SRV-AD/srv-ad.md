# Servidor `srv-ad` – Controlador de Dominio Principal

## Información general

- **Nombre del servidor:** `srv-ad`
- **Dirección IP:** `10.20.10.11`
- **Sistema operativo:** Windows Server 2022 Standard
- **Rol principal:** Controlador de Dominio (Active Directory)
- **Ubicación:** Sede Castellón

---

## Dominio y estructura

- **Nombre del dominio:** `ipvcsi.local`
- **Estructura de Unidades Organizativas (OUs):**

ipvcsi.local
├── Domain Controller
│ ├── srv-ad
│ └── srv-ad2
├── Equipos
├── Usuarios
└── Sedes
     ├── Castellón
     │        ├── Equipos
     │        └── Usuarios
     │                └── Departamentos
     │                           ├── Administración
     │                           ├── Marketing
     │                           ├── Soporte IT
     │                           └── Dirección
     └── Madrid

---

## Roles FSMO asignados

El servidor `srv-ad` contiene los **cinco roles FSMO** del dominio:

1. **Schema Master**
2. **Domain Naming Master**
3. **RID Master**
4. **PDC Emulator**
5. **Infrastructure Master**

> Estos roles se replican hacia el controlador secundario `srv-ad2` para alta disponibilidad.

---

## Configuración DNS

- Zona directa: `ipvcsi.local`  
- Zona inversa: `10.20.10.x`  
- Reenvío DNS configurado hacia pfSense (`10.20.10.1`)  
- Clientes configurados para usar este servidor como DNS primario

---

## Configuración NTP

El servidor `srv-ad` actúa como **referencia horaria para toda la red**:

- Sincroniza con `es.pool.ntp.org` por defecto
- Clientes sincronizan con `srv-ad` automáticamente

---

## Políticas de grupo (GPO) aplicadas

> Políticas asignadas por unidad organizativa usando `gpmc.msc`.


- **Dirección**: fondo de pantalla corporativo, escritorio personalizado  
- **Administración**: mapeo de unidad Z:\ con carpeta compartida  
- **Edición**: acceso a carpetas multimedia, sin acceso al panel de control

---

## Restauración y emergencia

- Copia de seguridad de estado del sistema (Windows Server Backup)
- Documento para restauración de FSMO disponible (`manual-fsmo.md`)
- Validación de replicación con `repadmin /replsummary`

---

## Pruebas realizadas

- Iniciar sesión en equipo cliente con usuario creado 
- Aplicación de políticas al reiniciar sesión 
- Replicación con `srv-ad2` verificada con `repadmin` 
- Restauración FSMO en entorno controlado 
- Consulta DNS desde clientes correcta

---

## Archivos relacionados

- GUÍA COMPLETA DE CONMUTACIÓN Y RECUPERACIÓN DE CONTROLADOR DE DOMINIO.docx



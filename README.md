# INNOVATE TECH - Plataforma Integrada de Servicios Multimedia y Base de Datos en Cloud

Design and implementation of a centralized cloud multimedia infrastructure with managed audio/video streaming, WebRTC videoconferencing, and an audited relational database — deployed on an AWS EC2 instance.
Authors: Liam, Jheremy, Felix
Cycle: CFGS ASIX — Administracio de Sistemes Informatics en Xarxa
Centre: Institut Tecnologic de Barcelona
Academic year: 2025–2026
Project period: 13/04/2026 → 12/05/2026
Defence: 20/05/2026

## The Problem

Traditional on-premise localized deployments present severe limitations regarding scalability, high availability, and efficient resource distribution for media assets. In modern enterprise environments, managing heavy video-on-demand files, real-time live audio broadcasting, and low-latency communication require a decoupled infrastructure capable of segregating processing layers while maintaining strict persistence control and perimetric security boundaries.
This project responds to that reality by architecture-designing and deploying a centralized cloud platform on AWS. Moving away from localized data stores, every service is systematically provisioned, integrated, and performance-evaluated under a single fixed corporate IP identifier. Access traffic is hardened at the infrastructure level, ensuring that internal application communication, database triggers, and user-end exposure operate within deterministic, audited boundaries.

## What This Project Builds

A fully integrated cloud infrastructure hosted on an AWS EC2 instance running Ubuntu Server (node ip-172-31-46-28). The core framework consolidates an enterprise radio broadcasting service, a Video-on-Demand (VoD) portal, a zero-plugin WebRTC videoconferencing environment, and a relational transactional database. All layers are secured via targeted Security Groups and audit mechanisms.

## Three-Layer Architecture

┌─────────────────────────────────────────────────────────┐
│  CAPA 3 — INFRAESTRUCTURA Y PERIMETRO (AWS VPC)          │
│  EC2 Ubuntu Server · Security Groups · Reglas de Entrada │
│  Punto de entrada unico · IP publica fija 98.83.198.167 │
└────────────────────────┬────────────────────────────────┘
                         │ filtrado y distribucion de puertos
┌────────────────────────▼────────────────────────────────┐
│  CAPA 2 — SERVICIOS MULTIMEDIA (Streaming y WebRTC)     │
│  Icecast2 · Jellyfin (VoD) · Jitsi Meet (Prosody/JVB)  │
│  Ingesta por BUTT · Streaming HLS · Comunicacion WebRTC │
└────────────────────────┬────────────────────────────────┘
                         │ persistencia e integracion de logs
┌────────────────────────▼────────────────────────────────┐
│  CAPA 1 — PERSISTENCIA Y CONTROL DE DATOS (Relacional)  │
│  MySQL / MariaDB · Triggers · Backups Automatizados    │
│  Registro de sesiones AV · Estructuras de privilegios   │
└─────────────────────────────────────────────────────────┘

Capa 1 — Persistencia y Control de Datos (Base de Datos): El motor relacional centraliza el almacenamiento de configuraciones, control de accesos y la auditoria automatizada. Los triggers registran eventos de streaming en la tabla log_events de manera automatica, mientras que tareas programadas en crontab aseguran copias de respaldo periodicas del esquema.

Capa 2 — Servicios Multimedia (Audio y Video): Capa encargada del procesamiento, codificacion y distribucion de flux multimedia. Gestiona la ingesta de emisiones de audio comprimido en tiempo real, el empaquetado de video bajo demanda adaptativo mediante segmentos HLS y el enrutamiento de videoconferencias síncronas.

Capa 3 — Infraestructura y Perimetro (Red Cloud): La VPC de AWS actua como el contenedor de seguridad perimetral de la maquina virtual. Restringe y autoriza las conexiones externas mapeando de forma estricta los sockets requeridos por los servicios de las capas inferiores, aislando el trafico administrativo del operativo.

## Operational Flow

### Flujo de Emision de Audio (Radio)
Cliente local (BUTT) → Conexion TCP Puerto 8000 (Credencial: ITB2026!)
                    → Punto de montaje unificado (/stream)
                    → Servidor Icecast2 (AWS EC2)
                    → Difusion publica (Stream MP3 CBR 128 kbps)
                    → Navegador Web del Cliente Final

### Flujo de Video bajo Demanda (VoD)
FileZilla SFTP (Puerto 22) → Transferencia segura de clip MP4 (H.264)
                          → Directorio de produccion /var/www/videos (chmod 777)
                          → Indexacion e inicializacion en Jellyfin (Puerto 8096)
                          → Streaming adaptativo HLS transcodificado
                          → Reproduccion nativa en navegador

### Flujo de Videoconferencia WebRTC
Usuario 1 (PC) + Usuario 2 (Movil 4G/5G) → Acceso cifrado HTTPS (Puerto TCP 443)
                                        → Servidor Jitsi Meet (Resolucion Hostname 98.83.198.167)
                                        → Validacion de Certificado TLS Autofirmado
                                        → Activacion de API WebRTC local en navegadores
                                        → Intercambio de streams multimedia via Puerto UDP 10000 (JVB)
                                        → Videollamada activa bidireccional

## Technology Stack

| Componente | Tecnologia | Rol / Proposito |
| :--- | :--- | :--- |
| Proveedor Cloud | AWS (VPC, EC2, Security Groups) | Aprovisionamiento del nodo virtual y politicas de filtrado perimetral. |
| Sistema Operativo | Ubuntu Server v22.04 LTS | Sistema operativo base de produccion (nodo ip-172-31-46-28). |
| Servidor de Audio | Icecast2 | Distribucion y montaje del flujo de audio en streaming continuo. |
| Cliente de Ingesta | BUTT (Broadcast Using This Tool) | Captura de entrada local, modulacion y codificacion MP3 hacia el cloud. |
| Plataforma VoD | Jellyfin | Gestion de librerias de video y streaming HLS de archivos locales. |
| Videoconferencia | Jitsi Meet (Jicofo, JVB, Prosody) | Orquestacion XMPP y transmision WebRTC síncrona multicliente. |
| Motor de Base de Datos| MySQL / MariaDB | Modelo relacional, persistencia, triggers y control de roles. |
| Gestor de Archivos | SFTP / FileZilla | Carga segura de assets multimedia y extraccion de respaldos SQL. |
| Telemetria y Red | iperf3 / speedtest-cli / htop | Cuantificacion de ancho de banda, latencias y estres de CPU/RAM. |

## Technical Validation — Quality Assurance

El correcto funcionamiento de la infraestructura cloud se ratifica mediante pruebas funcionales detalladas en la documentacion especifica de cada bloque:

### Validacion de Servicios Multimedia (Bloque 2)
* Flujo de Audio Estable: Verificacion del socket TCP 8000 operando en segundo plan y modulacion correcta en el vúmetro de BUTT al conectar el stream.
* Transmision de Video sin Bloqueos: Resolucion de incidencias de tiempo de espera excesivo (timeout) abriendo el puerto TCP 8096, logrando la reproduccion directa HLS del archivo MP4 subido en `/var/www/videos`.
* Conectividad WebRTC Multiplataforma: Mitigacion de la ausencia de camaras en monitores locales mediante la conexion cruzada de un smartphone a traves de redes moviles independientes, evadiendo colisiones de bucle de red (NAT Loopback) y manteniendo la llamada fluida a traves del puerto UDP 10000.
* Rendimiento del Servidor: Pruebas de carga utilizando htop concurrentemente con todos los servicios multimedia en ejecucion para certificar la estabilidad de la CPU y memoria RAM.

### Validacion de Estructuras de Datos (Bloque 3)
* Integridad de Esquemas: Ejecucion de SHOW TABLES constatando la existencia y vinculacion de las entidades disenadas en el diagrama E-R.
* Control de Privilegios: Auditoria via SHOW GRANTS comprobando el aislamiento de usuarios y denegacion automatica ante accesos no autorizados.
* Automatizacion: Verificacion del correcto disparo de triggers almacenando eventos en log_events y validacion de tareas Cron generando volcados .sql estables.

## Repository Structure

innovate-tech-projecte/
├── README.md                        # Indice general, IP publica y matriz de puertos corporativos
├── bloque1-infraestructura/         # Modulo técnico liderado por LIAM
│   ├── README.md                    # Documentacion de diseno de CPD, VPC, EC2, SFTP y logs
│   └── captures/                    # Evidencias graficas (Planos, AWS Console, FileZilla status)
├── bloque2-audio-video/             # Modulo técnico liderado por JHEREMY
│   ├── README.md                    # Manual de instalacion manual de Jellyfin, Icecast2, Jitsi y telemetria
│   └── captures/                    # Evidencias (Terminal systemctl status, streaming web, htop metrics)
└── bloque3-base-dades/              # Modulo técnico liderado por FELIX
    ├── README.md                    # Documentacion del modelo relacional, roles, triggers y backups
    ├── captures/                    # Evidencias (Diagramas E-R, consultas SHOW, outputs de scripts)
    └── scripts/                     # Ficheros fuentes .sql (Creacion de tablas, triggers, crontab setup)

## Methodology

El desarrollo tecnologico se ha estructurado bajo el marco de trabajo agil SCRUM, dividiendo los hitos de implementacion en sprints secuenciales indexados en la documentacion:

| Sprint | Periodo | Enfoque Tecnico Principal |
| :--- | :--- | :--- |
| Sprint 1 | 13/04/2026 → 24/04/2026 | Diseno de planos CPD, topologia de red AWS VPC y analisis inicial de mercado. |
| Sprint 2 | 27/04/2026 → 12/05/2026 | Despliegue manual de servicios multimedia, securizacion de puertos, modelo E-R e integracion BD. |

## Key Verification Documents

| Documento Interno | Descripcion |
| :--- | :--- |
| bloque1-infraestructura/README.md | Especificaciones de la arquitectura de red cloud y parametrizacion del servidor perimetral. |
| bloque2-audio-video/README.md | Procedimiento paso a paso para el despliegue multimedia, comandos de recuperacion y analisis de ancho de banda. |
| bloque3-base-dades/README.md | Definicion de politicas de triggers, automatizacion de copias de seguridad e integracion orientada al servicio. |

## Deployment Prerequisites

Para levantar los servicios de la plataforma desde un estado de parada total:
1. Acceder a la consola de AWS e iniciar la instancia EC2 Ubuntu Server corporativa.
2. Comprobar la asignacion de la direccion IP publica fija: `98.83.198.167`.
3. Conectar por SSH y verificar el estado general de los demonios basicos: `sudo systemctl start icecast2 jellyfin prosody`.
4. Auditar la escucha de sockets de red mediante el comando: `sudo netstat -tuln | grep -E "8000|8096|443|10000|3306"`.
5. Iniciar la ingesta remota de assets y transmisiones segun los manuales especificos indexados.

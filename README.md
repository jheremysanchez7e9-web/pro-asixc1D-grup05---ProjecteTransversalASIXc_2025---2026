# INNOVATE TECH - Plataforma Integrada de Serveis Multimèdia i Base de Dades en Cloud

Design and implementation of a centralized cloud multimedia infrastructure with managed audio/video streaming, WebRTC videoconferencing, and an audited relational database — deployed on an AWS EC2 instance.
Authors: Liam, Jheremy, Felix
Cycle: CFGS ASIX — Administració de Sistemes Informàtics en Xarxa
Centre: Institut Tecnològic de Barcelona
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
│  CAPA 3 — INFRAESTRUCTURA I PERÍMETRE (AWS VPC)          │
│  EC2 Ubuntu Server · Security Groups · Regles d'Entrada │
│  Punt d'entrada únic · IP pública fixa 98.83.198.167    │
└────────────────────────┬────────────────────────────────┘
                         │ filtratge i distribució de ports
┌────────────────────────▼────────────────────────────────┐
│  CAPA 2 — SERVEIS MULTIMÈDIA (Streaming i WebRTC)       │
│  Icecast2 · Jellyfin (VoD) · Jitsi Meet (Prosody/JVB)   │
│  Ingesta per BUTT · Streaming HLS · Comunicació WebRTC  │
└────────────────────────┬────────────────────────────────┘
                         │ persistència i integració de logs
┌────────────────────────▼────────────────────────────────┐
│  CAPA 1 — PERSISTÈNCIA I CONTROL DE DADES (Relacional)  │
│  MySQL / MariaDB · Triggers · Backups Automatitzats     │
│  Registre de sessions AV · Estructures de privilegis    │
└─────────────────────────────────────────────────────────┘

Capa 1 — Persistència i Control de Dades (Base de Dades): El motor relacional centralitza l'emmagatzematge de configuracions, control d'accessos i l'auditoria automatitzada. Els triggers registren esdeveniments de streaming a la taula log_events de manera automàtica, mentre que tasques programades en crontab asseguren còpies de seguretat periòdiques de l'esquema.

Capa 2 — Serveis Multimèdia (Àudio i Vídeo): Capa encarregada del processament, codificació i distribució de fluxos multimèdia. Gestiona la ingesta d'emissions d'àudio comprimit en temps real, l'empaquetat de vídeo sota demanda adaptatiu mitjançant segments HLS i l'enrutament de videoconferències síncrones.

Capa 3 — Infraestructura i Perímetre (Xarxa Cloud): La VPC d'AWS actua com el contenidor de seguretat perimetral de la màquina virtual. Restringeix i autoritza les connexions externes mapejant de forma estricta els sockets requerits pels serveis de les capes inferiors, aïllant el trànsit administratiu de l'operatiu.

## Operational Flow

### Flux d'Emissió d'Àudio (Ràdio)
Client local (BUTT) → Connexió TCP Port 8000 (Credencial: ITB2026!)
                    → Punt de muntatge unificat (/stream)
                    → Servidor Icecast2 (AWS EC2)
                    → Difusió pública (Stream MP3 CBR 128 kbps)
                    → Navegador Web del Client Final

### Flux de Vídeo sota Demanda (VoD)
FileZilla SFTP (Port 22) → Transferència segura de clip MP4 (H.264)
                          → Directori de producció /var/www/videos (chmod 777)
                          → Indexació i inicialització a Jellyfin (Port 8096)
                          → Streaming adaptatiu HLS transcodificat
                          → Reproducció nativa en navegador

### Flux de Videoconferència WebRTC
Usuari 1 (PC) + Usuari 2 (Mòbil 4G/5G) → Accés xifrat HTTPS (Port TCP 443)
                                        → Servidor Jitsi Meet (Resolució Hostname 98.83.198.167)
                                        → Validació de Certificat TLS Autofirmat
                                        → Activació de l'API WebRTC local en navegadors
                                        → Intercanvi de fluxos multimèdia via Port UDP 10000 (JVB)
                                        → Videollamada activa bidireccional

## Technology Stack

| Component | Tecnologia | Rol / Propòsit |
| :--- | :--- | :--- |
| Proveïdor Cloud | AWS (VPC, EC2, Security Groups) | Aprovisionament del node virtual i polítiques de filtratge perimetral. |
| Sistema Operatiu | Ubuntu Server v22.04 LTS | Sistema operatiu base de producció (node ip-172-31-46-28). |
| Servidor d'Àudio | Icecast2 | Distribució i muntatge del flux d'àudio en streaming continu. |
| Client d'Ingesta | BUTT (Broadcast Using This Tool) | Captura d'entrada local, modulació i codificació MP3 cap al cloud. |
| Plataforma VoD | Jellyfin | Gestió de llibreries de vídeo i streaming HLS d'arxius locals. |
| Videoconferència | Jitsi Meet (Jicofo, JVB, Prosody) | Orquestració XMPP i transmissió WebRTC síncrona multiclient. |
| Motor de Base de Dades| MySQL / MariaDB | Model relacional, persistència, triggers i control de rols. |
| Gestor d'Arxius | SFTP / FileZilla | Càrrega segura d'assets multimèdia i extracció de vòlculs SQL. |
| Telemetria i Xarxa | iperf3 / speedtest-cli / htop | Quantificació d'amplada de banda, latències i estrès de CPU/RAM. |

## Technical Validation — Quality Assurance

El correcte funcionament de la infraestructura cloud es ratifica mitjançant proves funcionals detallades en la documentació específica de cada bloc:

### Validació de Serveis Multimèdia (Bloc 2)
* Flux d'Àudio Estable: Verificació del socket TCP 8000 operant en segon pla i modulació correcta en el vúmetre de BUTT en connectar el stream.
* Transmissió de Vídeo sense Bloquejos: Resolució d'incidències de temps d'espera excessiu (timeout) obrint el port TCP 8096, aconseguint la reproducció directa HLS de l'arxiu MP4 pujat a `/var/www/videos`.
* Connectivitat WebRTC Multiplataforma: Mitigació de l'absència de càmeres en monitors locals mitjançant la connexió creuada d'un smartphone a través de xarxes mòbils independents, evitant col·lisions de bucle de xarxa (NAT Loopback) i mantenint la trucada fluida a través del port UDP 10000.
* Rendiment del Servidor: Proves de càrrega utilitzant htop concurrentment amb tots els serveis multimèdia en execució per certificar l'estabilitat de la CPU i memòria RAM.

### Validació d'Estructures de Dades (Bloc 3)
* Integritat d'Esquemes: Execució de SHOW TABLES constatant l'existència i vinculació de les entitats dissenyades en el diagrama E-R.
* Control de Privilegis: Auditoria via SHOW GRANTS comprovant l'aïllament d'usuaris i denegació automàtica davant d'accessos no autoritzats.
* Automatització: Verificació del correcte dispar d'actuadors (triggers) emmagatzemant esdeveniments a log_events i validació de tasques Cron generant vòlculs .sql estables.

## Repository Structure

innovate-tech-projecte/
├── README.md                        # Índex general, IP pública i matriu de ports corporatius
├── bloque1-infraestructura/         # Mòdul tècnic liderat per LIAM
│   ├── README.md                    # Documentació de disseny de CPD, VPC, EC2, SFTP i logs
│   └── captures/                    # Evidències gràfiques (Plànols, AWS Console, FileZilla status)
├── bloque2-audio-video/             # Mòdul tècnic liderat per JHEREMY
│   ├── README.md                    # Manual d'instal·lació manual de Jellyfin, Icecast2, Jitsi i telemetria
│   └── captures/                    # Evidències (Terminal systemctl status, streaming web, htop metrics)
└── bloque3-base-dades/              # Mòdul tècnic liderat per FELIX
    ├── README.md                    # Documentació del model relacional, rols, triggers i backups
    ├── captures/                    # Evidències (Diagrames E-R, consultes SHOW, outputs de scripts)
    └── scripts/                     # Fitxers fonts .sql (Creació de taules, triggers, crontab setup)

## Methodology

El desenvolupament tecnològic s'ha estructurat sota el marc de treball àgil SCRUM, dividint les fites d'implementació en sprints seqüencials indexats en la documentació:

| Sprint | Període | Enfocament Tècnic Principal |
| :--- | :--- | :--- |
| Sprint 1 | 13/04/2026 → 24/04/2026 | Disseny de plànols CPD, topologia de xarxa AWS VPC i anàlisi inicial de mercat. |
| Sprint 2 | 27/04/2026 → 12/05/2026 | Desplegament manual de serveis multimèdia, securització de ports, model E-R i integració BD. |

## Key Verification Documents

| Document Intern | Descripció |
| :--- | :--- |
| bloque1-infraestructura/README.md | Especificacions de la arquitectura de xarxa cloud i parametrització del servidor perimetral. |
| bloque2-audio-video/README.md | Procediment pas a pas pel desplegament multimèdia, comandes de recuperació i anàlisi d'amplada de banda. |
| bloque3-base-dades/README.md | Definició de polítiques de triggers, automatització de còpies de seguretat i integració orientada al servei. |

## Deployment Prerequisites

Per aixecar els serveis de la plataforma des d'un estat de parada total:
1. Accedir a la consola d'AWS i iniciar la instància EC2 Ubuntu Server corporativa.
2. Comprovar l'assignació de l'adreça IP pública fixa: `98.83.198.167`.
3. Connectar per SSH i verificar l'estat general dels dimonis bàsics: `sudo systemctl start icecast2 jellyfin prosody`.
4. Auditar l'escolta de sockets de xarxa mitjançant la comanda: `sudo netstat -tuln | grep -E "8000|8096|443|10000|3306"`.
5. Iniciar la ingesta remota d'assets i transmissions segons els manuals específics indexats.

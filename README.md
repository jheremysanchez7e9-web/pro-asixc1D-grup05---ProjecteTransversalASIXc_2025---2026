# INNOVATE TECH - Plataforma Integrada de Serveis Multimèdia i Base de Dades en Cloud

Disseny i implementació d'una infraestructura multimèdia centralitzada en el cloud amb streaming d'àudio/vídeo gestionat, videoconferència WebRTC i una base de dades relacional auditada — desplegat en una instància AWS EC2.
Autors: Liam, Jheremy, Felix
Cicle: CFGS ASIX — Administració de Sistemes Informàtics en Xarxa
Centre: Institut Tecnològic de Barcelona
Any acadèmic: 2025–2026
Període del projecte: 
Defensa: 

## El Problema

Els desplegaments locals tradicionals on-premise presenten severes limitacions pel que fa a l'escalabilitat, l'alta disponibilitat i la distribució eficient de recursos per als actius multimèdia. En els entorns empresarials moderns, la gestió de fitxers pesats de vídeo sota demanda, la radiodifusió d'àudio en directe en temps real i la comunicació de baixa latència requereixen una infraestructura desacoblada capaç de segregar les capes de processament mentre es manté un control estricte de la persistència i els límits de seguretat perimetral.
Aquest projecte respon a aquesta realitat mitjançant el disseny de l'arquitectura i el desplegament d'una plataforma cloud centralitzada a AWS. Allunyant-se dels emmagatzematges de dades locals, cada servei s'aprovisiona, s'integra i s'avalua el seu rendiment de manera sistemàtica sota un únic identificador d'IP corporativa fixa. El trànsit d'accés s'endureix a nivell d'infraestructura, assegurant que la comunicació interna de les aplicacions, els triggers de la base de dades i l'exposició a l'usuari final operin dins de límits deterministes i auditats.

## Què Construeix Aquest Projecte

Una infraestructura cloud completament integrada i allotjada en una instància AWS EC2 que executa Ubuntu Server (node ip-172-31-46-28). L'entorn central consolida un servei de radiodifusió empresarial, un portal de vídeo sota demanda (VoD), un entorn de videoconferència WebRTC sense connectors (zero-plugin) i una base de dades transaccional relacional. Totes les capes estan protegides mitjançant Security Groups específics i mecanismes d'auditoria.

## Arquitectura de Tres Capes

┌─────────────────────────────────────────────────────────┐
│  CAPA 3 — INFRAESTRUCTURA I PERÍMETRE (AWS VPC)         │
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

## Flux Operatiu

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
                                        → Videotrucada activa bidireccional

## Stack Tecnològic

| Component | Tecnologia | Rol / Propòsit |
| :--- | :--- | :--- |
| Proveïdor Cloud | AWS (VPC, EC2, Security Groups) | Aprovisionament del node virtual i polítiques de filtratge perimetral. |
| Sistema Operatiu | Ubuntu Server v22.04 LTS | Sistema operatiu base de producció (node ip-172-31-46-28). |
| Servidor d'Àudio | Icecast2 | Distribució i muntatge del flux d'àudio en streaming continu. |
| Client d'Ingesta | BUTT (Broadcast Using This Tool) | Captura d'entrada local, modulació i codificació MP3 cap al cloud. |
| Plataforma VoD | Jellyfin | Gestió de llibreries de vídeo i streaming HLS d'arxius locals. |
| Videoconferència | Jitsi Meet (Jicofo, JVB, Prosody) | Orquestració XMPP i transmissió WebRTC síncrona multiclient. |
| Motor de Base de Dades | MySQL / MariaDB | Model relacional, persistència, triggers i control de rols. |
| Gestor d'Arxius | SFTP / FileZilla | Càrrega segura d'assets multimèdia i extracció de vòlculs SQL. |
| Telemetria i Xarxa | iperf3 / speedtest-cli / htop | Quantificació d'amplada de banda, latències i estrès de CPU/RAM. |

## Validació Tècnica — Quality Assurance

El correcte funcionament de la infraestructura cloud es ratifica mitjançant proves funcionals detallades en la documentació específica de cada bloc:

### Validació de Serveis Multimèdia (Bloc 2)
* **Flux d'Àudio Estable:** Verificació del socket TCP 8000 operant en segon pla i modulació correcta en el vúmetre de BUTT en connectar el stream.
* **Transmissió de Vídeo sense Bloquejos:** Resolució d'incidències de temps d'espera excessiu (timeout) obrint el port TCP 8096, aconseguint la reproducció directa HLS de l'arxiu MP4 pujat a `/var/www/videos`.
* **Connectivitat WebRTC Multiplataforma:** Mitigació de l'absència de càmeres en monitors locals mitjançant la connexió creuada d'un smartphone a través de xarxes mòbils independents, evitant col·lisions de bucle de xarxa (NAT Loopback) i mantenint la trucada fluida a través del port UDP 10000.
* **Rendiment del Servidor:** Proves de càrrega utilitzant htop concurrentment amb tots els serveis multimèdia en execució per certificar l'estabilitat de la CPU i memòria RAM.

### Validació d'Estructures de Dades (Bloc 3)
* **Integritat d'Esquemes:** Execució de `SHOW TABLES` constatant l'existència i vinculació de les entitats dissenyades en el diagrama E-R.
* **Control de Privilegis:** Auditoria via `SHOW GRANTS` comprovant l'aïllament d'usuaris i denegació automàtica davant d'accessos no autoritzats.
* **Automatització:** Verificació del correcte dispar d'actuadors (triggers) emmagatzemant esdeveniments a `log_events` i validació de tasques Cron generant vòlculs `.sql` estables.

## Estructura del Repositori

```text
innovate-tech-projecte/
├── .gitignore                             # Filtre de fitxers exclosos del sistema (logs locals, .DS_Store, temporals)
├── README.md                              # Índex global, direccionament IP pública (98.83.198.167) i taula de ports
│
├── documentacio/                          # COBERTA DOCUMENTAL I PLANIFICACIÓ GLOBAL DEL GRUP
│   ├── memoria/                           # Document de text i memòria final del projecte (.pdf / .docx)
│   ├── arquitectura/                      # Diagrames de blocs logicials i relació de dependències de xarxa
│   ├── topologia/                         # Plànols estructurals d'infraestructura (Cisco Packet Tracer / Draw.io)
│   └── captures-generals/                 # Evidències de validació globals o de funcionament d'equip
│
├── bloc1-infraestructura-cloud/           # INFRAESTRUCTURA EN NÚVOL I SERVEIS DE GESTIÓ · Liam
│   ├── README.md                          # Full de ruta regional, configuració de tallafocs i llista de captures QA
│   ├── captures/                          # Evidències gràfiques d'auditoria (PAS_1.1 a PAS_1.6)
│   ├── aws/                               # Configuracions declaratives de la VPC, subxarxes i regles de Security Groups
│   ├── apache/                            # Fitxers de configuració de llocs web i directoris VirtualHosts
│   ├── sftp/                              # Parametrització del dimoni SSH per a la transferència de fitxers xifrada
│   ├── ldap/                              # Arxius d'estructura, esquemes de directori actiu i fitxers d'usuaris (.ldif)
│   ├── graylog/                           # Dashboards, inputs i encaminaments de logs del sistema via rsyslogd
│   ├── ansible/                           # Playbooks i rols per a l'automatització del desplegament de paquets
│   ├── scripts/
│   │   └── provisionament.sh              # Script en Bash d'ajuda per accelerar la instal·lació inicial del node
│   └── troubleshooting/                   # Diari de resolució de conflictes de xarxa, errors de ports o permisos
│
├── bloc2-audio-video/                     # PROCESSAMENT MULTIMÈDIA I TELEMETRIA DE XARXA · Jheremy
│   ├── README.md                          # Arquitectura de fluxos de streaming, codificació de còdecs i taula de sockets
│   ├── captures/                          # Evidències gràfiques d'auditoria (PAS_2.1 a PAS_2.5)
│   ├── jellyfin/                          # Paràmetres d'optimització HLS i llibreries de vídeo sota demanda (VoD)
│   ├── icecast2/                          # Arquitectura del fitxer de configuració icecast.xml i definició de muntatges
│   ├── jitsi/                             # Sockets de control HTTPS i assignació de ports UDP del Jitsi Videobridge (JVB)
│   ├── monitoritzacio/                    # Configuració de mètriques del sistema, alertes de rendiment i llindars de consum
│   ├── scripts/
│   │   └── mesura_rendiment.sh            # Script en Bash d'automatització de telemetria (iperf3 i speedtest-cli)
│   └── troubleshooting/                   # Resolució d'errors de NAT Loopback, desconnexions o talls en el flux de ràdio
│
└── bloc3-base-de-dades/                   # ENGINYERIA DE DADES I INTEGRACIÓ DE SISTEMES CREUATS · Felix
    ├── README.md                          # Disseny relacional, seguretat lògica d'accessos i documentació d'actuadors
    ├── captures/                          # Evidències gràfiques d'auditoria (PAS_3.1 a PAS_3.8)
    ├── mysql/                             # Arxius de paràmetres d'optimització i configuració del motor (my.cnf)
    ├── model-relacional/                  # Imatges del disseny i diagrames Entitat-Relació (E-R) normalitzats
    ├── triggers-i-procediments/           # Codi neta de funcions procedimentals externes i rutines del gestor
    ├── backups/
    │   └── 04_backup_cron.sh              # Script Bash encarregat de l'automatització i exportació de dumps mysqldump
    ├── scripts-sql/
    │   ├── 01_creacio_esquema.sql         # DDL: Instanciació de la Base de Dades, definició de taules i claus foranes
    │   ├── 02_usuaris_privilegis.sql      # DCL: Polítiques de control d'accés, perfils i directives GRANT unificades
    │   └── 03_triggers_auditoria.sql      # DML: Lògica de triggers per alimentar de forma automatitzada la taula log_events
    └── troubleshooting/                   # Resolució de fallades amb restriccions referencials o errors Access Denied

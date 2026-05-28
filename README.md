# INNOVATE TECH - Plataforma Integrada de Serveis Multimèdia i Base de Dades en Cloud

Disseny i implementació d'una infraestructura multimèdia centralitzada en el cloud amb streaming d'àudio/vídeo gestionat, videoconferència WebRTC i una base de dades relacional auditada — desplegat en una instància AWS EC2 per al projecte transversal.

**Autors:** Liam, Jheremy, Felix (Grup 5)  
**Cicle:** CFGS ASIX — Administració de Sistemes Informàtics en Xarxa  
**Centre:** Institut Tecnològic de Barcelona  
**Any acadèmic:** 2025–2026  

👉 [Anar directament a l'estructura del repositori](#-estructura-del-repositori)

---

## El Problema

Els desplegaments locals tradicionals on-premise presenten severes limitacions pel que fa a l'escalabilitat, l'alta disponibilitat i la distribució eficient de recursos per als actius multimèdia. En els entorns empresarials moderns, la gestió de fitxers pesats de vídeo sota demanda, la radiodifusió d'àudio en directe en temps real i la comunicació de baixa latència requereixen una infraestructura desacoblada capaç de segregar les capes de processament mentre es manté un control estricte de la persistència i els límits de seguretat perimetral.

Aquest projecte respon a aquesta realitat mitjançant el disseny de l'arquitectura i el desplegament d'una plataforma cloud centralitzada a AWS realitzada pel **Grup 5**. Allunyant-se dels emmagatzematges de dades locals, cada servei s'aprovisiona, s'integra i s'avalua el seu rendiment de manera sistemàtica sota un únic identificador d'IP corporativa fixa. El trànsit d'accés s'endureix a nivell d'infraestructura, assegurant que la comunicació interna de les aplicacions, els triggers de la base de dades i l'exposició a l'usuari final operin dins de límits deterministes i auditats.

## Què Construeix Aquest Projecte

Una infraestructura cloud completament integrada i allotjada en una instància AWS EC2 que executa Ubuntu Server. L'entorn central del **Grup 5** consolida un servei de radiodifusió, un portal de vídeo sota demanda (VoD) basat en Jellyfin, un entorn de videoconferència WebRTC de Jitsi Meet i una base de dades relacional. Totes les capes estan protegides mitjançant Security Groups específics de la plataforma d'Amazon.

## Arquitectura de Tres Capes

```text
┌─────────────────────────────────────────────────────────┐
│  CAPA 3 — INFRAESTRUCTURA I PERÍMETRE (AWS VPC)         │
│  EC2 Ubuntu Server · Security Groups · Regles d'Entrada │
│  Punt d'entrada únic · IP pública fixa 98.83.198.167    │
└────────────────────────┬────────────────────────────────┘
                         │ filtratge i distribució de ports
┌────────────────────────▼────────────────────────────────┐
│  CAPA 2 — SERVEIS MULTIMÈDIA (Streaming i WebRTC)       │
│  Icecast2 · Jellyfin (VoD) · Jitsi Meet (Prosody/JVB)   │
│  Ingesta / Playlist · Streaming HLS · Comunicació WebRTC│
└────────────────────────┬────────────────────────────────┘
                         │ persistència i integració (Treball Futur)
┌────────────────────────▼────────────────────────────────┐
│  CAPA 1 — PERSISTÈNCIA I CONTROL DE DADES (Relacional)  │
│  MySQL · Model Relacional · Triggers · Backups          │
│  Estructures de privilegis · Taula mesures_amplada_banda│
└─────────────────────────────────────────────────────────┘

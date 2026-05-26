# Projecte de Disseny d’un CPD Sostenible per InnovateTech

## 1. Introducció

InnovateTech és una empresa tecnològica que necessita modernitzar la seva infraestructura informàtica per oferir serveis de manera segura, estable i escalable.

Per aquest motiu, es planteja la creació d’un CPD (Centre de Processament de Dades) híbrid, combinant infraestructura física pròpia amb serveis desplegats al núvol mitjançant Amazon Web Services (AWS).

L’objectiu principal del projecte és garantir:

- Alta disponibilitat
- Seguretat física i lògica
- Escalabilitat
- Eficiència energètica
- Redundància
- Monitorització centralitzada
- Facilitat d’administració

---

# 2. Distribució física del CPD

El CPD s’ha dissenyat amb una estructura professional basada en centres de dades empresarials moderns.

La infraestructura es divideix en tres zones principals:

## Sala principal del CPD

Espai destinat als racks de servidors i equips de comunicacions.

Inclou:

- Rack de xarxa i comunicacions
- Rack de servidors
- Passadís fred
- Passadís calent
- Climatització redundant
- Sistema elèctric
- Sensors ambientals
- Sistema antiincendis

---

## Sala tècnica de preparació

Zona destinada al:

- muntatge de servidors
- manteniment
- reparacions
- emmagatzematge de components

Disposa de:

- taules antiestàtiques
- eines tècniques
- banc de proves
- equips spare

---

## Sala de monitorització (NOC)

Espai dedicat a la supervisió de tota la infraestructura.

Inclou:

- monitorització Graylog
- dashboards
- control de serveis
- supervisió de xarxa
- control d’accessos
- videovigilància

---

# 3. Característiques de la sala

La sala principal del CPD té aproximadament:

- 8 metres de llarg
- 6 metres d’ample
- 3 metres d’alçada

Superfície total:

48 m²

Aquesta distribució permet:

- circulació segura
- manteniment senzill
- correcta ventilació
- separació de fluxos d’aire

---

# 4. Terra tècnic i sostre tècnic

## Terra tècnic

S’ha implementat un terra tècnic elevat de 40 cm.

Per sota del terra passen:

- cablejat elèctric
- fibra òptica
- cablejat de xarxa
- conductes d’aire fred
- sensors i control

Avantatges:

- millor ventilació
- manteniment més senzill
- separació entre dades i electricitat
- major seguretat

---

## Sostre tècnic

El sostre tècnic permet:

- retorn d’aire calent
- instal·lació de càmeres
- sensors ambientals
- il·luminació LED
- detecció d’incendis

---

# 5. Climatització

La climatització s’ha dissenyat seguint criteris d’eficiència energètica.

## Temperatura

- 21°C ±2°C

## Humitat

- 45% - 55%

## Sistemes implementats

S’han instal·lat:

- 2 unitats de climatització de precisió (AC1 i AC2)
- configuració redundant 1+1

El flux d’aire es distribueix mitjançant:

- passadís fred
- passadís calent

---

# 6. Passadissos freds i calents

## Passadís fred

Situat davant dels racks.

Característiques:

- impulsió d’aire fred
- temperatura aproximada de 20°C
- refrigeració directa dels servidors

---

## Passadís calent

Situat darrere dels racks.

Característiques:

- expulsió d’aire calent
- temperatura aproximada de 30°C
- retorn cap als sistemes CRAC

---

# 7. Cablejat estructurat

## Tipus de cablejat

### Xarxa

- CAT6A
- fins a 10 Gbps

### Fibra òptica

- OM4 multimode

---

## Organització del cablejat

S’utilitzen:

- safates tècniques
- velcros
- etiquetatge
- codificació per colors

### Colors utilitzats

- Blau → Xarxa
- Vermell → Energia
- Groc → Fibra
- Verd → Sensors
- Lila → Seguretat

---

# 8. Distribució dels racks

## Rack 1 — Xarxa i comunicacions

Conté:

- Firewall
- Router ISP
- Switch Core 1
- Switch Core 2
- Patch Panels
- NAS Backups
- SAI secundari

---

## Rack 2 — Servidors

Conté:

- Servidor Web
- Servidor SFTP
- Servidor Logs
- Controlador AD
- Servidor Monitorització
- Servidor Backup

---

# 9. Infraestructura elèctrica

El CPD disposa de:

- alimentació redundant
- doble línia elèctrica
- SAI principal
- SAI secundari
- protecció diferencial

---

# 10. Sistema SAI (UPS)

S’ha implementat un sistema:

- APC Smart-UPS

Objectiu:

- mantenir els serveis actius durant talls elèctrics
- protegir els equips davant sobretensions

Autonomia estimada:

- 30 minuts

---

# 11. Seguretat física

## Control d’accés

La sala incorpora:

- RFID
- PIN
- registre d’accessos

Només el personal autoritzat pot accedir al CPD.

---

## Videovigilància

S’han instal·lat:

- 7 càmeres IP

Ubicades a:

- entrada
- passadissos
- racks
- zones crítiques

---

## Sensors implementats

- temperatura
- humitat
- fum
- fuita d’aigua
- pressió diferencial

---

# 12. Prevenció d’incendis

El sistema incorpora:

- detecció de fum
- sensors ambientals
- extinció amb gas FM-200
- extintors CO₂

Aquest sistema permet apagar incendis sense danyar equips electrònics.

---

# 13. Monitorització i gestió

La infraestructura disposa de:

- Graylog
- dashboards
- alertes
- registre d’esdeveniments
- monitorització 24/7

---

# 14. Integració cloud AWS

Part dels serveis han estat desplegats sobre AWS EC2:

- Apache Web Server
- OpenLDAP
- Graylog
- SFTP
- Automatització Ansible

Avantatges:

- escalabilitat
- flexibilitat
- administració remota
- desplegament ràpid

---

# 15. Sostenibilitat

El projecte incorpora mesures d’eficiència energètica:

- il·luminació LED
- climatització eficient
- virtualització
- sensors intel·ligents
- optimització del consum

---

# 16. Conclusions

El CPD d’InnovateTech permet disposar d’una infraestructura moderna, segura i preparada per al creixement futur de l’empresa.

La combinació entre infraestructura física i serveis desplegats sobre AWS proporciona:

- alta disponibilitat
- flexibilitat
- redundància
- millor rendiment
- protecció de dades

La implementació de:

- climatització redundant
- passadissos freds i calents
- monitorització centralitzada
- seguretat física
- automatització amb Ansible

garanteix una administració eficient i professional de tota la infraestructura.

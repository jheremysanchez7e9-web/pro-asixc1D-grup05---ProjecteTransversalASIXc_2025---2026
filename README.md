
#  Projecte Transversal — Grup 05 (ASIXc1D)
###  Institut Tecnològic de Barcelona (ITB) · Curs 2025-2026

---

##  Presentació i Defensa del Projecte

Podeu accedir a tot el material audiovisual, el vídeo demostratiu de 3 minuts i les diapositives de suport per a l'exposició oral a través del següent enllaç unificat:

 **[Enllaç a les Diapositives i Vídeo de la Defensa (Canva)](https://canva.link/hkygq7034cgfa79)**

---

##  Membres del Grup i Rols (RAs)

*  **Jheremy** — *Multimedia Engineer* **Mòdul M0375:** `RA7 (Àudio)` i `RA8 (Vídeo i Jitsi WebRTC)`.  
  *Responsable del servidor Icecast2, l'automatització amb Liquidsoap, Nginx HLS i el servei de videoconferència.*

*  **Liam** — *SecOps & Monitoring Admin* **Mòdul M1665:** `RA4 (Auditoria)` i `RA5 (Seguretat)`.  
  *Responsable de la seguretat perimetral, control del soroll de la xarxa i la pila de logs centralitzada amb Kibana.*

*  **Félix** — *Database Administrator* **Mòdul M0378:** `RA3 (Estructures)` i `RA4 (Optimització)`.  
  *Responsable de l'arquitectura relacional a MariaDB, la consistència de les transaccions distribuïdes i les polítiques de backup.*

---


# pro-asixc1D-grup05 - Projecte Transversal ASIXc 2025_2026

<a name="indice"></a>
# Índice

* [1. Proposta de CPD Sostenible – InnovateTech](#1-proposta-de-cpd-sostenible--innovatetech)
* [1.1 Introducció](#11-introduccio)
* [1.2 Dimensions i escala del CPD](#12-dimensions-i-escala-del-cpd)
* [1.3 Ubicació física del CPD](#13-ubicacio-fisica-del-cpd)
* [1.4 Distribució general del CPD](#14-distribucio-general-del-cpd)
* [1.5 Climatització](#15-climatitzacio)
  * [Temperatures configurades](#temperatures-configurades)
    * [Passadís fred](#passadis-fred)
    * [Passadís calent](#passadis-calent)
  * [Humitat relativa](#humitat-relativa)
* [1.6 Terra tècnic i sostre tècnic](#16-terra-tecnic-i-sostre-tecnic)
  * [Terra tècnic](#terra-tecnic)
  * [Sostre tècnic](#sostre-tecnic)
* [1.7 Sensors ambientals](#17-sensors-ambientals)
  * [Sensors instal·lats](#sensors-instal-lats)
* [1.8 Videovigilància](#18-videovigilancia)
  * [Distribució](#distribucio)
* [2. Infraestructura IT](#2-infraestructura-it)
* [2.1 Objectiu de la infraestructura IT](#21-objectiu-de-la-infraestructura-it)
* [2.2 Rack 1 – Xarxa i comunicacions](#22-rack-1--xarxa-i-comunicacions)
  * [Components del Rack 1](#components-del-rack-1)
  * [Firewall](#firewall)
  * [Característiques](#caracteristiques)
* [2.3 Rack 2 – Servidors](#23-rack-2--servidors)
  * [Servidors implementats](#servidors-implementats)
* [2.4 Models de servidors](#24-models-de-servidors)
  * [Característiques](#caracteristiques)
* [2.5 VLANs definides](#25-vlans-definides)
* [3. Infraestructura elèctrica](#3-infraestructura-electrica)
* [3.1 Objectiu de la infraestructura elèctrica](#31-objectiu-de-la-infraestructura-electrica)
* [3.2 SAIs](#32-sais)
  * [Característiques principals](#caracteristiques-principals)
  * [Distribució dels SAIs](#distribucio-dels-sais)
  * [Consum estimat del CPD](#consum-estimat-del-cpd)
* [4. Seguretat física i lògica](#4-seguretat-fisica-i-logica)
* [4.1 Seguretat física](#41-seguretat-fisica)
  * [Control d’accés](#control-d-acces)
  * [Característiques del control d’accés](#caracteristiques-del-control-d-acces)
  * [Videovigilància](#videovigilancia)
  * [Sistemes antiincendis](#sistemes-antiincendis)
  * [Sistemes implementats](#sistemes-implementats)
* [4.2 Seguretat lògica](#42-seguretat-logica)
  * [Restricció d’accés](#restriccio-d-acces)
  * [Monitorització](#monitoritzacio)
  * [Backups](#backups)
  * [RAIDs](#raids)
  * [Conclusions](#conclusions)
  * [PLA VISUAL DEL CPD (Vista aèria):](#pla-visual-del-cpd-vista-aeria)
    * [2.1 Creació de la infraestructura EC2](#21-creacio-de-la-infraestructura-ec2)
    * [2.2 Replicació de la infraestructura](#22-replicacio-de-la-infraestructura)
    * [3.1 Instal·lació del servidor web Apache](#31-instal-lacio-del-servidor-web-apache)
    * [3.2 Verificació del servei web](#32-verificacio-del-servei-web)
    * [3.3 Configuració del dashboard](#33-configuracio-del-dashboard)
    * [4.1 Instal·lació del servei SFTP](#41-instal-lacio-del-servei-sftp)
    * [4.2 Configuració del servei SFTP](#42-configuracio-del-servei-sftp)
    * [4.3 Verificació de connexió SFTP](#43-verificacio-de-connexio-sftp)
  * [5.1 Instal·lació del servidor LDAP](#51-instal-lacio-del-servidor-ldap)
  * [5.2 Configuració del servei LDAP](#52-configuracio-del-servei-ldap)
  * [5.3 Verificació del servei LDAP](#53-verificacio-del-servei-ldap)
  * [5.4 Verificació dels usuaris LDAP](#54-verificacio-dels-usuaris-ldap)
  * [5.5 Integració del directori LDAP](#55-integracio-del-directori-ldap)
  * [6.1 Instal·lació d'Elasticsearch](#61-instal-lacio-d-elasticsearch)
  * [6.2 Verificació del servei Elasticsearch](#62-verificacio-del-servei-elasticsearch)
  * [6.3 Instal·lació de Kibana](#63-instal-lacio-de-kibana)
  * [6.5 Configuració de Filebeat](#65-configuracio-de-filebeat)
  * [6.6 Verificació de la connexió de Filebeat](#66-verificacio-de-la-connexio-de-filebeat)
  * [6.7 Visualització dels logs centralitzats](#67-visualitzacio-dels-logs-centralitzats)

---

<div align="justify">

<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em><br><br>
<strong>PROJECTE </strong><br><br>
<strong>TRANSVERSAL ASIXc1 </strong><br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em><strong>Pro01 - </strong>Projecte Transversal ASIXc <br><br>
Mòduls i Resultats d’Aprenentatge (RA) implicats <br><br>
</div>

| Pes  | Tasca |  |  |
| --- | --- | --- | --- |
|  |  | 0371 Fonaments de maquinari |  |
| 30  | 1  | RA4 | Implanta maquinari específic de centres de processament de dades (CPD), analitzant-ne les característiques i aplicacions |
|  |  | 0375 Serveis de Xarxes i Internet |  |
| 15  | 2  | RA7 | Administra serveis d'àudio identificant les necessitats de distribució i adaptant els formats |
| 15  | 2  | RA8 | Administra serveis de vídeo identificant les necessitats de distribució i adaptant-ne els formats |
|  |  | 0377 Administració de Bases de Dades |  |
| 20  | 3  | RA3-RA4 | Implanta mètodes de control d’accés utilitzant assistents, eines gràfiques i comandes del llenguatge |
|  |  | 1665 Digitalització aplicada als sectors productius |  |
| 3  | 1, 4  | RA3 | Caracteritza les tecnologies habilitadores digitals necessàries per a l'adequació/transformació de les empreses a entorns digitals descrivint les seves característiques i aplicacions. |
| 4,5  | 1, 3  | RA5 | Avalua la importància de les dades, així com la seva protecció en una economia digital globalitzada, definint sistemes de seguretat i ciberseguretat tant a nivell d'equip/sistema, com a globals. |
| 2,5 | 1, 2,  3, 4  | RA6 | Desenvolupa un projecte de transformació digital d'una empresa d'un sector relacionat amb el títol, tenint en compte els canvis que s'han de produir en funció dels objectius de l'empresa. |
| 10  |  | Presentació 29 de maig |  |

<div align='justify'>

Com es realitza el projecte: <br><br>
● Treball en <strong>grups de 4 alumnes </strong><br><br>
● Cal generar un projecte amb el nom: <br><br>
`pro-grupDeClasse-grupDeTreball `<br><br>
Exemple: `pro-asixc1a-g1 `<br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em><br><br>
Com es lliura la tasca: <br><br>
● Informe detallat amb les respostes i justificacions <br><br>
● Video-demostració pràctic que mostri el funcionament real. <br><br>
● Respectar la <strong>data de lliurament del dia 28 de maig a les 23:59 hores </strong><br><br>
Descripció del projecte: <br><br>
El projecte neix de la necessitat d'<strong>Innovate Tech</strong>, una empresa dedicada a la provisió de serveis tecnològics, de modernitzar la seva capacitat operativa i comunicativa. El creixement de l'activitat de vendes en línia i la demanda de suport tècnic requereixen una base tecnològica sòlida que integri la gestió del personal amb serveis multimèdia avançats. <br><br>
L'objectiu central és dissenyar i implementar un <strong>Centre de Processament de Dades (CPD) </strong>eficient, que actuï com el cor de les operacions de l'empresa, garantint la continuïtat del negoci i la qualitat del servei en un entorn empresarial exigent. <br><br>
Per respondre a aquestes necessitats, la proposta arquitectònica esta orientada al núvol mitjançant <strong>AWS</strong>, prioritzant la <strong>sostenibilitat i la seguretat</strong>. Es planteja una infraestructura que suporti la distribució de continguts d'àudio i vídeo en <em>streaming</em>, així com sistemes de videoconferència per a la formació i comunicació interna. Aquest desplegament s'acompanya de proves d'amplada de banda per assegurar una transmissió fluida i sense degradació, optimitzant l'ús de recursos per minimitzar l'impacte ambiental i calcular la petjada ecològica dels processos. <br><br>
Finalment, el projecte inclou la implementació d'una <strong>base de dades integral </strong>per gestionar l'estructura organitzativa i el registre d'activitat. Aquest sistema incorpora un control d'accés estricte mitjançant rols, automatització de tasques amb <em>scripts </em>i <em>triggers </em>d'auditoria per protegir la informació sensible. <br><br>
Tota la infraestructura es gestiona amb eines de configuració com <strong>Ansible </strong>i es documenta en format Markdown a GitHub, assegurant una solució tecnològica escalable, segura i alineada amb la normativa internacional de protecció de dades. <br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em>Objectius del projecte: <br><br>
● Dissenyar i implantar una infraestructura tecnològica de CPD eficient, segura i sostenible. <br><br>
● Implementar una arquitectura de sistemes i comunicacions que donin suport als requeriments de negoci definits. <br><br>
● Garantir la qualitat del servei de transmissió d'àudio i vídeo amb proves d'amplada de banda realitzades. <br><br>
● Gestionar les dades de l’empresa referents a empleats, clients i serveis. ● Protegir les dades de clients i usuaris segons les normatives internacionals de seguretat. <br><br>
● Optimitzar l'ús de recursos i minimitzar l'impacte ambiental de la infraestructura tecnològica. <br><br>
● Realització de documentació en format markdown publicat al github. Tasca a realitzar <br><br>
<strong>Definició de l'Arquitectura de CPD Sostenible </strong><br><br>
<strong>InnovateTech </strong>necessita un CPD que sigui capaç de gestionar els nostres sistemes d'informació de manera eficient i amb un mínim impacte ambiental. Ens agradaria una arquitectura que integri solucions energèticament eficients. A més, volem que la solució ofereix un alt nivell de seguretat per protegir tant la nostra informació com la de les nostres plataformes de contingut digital. <br><br>
1 Proposta de CPD <br><br>
Cal proposar una solució de CPD que contempli -com a mínim- els següents requeriments: <br><br>
● Ubicació física <br><br>
○ Situació física de la sala a l’edifici. <br><br>
○ Sistemes de climatització (aire condicionat). Nivells de temperatura, humitat i neteja de l’aire. <br><br>
○ Mesures per dificultar la identificació de la sala. <br><br>
○ Distribució i gestió del cablejat. <br><br>
○ Terra tècnic i sostre tècnic. <br><br>
○ Planells, dibuixos, diagrames dels elements anteriorment citats. <br><br>
○ Estructuració dels racks (mínim 2 racks). <br><br>
● Infraestructura IT: <br><br>
○ Servidors: Número i tipus de model. <br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em><br><br>
○ Patch panels. <br><br>
○ Switches. <br><br>
○ Planells i diagrames de com estan distribuïts els racks amb els servidors, patch panels i switches. <br><br>
● Infraestructura elèctrica: <br><br>
○ Sistemes d’alimentació redundant. <br><br>
○ SAIS. Càlcul de quantes bateries o components per tenir els servidors operatius sense corrent elèctric i temps que voleu de funcionament sense senyal elèctric en els servidors. <br><br>
● Seguretat física i lògica: <br><br>
○ Física: <br><br>
■ Elements de control d’accés a incorporar en el CPD. <br><br>
■ Videovigilància. <br><br>
■ Sistemes prevenció, detecció i d’extinció d’incendis. <br><br>
■ Vies d’evacuació. <br><br>
■ Diagrames, planells i fotografies de tota la seguretat física <br><br>
incorporada. <br><br>
○ Lògica: <br><br>
■ Restricció d’accés per autorització. <br><br>
■ Firewalls. <br><br>
■ Monitorizació. <br><br>
■ Còpies de seguretat/Backups. <br><br>
■ RAIDs. <br><br>
○ Prevenció de riscos laborals: <br><br>
■ Mesures aplicades en matèria de prevenció de RRLL en el CPD <br><br>
● Implementació del CPD al núvol AWS amb els serveis utilitzats (mínim de 4 - el serveis d'àudio, vídeo i bases de dades es valoren en els altres blocs). ○ Els serveis a muntar (no es poden utilitzar AMI’s del marketplace amb software instal.lat) són: <br><br>
■ Servei web <br><br>
■ Servei de transferència de fitxers segur (sftp). S’autenticarà amb els usuaris de directori actiu. <br><br>
■ Servei de centralització de logs que reculli els logs de tots els equips. ■ Servei de directori actiu per a guardar els usuaris. <br><br>
○ Cada servei haurà d’estar instal·lat en un servidor diferent (a excepció del servei web i sftp). <br><br>
○ Dues de les màquines (com a mínim) han d’estar configurades amb Ansible (incloent tota la configuració feta al servidor). <br><br>
○ Les màquines s'han d’administrar amb un usuari específic (no es podrà utilitzar l’usuari per defecte del servidor) i l’accés es farà amb clau <br><br>
pública/privada (sense utilitzar contrasenya).<br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em><br><br>
</div>

<a name="1-proposta-de-cpd-sostenible--innovatetech"></a>
# <a href="#1-proposta-de-cpd-sostenible--innovatetech">1. Proposta de CPD Sostenible – InnovateTech</a>
[↑ Volver al índice](#indice)



<a name="11-introduccio"></a>
# <a href="#11-introduccio">1.1 Introducció</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Per aquest projecte hem dissenyat un CPD (Centre de Processament de Dades) pensat per a l’empresa fictícia InnovateTech, una empresa orientada a serveis digitals, allotjament web, videoconferència i gestió centralitzada de dades.`<br><br>
`L’objectiu principal del CPD és garantir:`<br><br>
* alta disponibilitat dels serveis
* seguretat física i lògica
* escalabilitat
* eficiència energètica
* monitorització centralitzada
* tolerància a fallades

`A més, s’ha buscat que el disseny sigui realista i aplicable a una infraestructura empresarial moderna, combinant una part física (CPD propi) amb una infraestructura híbrida al núvol mitjançant AWS.`<br><br>
`Per al disseny s’han tingut en compte aspectes de:`<br><br>
* refrigeració
* distribució de cablejat
* seguretat
* redundància elèctrica
* monitorització ambiental
* videovigilància
* segmentació dels serveis

</div>

<a name="12-dimensions-i-escala-del-cpd"></a>
# <a href="#12-dimensions-i-escala-del-cpd">1.2 Dimensions i escala del CPD</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El CPD s’ha dissenyat amb unes dimensions totals aproximades de:`<br><br>
* 8 metres d’amplada
* 6 metres de profunditat

`Superfície total:`<br><br>
* 48 m²

`L’escala utilitzada al plànol és aproximadament:`<br><br>
* 1:50

`L’espai està dividit en:`<br><br>
* zona de racks
* passadís fred
* passadís calent
* control d’accés
* sistemes elèctrics
* climatització
* sistemes de seguretat

</div>

<a name="13-ubicacio-fisica-del-cpd"></a>
# <a href="#13-ubicacio-fisica-del-cpd">1.3 Ubicació física del CPD</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El CPD estaria situat:`<br><br>
* a una planta interior de l’edifici
* sense accés directe des de l’exterior
* allunyat de finestres
* zones humides
* ascensors
* canonades principals d’aigua

`La sala s’ubicaria en una zona restringida només accessible per personal autoritzat.`<br><br>
`També s’han aplicat mesures per dificultar la identificació del CPD:`<br><br>
* absència de cartells visibles
* porta ignífuga sense etiquetatge
* accés mitjançant RFID + PIN
* càmeres de seguretat
* monitorització 24/7

</div>

<a name="14-distribucio-general-del-cpd"></a>
# <a href="#14-distribucio-general-del-cpd">1.4 Distribució general del CPD</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El CPD està estructurat principalment en:`<br><br>
* 2 racks principals
* climatització redundant
* terra tècnic
* sensors ambientals
* control d’accés
* videovigilància
* SAI
* quadre elèctric independent

</div>

<a name="15-climatitzacio"></a>
# <a href="#15-climatitzacio">1.5 Climatització</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El CPD incorpora:`<br><br>
* 2 sistemes de climatització redundants:
* AC1
* AC2

`Tipus:`<br><br>
* aire condicionat de precisió

`Model orientatiu:`<br><br>
* Daikin InRow o equivalent professional

</div>

<a name="temperatures-configurades"></a>
## <a href="#temperatures-configurades">Temperatures configurades</a>
[↑ Volver al índice](#indice)



<a name="passadis-fred"></a>
### <a href="#passadis-fred">Passadís fred</a>
[↑ Volver al índice](#indice)

<div align='justify'>

* 20 ºC aproximadament

</div>

<a name="passadis-calent"></a>
### <a href="#passadis-calent">Passadís calent</a>
[↑ Volver al índice](#indice)

<div align='justify'>

* 30 ºC aproximadament

</div>

<a name="humitat-relativa"></a>
## <a href="#humitat-relativa">Humitat relativa</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Es manté entre:`<br><br>
* 45% i 55%

</div>

<a name="16-terra-tecnic-i-sostre-tecnic"></a>
# <a href="#16-terra-tecnic-i-sostre-tecnic">1.6 Terra tècnic i sostre tècnic</a>
[↑ Volver al índice](#indice)



<a name="terra-tecnic"></a>
## <a href="#terra-tecnic">Terra tècnic</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Alçada:`<br><br>
* 40 cm

`Permet passar:`<br><br>
* cablejat elèctric
* fibra òptica
* xarxa CAT6A
* sensors
* climatització

</div>

<a name="sostre-tecnic"></a>
## <a href="#sostre-tecnic">Sostre tècnic</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El sostre incorpora:`<br><br>
* cablejat secundari
* sistemes de seguretat
* càmeres
* sensors
* ventilació

</div>

<a name="17-sensors-ambientals"></a>
# <a href="#17-sensors-ambientals">1.7 Sensors ambientals</a>
[↑ Volver al índice](#indice)



<a name="sensors-instal-lats"></a>
## <a href="#sensors-instal-lats">Sensors instal·lats</a>
[↑ Volver al índice](#indice)



| SENSOR | QUANTITAT |
| --- | --- |
| Temperatura | 6 |
| Humitat | 6 |
| Fum | 4 |
| Fuita d’aigua | 4 |
| Pressió diferencial | 4 |



<a name="18-videovigilancia"></a>
# <a href="#18-videovigilancia">1.8 Videovigilància</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El CPD incorpora:`<br><br>
* 7 càmeres IP

</div>

<a name="distribucio"></a>
## <a href="#distribucio">Distribució</a>
[↑ Volver al índice](#indice)



| CÀMERA | UBICACIÓ |
| --- | --- |
| Càmera 1 | Entrada principal |
| Càmera 2 | Passadís dret |
| Càmera 3 | Passadís esquerre |
| Càmera 4 | Rack superior esquerra |
| Càmera 5 | Zona central |
| Càmera 6 | Rack superior dreta |
| Càmera 7 | Zona inferior dreta |



<a name="2-infraestructura-it"></a>
# <a href="#2-infraestructura-it">2. Infraestructura IT</a>
[↑ Volver al índice](#indice)



<a name="21-objectiu-de-la-infraestructura-it"></a>
# <a href="#21-objectiu-de-la-infraestructura-it">2.1 Objectiu de la infraestructura IT</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`La infraestructura IT del CPD d’InnovateTech s’ha dissenyat amb l’objectiu de garantir:`<br><br>
* alta disponibilitat
* redundància
* seguretat
* escalabilitat
* facilitat d’administració

`S’ha separat la infraestructura en dos racks principals:`<br><br>
* un rack dedicat a comunicacions i xarxa
* un rack dedicat als servidors

</div>

<a name="22-rack-1--xarxa-i-comunicacions"></a>
# <a href="#22-rack-1--xarxa-i-comunicacions">2.2 Rack 1 – Xarxa i comunicacions</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Aquest rack està destinat als sistemes de comunicació, connectivitat i seguretat de xarxa.`<br><br>
</div>

<a name="components-del-rack-1"></a>
## <a href="#components-del-rack-1">Components del Rack 1</a>
[↑ Volver al índice](#indice)



| EQUIP | MODEL PROPOSAT | QUANTITAT |
| --- | --- | --- |
| Firewall | Fortigate 60F | 1 |
| Router ISP | Cisco ISR 1100 | 1 |
| Switch Core | Cisco Catalyst 9200 | 2 |
| Patch Panels CAT6A | 24 ports | 4 |
| NAS Backups | Synology DS1821+ | 1 |
| SAI secundari | APC SmartUPS 3000VA | 1 |



<a name="firewall"></a>
## <a href="#firewall">Firewall</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Per protegir la xarxa s’ha seleccionat un:`<br><br>
* Fortigate 60F

`Aquest firewall permet:`<br><br>
* filtratge de trànsit
* VPN
* inspecció profunda de paquets
* segmentació VLAN
* control d’accessos
* monitorització del trànsit

</div>

<a name="caracteristiques"></a>
## <a href="#caracteristiques">Característiques</a>
[↑ Volver al índice](#indice)



| COMPONENT | CARACTERÍSTICA |
| --- | --- |
| Throughput Firewall | 10 Gbps |
| Ports | 10 x GE RJ45 |
| VPN IPSec | Sí |
| IDS/IPS | Sí |
| Consum | ~18W |

<div align='justify'>

`Preu aproximat:`<br><br>
* 850€

</div>

<a name="23-rack-2--servidors"></a>
# <a href="#23-rack-2--servidors">2.3 Rack 2 – Servidors</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Aquest rack està dedicat als servidors principals de la infraestructura.`<br><br>
</div>

<a name="servidors-implementats"></a>
## <a href="#servidors-implementats">Servidors implementats</a>
[↑ Volver al índice](#indice)



| SERVIDOR | FUNCIÓ |
| --- | --- |
| Servidor Web | Dashboard PHP i aplicació web |
| Servidor SFTP | Transferència segura d’arxius |
| Servidor Logs | Elasticsearch + Kibana |
| Controlador LDAP | Gestió centralitzada d’usuaris |
| Servidor Monitorització | Filebeat i monitorització |
| Servidor Backup | Còpies de seguretat |



<a name="24-models-de-servidors"></a>
# <a href="#24-models-de-servidors">2.4 Models de servidors</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`S’ha proposat utilitzar:`<br><br>
* Dell PowerEdge R740
* format rack 2U
* doble font redundant

</div>

<a name="caracteristiques"></a>
## <a href="#caracteristiques">Característiques</a>
[↑ Volver al índice](#indice)



| COMPONENT | CARACTERÍSTICA |
| --- | --- |
| CPU | Intel Xeon Silver |
| RAM | 64 GB ECC |
| Emmagatzematge | SSD NVMe RAID 1 |
| Xarxa | 2x10GbE |
| Alimentació | Dual PSU redundant |



<a name="25-vlans-definides"></a>
# <a href="#25-vlans-definides">2.5 VLANs definides</a>
[↑ Volver al índice](#indice)



| VLAN | FUNCIÓ |
| --- | --- |
| VLAN 10 | Administració |
| VLAN 20 | Servidors |
| VLAN 30 | Monitorització |
| VLAN 40 | Videovigilància |
| VLAN 50 | Gestió interna |



<a name="3-infraestructura-electrica"></a>
# <a href="#3-infraestructura-electrica">3. Infraestructura elèctrica</a>
[↑ Volver al índice](#indice)



<a name="31-objectiu-de-la-infraestructura-electrica"></a>
# <a href="#31-objectiu-de-la-infraestructura-electrica">3.1 Objectiu de la infraestructura elèctrica</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`La infraestructura elèctrica del CPD s’ha dissenyat amb l’objectiu de garantir la continuïtat dels serveis encara que es produeixi una fallada elèctrica.`<br><br>
`Per aquest motiu s’han incorporat:`<br><br>
* SAIs redundants
* doble línia d’alimentació
* protecció elèctrica
* monitorització energètica

</div>

<a name="32-sais"></a>
# <a href="#32-sais">3.2 SAIs</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Per protegir la infraestructura s’han instal·lat:`<br><br>
* dos SAIs principals

`Model proposat:`<br><br>
* APC SmartUPS 3000VA

</div>

<a name="caracteristiques-principals"></a>
## <a href="#caracteristiques-principals">Característiques principals</a>
[↑ Volver al índice](#indice)



| COMPONENT | CARACTERÍSTICA |
| --- | --- |
| Model | APC SmartUPS 3000VA |
| Potència | 3000VA |
| Autonomia | 25-35 minuts |
| Tipus | Online |
| Monitorització | Sí |
| Bateries reemplaçables | Sí |



<a name="distribucio-dels-sais"></a>
## <a href="#distribucio-dels-sais">Distribució dels SAIs</a>
[↑ Volver al índice](#indice)



| SAI | FUNCIÓ |
| --- | --- |
| SAI Principal | Alimentació servidors |
| SAI Secundari | Xarxa i comunicacions |



<a name="consum-estimat-del-cpd"></a>
## <a href="#consum-estimat-del-cpd">Consum estimat del CPD</a>
[↑ Volver al índice](#indice)



| EQUIP | CONSUM APROXIMAT |
| --- | --- |
| Servidors | 2500W |
| Switches | 300W |
| Firewall i router | 100W |
| Climatització | 2500W |
| NAS backups | 150W |
| Càmeres i sensors | 120W |

<div align='justify'>

`Consum total aproximat:`<br><br>
* entre 5000W i 6000W

</div>

<a name="4-seguretat-fisica-i-logica"></a>
# <a href="#4-seguretat-fisica-i-logica">4. Seguretat física i lògica</a>
[↑ Volver al índice](#indice)



<a name="41-seguretat-fisica"></a>
# <a href="#41-seguretat-fisica">4.1 Seguretat física</a>
[↑ Volver al índice](#indice)



<a name="control-d-acces"></a>
## <a href="#control-d-acces">Control d’accés</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`L’accés al CPD està restringit únicament a:`<br><br>
* personal autoritzat

`Per entrar a la sala és necessari:`<br><br>
* targeta RFID
* PIN numèric

</div>

<a name="caracteristiques-del-control-d-acces"></a>
## <a href="#caracteristiques-del-control-d-acces">Característiques del control d’accés</a>
[↑ Volver al índice](#indice)



| COMPONENT | CARACTERÍSTICA |
| --- | --- |
| Accés | RFID + PIN |
| Registre d’accessos | Sí |
| Control horari | Sí |
| Restricció per rols | Sí |



<a name="videovigilancia"></a>
## <a href="#videovigilancia">Videovigilància</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El CPD incorpora:`<br><br>
* 7 càmeres IP distribuïdes per tota la sala

`Aquestes càmeres permeten:`<br><br>
* monitorització 24/7
* gravació contínua
* revisió d’incidències

</div>

<a name="sistemes-antiincendis"></a>
## <a href="#sistemes-antiincendis">Sistemes antiincendis</a>
[↑ Volver al índice](#indice)



<a name="sistemes-implementats"></a>
## <a href="#sistemes-implementats">Sistemes implementats</a>
[↑ Volver al índice](#indice)



| SISTEMA | FUNCIÓ |
| --- | --- |
| Sensors de fum | Detecció d’incendis |
| Sensors temperatura | Sobreescalfament |
| Sensors d’aigua | Fuites |
| FM-200 | Extinció automàtica |
| Extintors CO₂ | Extinció manual |



<a name="42-seguretat-logica"></a>
# <a href="#42-seguretat-logica">4.2 Seguretat lògica</a>
[↑ Volver al índice](#indice)



<a name="restriccio-d-acces"></a>
## <a href="#restriccio-d-acces">Restricció d’accés</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Els servidors utilitzen:`<br><br>
* autenticació per claus SSH
* usuaris específics
* restriccions de permisos

`No s’utilitza:`<br><br>
* l’usuari root directament

</div>

<a name="monitoritzacio"></a>
## <a href="#monitoritzacio">Monitorització</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`S’ha implementat:`<br><br>
* Elasticsearch
* Kibana
* Filebeat

`Aquest sistema permet:`<br><br>
* centralitzar logs
* detectar errors
* monitoritzar tots els servidors

</div>

<a name="backups"></a>
## <a href="#backups">Backups</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Les còpies de seguretat es realitzen:`<br><br>
* automàticament
* cada dia
* al NAS central

</div>

<a name="raids"></a>
## <a href="#raids">RAIDs</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Els servidors utilitzen:`<br><br>
* RAID 1

`Avantatges:`<br><br>
* redundància
* tolerància a fallades
* protecció de dades

</div>

<a name="conclusions"></a>
## <a href="#conclusions">Conclusions</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Les mesures implementades permeten:`<br><br>
* protegir físicament el CPD
* limitar accessos
* monitoritzar incidències
* garantir la seguretat dels serveis

`La combinació de:`<br><br>
* seguretat física
* seguretat lògica
* backups
* monitorització

`fa que la infraestructura sigui molt més robusta davant possibles incidències.`<br><br>
</div>

<a name="pla-visual-del-cpd-vista-aeria"></a>
## <a href="#pla-visual-del-cpd-vista-aeria">PLA VISUAL DEL CPD (Vista aèria):</a>
[↑ Volver al índice](#indice)



<p align="center">
  <img src="images/img_1.png" alt="Imagen 1" />
</p>



<a name="21-creacio-de-la-infraestructura-ec2"></a>
### <a href="#21-creacio-de-la-infraestructura-ec2">2.1 Creació de la infraestructura EC2</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Es creen diferents instàncies Ubuntu Server 24.04 sobre AWS EC2 per separar els serveis principals del CPD i millorar la seguretat i l’organització de la infraestructura.`<br><br>
`Característiques generals:`<br><br>
* Ubuntu Server 24.04 LTS
* Disc SSD EBS
* Accés SSH amb clau RSA
* Security Groups personalitzats
* Xarxa privada interna AWS

`Cada màquina s’ha destinat a un servei diferent:`<br><br>
* servidor web
* servidor SFTP
* servidor LDAP
* servidor de logs
* servidor de monitorització

`També s’han configurat IPs privades per permetre la comunicació interna entre serveis.`<br><br>
</div>

<p align="center">
  <img src="images/img_2.png" alt="Imagen 2" />
</p>



<p align="center">
  <img src="images/img_3.png" alt="Imagen 3" />
</p>



<p align="center">
  <img src="images/img_4.png" alt="Imagen 4" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Verificació visual de la infraestructura desplegada sobre AWS amb separació de serveis.`<br><br>
</div>

<a name="22-replicacio-de-la-infraestructura"></a>
### <a href="#22-replicacio-de-la-infraestructura">2.2 Replicació de la infraestructura</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Després de validar el funcionament de la primera instància, es repeteix el mateix procés de configuració quatre vegades més per desplegar la resta de servidors necessaris del projecte.`<br><br>
`A cada màquina:`<br><br>
* es configura un usuari administrador
* s’activa accés SSH segur
* es configuren els ports necessaris
* s’instal·la el servei corresponent

`Aquesta separació permet:`<br><br>
* major seguretat
* millor manteniment
* escalabilitat
* aïllament de serveis crítics

</div>

<p align="center">
  <img src="images/img_5.png" alt="Imagen 5" />
</p>



<p align="center">
  <img src="images/img_6.png" alt="Imagen 6" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Comprovació visual de la implementació de múltiples servidors independents dins la infraestructura AWS.`<br><br>
</div>

<a name="31-instal-lacio-del-servidor-web-apache"></a>
### <a href="#31-instal-lacio-del-servidor-web-apache">3.1 Instal·lació del servidor web Apache</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`S’instal·la Apache2 al servidor web per allotjar el dashboard principal del projecte InnovateTech.`<br><br>
`Comandes utilitzades:`<br><br>
`sudo apt update`<br><br>
`sudo apt install apache2 -y`<br><br>
`sudo systemctl enable apache2`<br><br>
`sudo systemctl start apache2`<br><br>
`Posteriorment es comprova el correcte funcionament del servei.`<br><br>
<strong>
</strong><br><br>
</div>

<p align="center">
  <img src="images/img_7.png" alt="Imagen 7" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Verificació visual del correcte funcionament del servidor web Apache.`<br><br>
</div>

<a name="32-verificacio-del-servei-web"></a>
### <a href="#32-verificacio-del-servei-web">3.2 Verificació del servei web</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Una vegada instal·lat Apache, es comprova l’accés web des del navegador utilitzant la IP pública del servidor AWS.`<br><br>
`URL utilitzada:`<br><br>
`http://34.204.242.186/dashboard.php`<br><br>
`El dashboard permet:`<br><br>
* visualitzar serveis
* consultar dades
* descarregar CSV
* accedir als diferents sistemes

</div>

<p align="center">
  <img src="images/img_8.png" alt="Imagen 8" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Comprovació visual del correcte desplegament del servei web sobre AWS.`<br><br>
</div>

<a name="33-configuracio-del-dashboard"></a>
### <a href="#33-configuracio-del-dashboard">3.3 Configuració del dashboard</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Es configura el fitxer principal del dashboard dins:`<br><br>
`/var/www/html/dashboard.php`<br><br>
`Aquest dashboard centralitza:`<br><br>
* informació dels serveis
* connexió amb base de dades
* monitorització
* accessos principals

`També es personalitza la interfície per adaptar-la al projecte InnovateTech.`<br><br>
</div>

<p align="center">
  <img src="images/img_9.png" alt="Imagen 9" />
</p>



<p align="center">
  <img src="images/img_10.png" alt="Imagen 10" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Verificació visual de la configuració i personalització del dashboard principal.`<br><br>
</div>

<a name="41-instal-lacio-del-servei-sftp"></a>
### <a href="#41-instal-lacio-del-servei-sftp">4.1 Instal·lació del servei SFTP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Per permetre la transferència segura d’arxius s’instal·la el servei OpenSSH Server al servidor web.`<br><br>
`Comandes utilitzades:`<br><br>
`sudo apt update`<br><br>
`sudo apt install openssh-server -y`<br><br>
`sudo systemctl enable ssh`<br><br>
`sudo systemctl start ssh`<br><br>
`Posteriorment es comprova el correcte funcionament del servei SSH.`<br><br>
</div>

<p align="center">
  <img src="images/img_11.png" alt="Imagen 11" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Verificació visual del correcte funcionament del servei SSH/SFTP.`<br><br>
</div>

<a name="42-configuracio-del-servei-sftp"></a>
### <a href="#42-configuracio-del-servei-sftp">4.2 Configuració del servei SFTP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Es configura OpenSSH per permetre connexions SFTP segures mitjançant autenticació SSH.`<br><br>
`També es configuren:`<br><br>
* permisos d’accés
* directoris d’usuari
* autenticació segura

`Fitxer modificat:`<br><br>
`/etc/ssh/sshd_config`<br><br>
`Es reinicia el servei després de la configuració:`<br><br>
`sudo systemctl restart ssh`<br><br>
</div>

<p align="center">
  <img src="images/img_12.png" alt="Imagen 12" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Comprovació visual de la configuració segura del servei SFTP.`<br><br>
</div>

<a name="43-verificacio-de-connexio-sftp"></a>
### <a href="#43-verificacio-de-connexio-sftp">4.3 Verificació de connexió SFTP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Es comprova la connexió SFTP des d’un client remot utilitzant autenticació SSH.`<br><br>
`Comanda utilitzada:`<br><br>
`sftp adminit@IP_SERVIDOR`<br><br>
`La connexió es realitza correctament i permet:`<br><br>
* pujada d’arxius
* descàrrega
* navegació segura

</div>

<p align="center">
  <img src="images/img_13.png" alt="Imagen 13" />
</p>

<div align="justify">
<strong>`Justificació:
`</strong>`Verificació visual del correcte funcionament del servei SFTP remot.`<br><br>
</div>

<a name="51-instal-lacio-del-servidor-ldap"></a>
## <a href="#51-instal-lacio-del-servidor-ldap">5.1 Instal·lació del servidor LDAP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Per centralitzar la gestió d’usuaris del CPD s’instal·la OpenLDAP sobre Ubuntu Server. Aquest servei permet gestionar els usuaris des d’un únic punt i facilitar la seva integració amb la resta de serveis de la infraestructura.`<br><br>
</div>

<p align="center">
  <img src="images/img_14.png" alt="Imagen 14" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Confirmació visual de la correcta instal·lació dels paquets OpenLDAP i ldap-utils al servidor LDAP.`<br><br>
</div>

<a name="52-configuracio-del-servei-ldap"></a>
## <a href="#52-configuracio-del-servei-ldap">5.2 Configuració del servei LDAP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Una vegada instal·lat el servei es configura el domini LDAP, la contrasenya d’administració i els paràmetres necessaris per al funcionament del directori centralitzat.`<br><br>
</div>

<p align="center">
  <img src="images/img_15.png" alt="Imagen 15" />
</p>



<p align="center">
  <img src="images/img_16.png" alt="Imagen 16" />
</p>



<p align="center">
  <img src="images/img_17.png" alt="Imagen 17" />
</p>



<p align="center">
  <img src="images/img_18.png" alt="Imagen 18" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Verificació visual de la configuració inicial del directori LDAP.`<br><br>
</div>

<a name="53-verificacio-del-servei-ldap"></a>
## <a href="#53-verificacio-del-servei-ldap">5.3 Verificació del servei LDAP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Després de la configuració es comprova que el servei slapd es troba actiu i funcionant correctament dins del servidor.`<br><br>
</div>

<p align="center">
  <img src="images/img_19.png" alt="Imagen 19" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Confirmació visual del correcte funcionament del servei LDAP.`<br><br>
</div>

<a name="54-verificacio-dels-usuaris-ldap"></a>
## <a href="#54-verificacio-dels-usuaris-ldap">5.4 Verificació dels usuaris LDAP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Es comprova que els usuaris i objectes del directori es troben registrats correctament dins de la base de dades LDAP.`<br><br>
</div>

<p align="center">
  <img src="images/img_20.png" alt="Imagen 20" />
</p>



<p align="center">
  <img src="images/img_21.png" alt="Imagen 21" />
</p>



<p align="center">
  <img src="images/img_22.png" alt="Imagen 22" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Verificació visual dels usuaris emmagatzemats al directori LDAP.`<br><br>
</div>

<a name="55-integracio-del-directori-ldap"></a>
## <a href="#55-integracio-del-directori-ldap">5.5 Integració del directori LDAP</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`El servidor LDAP s’utilitza com a sistema centralitzat d’autenticació per facilitar la gestió d’usuaris entre els diferents serveis implementats dins del projecte.`<br><br>
</div>

<p align="center">
  <img src="images/img_23.png" alt="Imagen 23" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Confirmació visual del funcionament del directori LDAP com a sistema centralitzat d’autenticació.`<br><br>
</div>

<a name="61-instal-lacio-d-elasticsearch"></a>
## <a href="#61-instal-lacio-d-elasticsearch">6.1 Instal·lació d'Elasticsearch</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Per centralitzar els logs de tota la infraestructura s’instal·la Elasticsearch al servidor de monitorització. Aquest servei és l’encarregat d'emmagatzemar, indexar i gestionar tota la informació rebuda dels diferents equips.`<br><br>
</div>

<p align="center">
  <img src="images/img_24.png" alt="Imagen 24" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Confirmació visual de la correcta instal·lació del servei Elasticsearch.`<br><br>
</div>

<a name="62-verificacio-del-servei-elasticsearch"></a>
## <a href="#62-verificacio-del-servei-elasticsearch">6.2 Verificació del servei Elasticsearch</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Després de la instal·lació es comprova que Elasticsearch es troba actiu i funcionant correctament.`<br><br>
</div>

<p align="center">
  <img src="images/img_25.png" alt="Imagen 25" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Verificació visual del correcte funcionament del servei Elasticsearch.`<br><br>
</div>

<a name="63-instal-lacio-de-kibana"></a>
## <a href="#63-instal-lacio-de-kibana">6.3 Instal·lació de Kibana</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`S’instal·la Kibana per permetre la visualització dels logs emmagatzemats a Elasticsearch mitjançant una interfície web intuïtiva.`<br><br>
</div>

<p align="center">
  <img src="images/img_26.png" alt="Imagen 26" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Confirmació visual de la correcta instal·lació de Kibana.`<br><br>
</div>

<a name="65-configuracio-de-filebeat"></a>
## <a href="#65-configuracio-de-filebeat">6.5 Configuració de Filebeat</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Per centralitzar els logs dels servidors es configura Filebeat perquè reculli els registres del sistema i els enviï automàticament a Elasticsearch.`<br><br>
</div>

<p align="center">
  <img src="images/img_27.png" alt="Imagen 27" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Confirmació visual de la configuració del servei Filebeat.`<br><br>
</div>

<a name="66-verificacio-de-la-connexio-de-filebeat"></a>
## <a href="#66-verificacio-de-la-connexio-de-filebeat">6.6 Verificació de la connexió de Filebeat</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Una vegada configurat el servei es comprova que Filebeat pot comunicar-se correctament amb Elasticsearch.`<br><br>
</div>

<p align="center">
  <img src="images/img_28.png" alt="Imagen 28" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Verificació visual de la comunicació entre Filebeat i Elasticsearch.`<br><br>
</div>

<a name="67-visualitzacio-dels-logs-centralitzats"></a>
## <a href="#67-visualitzacio-dels-logs-centralitzats">6.7 Visualització dels logs centralitzats</a>
[↑ Volver al índice](#indice)

<div align='justify'>

`Finalment es comprova que els logs dels diferents servidors arriben correctament a Elasticsearch i poden ser visualitzats des de Kibana.`<br><br>
`Aquesta comprovació i la de Kibana funcionant estaven a punt de ser fetes pero per algun motiu els serveis es van caure quan menys ens ho esperavem.`<br><br>
`La Laura Villalva va poder veure el sistema de logs que es va configurar a classe.`<br><br>
</div>

<p align="center">
  <img src="images/img_29.png" alt="Imagen 29" />
</p>



<p align="center">
  <img src="images/img_30.png" alt="Imagen 30" />
</p>

<div align="justify">
<strong>`Justificació:`</strong>` Confirmació visual de la recepció i visualització dels logs centralitzats de la infraestructura.`<br><br>
2 Implantació dels serveis d'àudio i vídeo <br><br>
`2.1 Descripció general `<br><br>
<strong>InnovateTech </strong>requereix la implantació d’una infraestructura de serveis multimèdia dins del seu Centre de Processament de Dades (CPD), amb l’objectiu de donar suport a la comunicació interna, la formació corporativa i la distribució de continguts als clients. <br><br>
Aquesta infraestructura haurà de permetre: <br><br>
● La distribució de continguts d’àudio en streaming. <br><br>
● La distribució de continguts de vídeo en streaming. <br><br>
● La realització de videoconferències. <br><br>
● L’accés als serveis tant des de clients locals com mitjançant navegadors web. <br><br>
● La integració amb el sistema de comunicació interna definit a l’apartat corresponent del projecte. <br><br>
Els serveis s’hauran d’implantar utilitzant tecnologies estàndard i configuracions realistes d’entorn empresarial. <br><br>
`2.2 Implantació del servei d’àudio `<br><br>
`2.2.1 Objectius `<br><br>
Implementar un sistema de distribució d’àudio que permeti streaming en directe i sota demanda. 
<br><br>
`2.2.2 Requeriments `<br><br>
L’alumne haurà de: <br><br>
<strong>● </strong>Descriure la funcionalitat del servei d’àudio. <br><br>
<strong>● </strong>Instal·lar i configurar un servidor de streaming d’àudio. <br><br>
<strong>● </strong>Utilitzar formats d’àudio digital com MP3, AAC o OGG. <br><br>
<strong>● </strong>Configurar clients d’accés. <br><br>
<strong>● </strong>Permetre l’accés via navegador web. <br><br>
<strong>● </strong>Documentar la instal·lació, configuració i proves del servei. 
<br><br>
`2.2.3 Requisits mínims obligatoris `<br><br>
Per poder ser avaluat, el servei haurà de complir com a mínim: <br><br>
● Servidor d’àudio instal·lat i operatiu. 

<br><br>
● Almenys <strong>1 canal d’àudio funciona</strong>l. <br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em><br><br>
● Reproducció correcta des d’un client. <br><br>
● Accés funcional via navegador. <br><br>
● Ús d’almenys <strong>1 format d’àudio digital. </strong><br><br>
● Evidència de funcionament mitjançant captures o prova demostrable. <br><br>
`2.2.4 Validació `<br><br>
● Reproducció d’àudio en temps real. <br><br>
● Accés des de múltiples clients. <br><br>
● Funcionament estable del servei. <br><br>
`2.3 Implant``a``ció del servei de vídeo `<br><br>
`2.3.1 Objectius `<br><br>
Desplegar un sistema de distribució de vídeo en streaming i videoconferència. <br><br>
`2.3.2 Requeriments `<br><br>
L’alumne haurà de: <br><br>
● Descriure la funcionalitat del servei de vídeo. <br><br>
● Instal·lar i configurar un servidor de vídeo (ex: NGINX, Jellyfin o equivalent). <br><br>
● Configurar streaming (RTMP, HLS o similar). <br><br>
● Utilitzar formats i còdecs de vídeo: <br><br>
○ H.264 <br><br>
○ MP4 <br><br>
● Permetre accés des de navegador i clients. <br><br>
● Descriure protocols de videoconferència: <br><br>
○ WebRTC <br><br>
● Instal·lar i configurar una eina de videoconferència (ex: Jitsi Meet). ● Realitzar proves de connexió entre usuaris. <br><br>
`2.3.3 Requisits mínims obligatoris `<br><br>
Per poder ser avaluat, el servei haurà de complir com a mínim: <br><br>
● Servidor de vídeo instal·lat i operatiu. <br><br>
● Almenys <strong>1 vídeo accessible en streaming. </strong><br><br>
● Reproducció funcional des d’un navegador. <br><br>
● Ús d’almenys <strong>1 format de vídeo digita</strong>l. <br><br>
● Servei de videoconferència operatiu. <br><br>
● Realització d’almenys <strong>1 videotrucada funcional</strong>. <br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em>● Evidències documentades. <br><br>
`2.3.4 Validació `<br><br>
● Reproducció correcta de vídeo. <br><br>
● Accés remot funcional. <br><br>
● Funcionament correcte de videoconferència. <br><br>
`2.4 Comprovacions d’amplada de banda `<br><br>
`2.4.1 Objectiu `<br><br>
Garantir que la infraestructura desplegada és capaç de suportar els serveis d’àudio, vídeo i videoconferència sense degradació del servei. <br><br>
`2.4.2 Requeriments `<br><br>
L’alumne haurà de: <br><br>
● Realitzar proves de rendiment de xarxa. <br><br>
● Mesurar: <br><br>
○ Velocitat de baixada <br><br>
○ Velocitat de pujada <br><br>
○ Latència <br><br>
● Analitzar el comportament amb múltiples serveis actius. <br><br>
● Relacionar els resultats amb el consum dels serveis multimèdia. <br><br>
● Determinar si la infraestructura és suficient. <br><br>
● Proposar millores si escau. <br><br>
`2.4.3 Requisits mínims obligatoris `<br><br>
Per poder ser avaluat, caldrà: <br><br>
● Realitzar almenys <strong>2 proves d’amplada de banda. </strong><br><br>
● Mostrar: <br><br>
○ Download <br><br>
○ Upload <br><br>
○ Latència <br><br>
● Relacionar els resultats amb: <br><br>
○ Streaming d’àudio <br><br>
○ Streaming de vídeo <br><br>
○ Videoconferència <br><br>
● Classificar el sistema com: <br><br>
<strong>○ Acceptable </strong><br><br>
<strong>○ No acceptable </strong><br><br>
● Incloure evidències (captures). <br><br>
● Incloure una conclusió tècnica. <br><br>
`2.4.4 Validació `<br><br>
Es considerarà correcte si: <br><br>
● Les proves estan documentades. <br><br>
● Els resultats són interpretats correctament. <br><br>
● Existeix relació clara entre rendiment i serveis. <br><br>
`2.5 Documen``t``ació a lliurar `<br><br>
L’alumne haurà de lliurar: <br><br>
● Descripció de la infraestructura. <br><br>
● Esquema de xarxa. <br><br>
● Procediment d’instal·lació i configuració. <br><br>
● Justificació de tecnologies. <br><br>
● Proves de funcionament: <br><br>
○ Àudio <br><br>
○ Video <br><br>
○ Videoconferència <br><br>
● Amplada de banda <br><br>
● Incidències i solucions. <br><br>
`2.6 Criteris d’avaluació `<br><br>
Es valorarà: <br><br>
● Compliment dels requeriments tècnics. <br><br>
● Funcionament real dels serveis. <br><br>
● Ús correcte de formats i protocols. <br><br>
● Integració amb el sistema global. <br><br>
● Qualitat de la documentació. <br><br>
● Compliment dels requisits mínims obligatoris. <br><br>
<strong>`2. IMPLANTACIÓ DELS SERVEI D'ÀUDIO I VÍDEO`</strong><br><br>
<u>`2.1 Descripció General`</u><br><br>
`InnovateTech ha desplegat una infraestructura multimèdia desacoblada de forma nativa sobre Ubuntu Server a AWS, escalada a una instància t2.large (8 GB RAM) per gestionar alta concurrència sense degradació de CPU ni requerir memòria Swap.`<br><br>
<u>`2.2 Implantació del Servei d’Àudio (RA7)`</u><br><br>
<em>`2.2.1 Funcionalitat del Servei`</em><br><br>
<strong>`Arquitectura: `</strong>`Liquidsoap genera el flux continu des de fitxers MP3 locals i l'injecta per socket intern al servidor de mitjans Icecast2, que gestiona la multidifusió externa.`<br><br>
<strong>`Format:`</strong>` MP3 constant a 192 Kbps (Tipus MIME: audio/mpeg).`<br><br>
<strong>`Alta disponibilitat:`</strong>` Script radio.liq amb directiva fallback(track_sensitive=false, [musica, seguretat]) connectada a blank(). Si la llista falla, emet silenci digital evitant la caiguda del punt de muntatge.`<br><br>
<em>`2.2.2 Evidències i Justificació de Captures`</em><br><br>
<strong>`CAPTURA 1: Serveis d’àudio actius`</strong><br><br>
`«Certifica l'execució persistent i en segon pla dels daemons d'àudio sota el control de Systemd de Linux.»`<br><br>
<em>`sudo systemctl status icecast2 &amp;&amp; ps aux | grep liquidsoap.`</em><br><br>
</div>

<p align="center">
  <img src="images/img_31.png" alt="Imagen 31" />
</p>

<div align="justify">
<strong>`CAPTURA 2: Socket de xarxa d'àudio obert`</strong><br><br>
`«Demostra l'aixecament del socket TCP al port corporatiu 8000 en estat LISTEN a totes les interfícies (0.0.0.0).»`<br><br>
`sudo ss -tlnp | grep 8000.`<br><br>
</div>

<p align="center">
  <img src="images/img_32.png" alt="Imagen 32" />
</p>

<div align="justify">
 <strong>`CAPTURA 3: Interfície web pública d'Icecast2`</strong><br><br>
`«Valida la publicació a Internet del servidor i la disponibilitat immediata del punt de muntatge actiu /stream.»`<br><br>
`Navegador web accedint a http://98.83.198.167:8000`<br><br>
</div>

<p align="center">
  <img src="images/img_33.png" alt="Imagen 33" />
</p>

<div align="justify">
<strong>`CAPTURA 4: Connexió de client extern i còdec`</strong><br><br>
`«Finestra del navegador web connectada al servidor de producció per validar la resposta HTTP de l'enrutament del directori de streaming.» `<br><br>
</div>

<p align="center">
  <img src="images/img_34.png" alt="Imagen 34" />
</p>

<div align="justify">
<strong>`CAPTURA 5: Auditoria del servei (Logs)`</strong><br><br>
`Terminal amb tail -f /var/log/icecast2/access.log durant la reproducció.`<br><br>
`«Demostra el registre en temps real de les peticions HTTP GET i les respostes d'èxit (codi 200 OK) enviades als clients.»`<br><br>
</div>

<p align="center">
  <img src="images/img_35.png" alt="Imagen 35" />
</p>

<div align="justify">
<strong>`2.3 Implantació del Servei de Vídeo i Videoconferència (RA8)`</strong><br><br>
<em>`2.3.1 Funcionalitat del Servei`</em><br><br>
`Jellyfin: Instal·lació nativa (paquets .deb, sense Docker) per a accés directe a disc i consum òptim de RAM.`<br><br>
`Protocol de Streaming: HLS (HTTP Live Streaming), que fragmenta el vídeo per minimitzar el buffering.`<br><br>
`Format i Còdecs: Fitxer origen a la ruta `<br><br>
`/var/www/videos/videoplayback.mp4 en contenidor MP4 (Còdecs H.264 per a vídeo i AAC per a àudio), permetent reproducció directa (Direct Play) sense transcodificació.`<br><br>
`Videoconferència: Jitsi Meet sota arquitectura WebRTC en temps real, implementat obligatòriament sota xifrat HTTPS (Port 443) per habilitar perifèrics.`<br><br>
<em>`2.3.2 Evidències i Justificació de Captures`</em><br><br>
<strong>`CAPTURA 6: Socket del servidor de vídeo`</strong><br><br>
`«Verifica que el daemon natiu de Jellyfin està operatiu i escoltant correctament peticions al port TCP 8096.»`<br><br>
`Terminal amb sudo ss -tlnp | grep 8096.

`<br><br>
</div>

<p align="center">
  <img src="images/img_36.png" alt="Imagen 36" />
</p>

<div align="justify">
<strong>`CAPTURA 7: Validació de format del fitxer origen`</strong><br><br>
`«Prova de control de format que confirma que el fitxer corporatiu és un contenidor MP4 codificat en H.264.»`<br><br>
`Terminal amb file /var/www/videos/videoplayback.mp4.`<br><br>
</div>

<p align="center">
  <img src="images/img_37.png" alt="Imagen 37" />
</p>

<div align="justify">
<strong>`CAPTURA 8: Inspecció de streaming dinàmic (HLS)`</strong><br><br>
`«Demostra l'ús de streaming real: es constata el servei continu de fragments de transport .ts guiats per un índex .m3u8 sota protocol HLS.»`<br><br>
</div>

<p align="center">
  <img src="images/img_38.png" alt="Imagen 38" />
</p>

<div align="justify">
<strong>`CAPTURA 9: Videoconferència Jitsi Meet activa`</strong><br><br>
`«Certifica la implantació del servei de videoconferència sota arquitectura WebRTC i canal protegit per TLS/HTTPS.»`<br><br>
`Pantalla completa de la sala Jitsi amb 2 usuaris concurrents amb àudio/vídeo i el candau de xifrat HTTPS a la URL.`<br><br>
</div>

<p align="center">
  <img src="images/img_39.png" alt="Imagen 39" />
</p>

<div align="justify">
<u>`2.4 Comprovacions d’Amplada de Banda`</u><br><br>
<em>`2.4.1 Evidències de Rendiment de Xarxa`</em><br><br>
<strong>`CAPTURA 10: Prova de velocitat de la instància (CPD)`</strong><br><br>
`«Aporta les mètriques d'auditoria de la capacitat simètrica de la línia del núvol d'AWS (Download, Upload i Latència).»`<br><br>
`Execució a la terminal de l'eina speedtest-cli.`<br><br>
</div>

<p align="center">
  <img src="images/img_40.png" alt="Imagen 40" />
</p>

<div align="justify">
<em>`2.4.2 Anàlisi de concurrència i impacte en hardware`</em><br><br>
`Càlcul analititzat del consum simultani en el pitjor escenari:`<br><br>
`Streaming Àudio (MP3 192 Kbps): 0.19 Mbps de pujada.`<br><br>
`Streaming Vídeo (Jellyfin HLS HD): 4.00 Mbps de pujada.`<br><br>
`Videoconferència (Jitsi Meet WebRTC): 2.50 Mbps de pujada.`<br><br>
`Ample de banda crític combinat: 6.69 Mbps sostinguts.`<br><br>
<strong>`CAPTURA 11: Monitorització de recursos en càrrega simultània`</strong><br><br>
`«Demostra l'impacte gràfic i la coexistència dels processos de fons sobre la memòria i la CPU de la instància sota estrès.»`<br><br>
`Terminal amb el comando htop executat mentre es reprodueixen els 3 serveis alhora de forma concurrent.`<br><br>
</div>

<p align="center">
  <img src="images/img_41.png" alt="Imagen 41" />
</p>

<div align="justify">
<em>`2.4.3 Conclusió Tècnica d'Auditoria`</em><br><br>
<strong>`Classificació del Sistema: ACCEPTABLE`</strong><br><br>
`La infraestructura es classifica com a Altament Acceptable. Les mètriques reals d'AWS certifiquen una capacitat simètrica de 1 Gbps (1016.95 Mbps d'Upload), superant en un 15.000% l'ample de banda crític demandat (6.69 Mbps). Això garanteix zero colls d'ampolla. La latència obtinguda de 5.61 ms és perfecta per a WebRTC.`<br><br>
`L'escalat vertical a una instància t2.large (8 GB RAM física natius) absorbeix de forma folgada els serveis sense requerir memòria d'intercanvi (Swap) i immunitza el sistema operatiu contra el procés Linux OOM Killer, cobrint els requisits d'alta disponibilitat.`<br><br>
3 Disseny i implementació d’una base de dades <br><br>
`3.1 Context del Projecte `<br><br>
A més de la infraestructura dedicada a la operativa de l'empresa, l'empresa disposa d'una estructura interna amb diferents departaments (vendes, suport tècnic, administració i logística), els quals necessiten eines de comunicació eficients, incloent-hi un sistema de videoconferències i trucades internes. <br><br>
</div>

| Objectiu de la part de Bases de Dades  Dissenyar i implementar una base de dades integral per a InnovateTech que doni suport a les següents funcionalitats:  • La gestió del personal i l'estructura organitzativa de l'empresa.  • El sistema de comunicació interna: videotrucades, i gestió de l'streaming d’audio i de vídeo.  • El control d'accés, seguretat i auditoria de la base i els sistemes instal·lats. |
| --- |

<div align='justify'>

`3.2 Disseny i Implementació de la Base de Dades `<br><br>
Es tracta de dissenyar i implementar una base de dades completa per a la gestió d'InnovateTech, i que serveixí per a gestionar els serveis que s’implementen de streaming d'àudio i de vídeo. Aquesta base de dades servirà com a font de dades per a una aplicació de gestió que residirà al servidor web que també s’ha d’instal·lar. <br><br>
A continuació s'especifiquen les entitats, atributs i requisits funcionals que ha de cobrir la base de dades. <br><br>
<u>`3.2.1 Gestió del Personal i Estructura Organitzativa`</u> <br><br>
La base de dades ha de gestionar tota la informació relacionada amb el personal de l'empresa. Concretament: <br><br>
<strong>Empleats </strong><br><br>
• Identificador principal: DNI (únic per a cada empleat). <br><br>
• Dades personals: nom, cognoms, adreça completa i telèfon de contacte. • Cada empleat pertany a un únic departament. <br><br>
</div>

<p align="center">
  <img src="images/img_42.png" alt="Imagen 42" />
</p>

<div align="justify">
<strong>Departaments </strong><br><br>
• Codi identificador (únic per a cada departament). <br><br>
• Nom complet del departament. <br><br>
• Telèfon del departament. <br><br>
</div>

<p align="center">
  <img src="images/img_43.png" alt="Imagen 43" />
</p>

<div align="justify">
`3.2.2 Sistema de Comunicació Interna (Videotrucades i Streaming) `<br><br>
<strong>InnovateTech </strong>disposa d'un sistema de videotrucades i streaming de vídeo per a la comunicació interna i per als seus clients. La base de dades ha de gestionar els aspectes que es detallen a continuació. <br><br>
<strong>Usuaris del sistema de comunicació (empleats) </strong><br><br>
• Dades dels usuaris: nom complet, correu electrònic, extensió/identificador de trucades, estat (actiu/bloquejat). <br><br>
• Per a cada usuari, s'ha de poder generar un enllaç per iniciar una videotrucada. • Distinció entre tipus d'usuari: clients externs i treballadors interns (amb els seus rols). <br><br>
</div>

<p align="center">
  <img src="images/img_44.png" alt="Imagen 44" />
</p>

<div align="justify">
<strong>Configuració de trucades i qualitat de servei </strong><br><br>
• S'ha d'emmagatzemar la configuració de qualitat de vídeo/àudio per a grups d'usuaris (per exemple: alta, mitja, baixa qualitat de streaming). <br><br>
• Quan un usuari té limitacions d'amplada de banda, el sistema ha de poder recuperar la configuració de qualitat inferior corresponent al seu grup. <br><br>
• Configuració del servidor de videotrucades: paràmetres generals del servei, ports, protocols. <br><br>
</div>

<p align="center">
  <img src="images/img_45.png" alt="Imagen 45" />
</p>



<p align="center">
  <img src="images/img_46.png" alt="Imagen 46" />
</p>

<div align="justify">
<strong>Registre d'activitat de trucades </strong><br><br>
• Registre de cada trucada realitzada: usuari/client originador, destinatari, data i hora d'inici, data i hora de fi, durada total, qualitat de servei usada. <br><br>
• Possibilitat de consultar les trucades per usuari o client (historial complet). <br><br>
• Valoració del servei per part de l'usuari (puntuació i comentari opcional). <br><br>
</div>

<p align="center">
  <img src="images/img_47.png" alt="Imagen 47" />
</p>

<div align="justify">
<strong>Gestió del catàleg de vídeos en streaming </strong><br><br>
• Emmagatzemar la informació dels vídeos disponibles al sistema d'streaming: títol, descripció, categoria, durada, data de publicació. <br><br>
• Per a cada vídeo, guardar l'enllaç al servidor d'streaming per poder-hi accedir directament. <br><br>
• Possibilitat de fer cerques de vídeos per títol, categoria o paraules clau. <br><br>
</div>

<p align="center">
  <img src="images/img_48.png" alt="Imagen 48" />
</p>

<div align="justify">
<strong>Anàlisi d'amplada de banda </strong><br><br>
• Emmagatzemar els resultats de les mesures d'amplada de banda realitzades pels operaris: data i hora de la mesura, usuari/equip mesurat, velocitat de baixada, velocitat de pujada, latència, resultat (acceptable/no acceptable). <br><br>
• Cal emmagatzemar l'operari que ha realitzat la mesura i qualsevol nota o observació addicional. <br><br>
</div>

<p align="center">
  <img src="images/img_49.png" alt="Imagen 49" />
</p>

<div align="justify">
`→ Per comprovar que hem afegit totes les taules correctament, fem un “show tables;” i revisem els noms de totes les taules. `<br><br>
</div>

<p align="center">
  <img src="images/img_50.png" alt="Imagen 50" />
</p>



| Integració valorada positivament  S'avaluarà positivament la integració automàtica del registre de mesures d'amplada de banda als scripts de comprovació, per sobre de la inserció manual mitjançant una aplicació, i aquesta per sobre de la inserció directa transformant logs manualment. |
| --- |

<div align='justify'>

`→ Per fer la integració automatitzada, hem creat un script que mesura i registra la qualitat de la xarxa de forma autònoma, i l’hem afegit al crontab perquè es vagi aplicant de forma constant i enregistri l’estat d’aquesta. `<br><br>
</div>

<p align="center">
  <img src="images/img_51.png" alt="Imagen 51" />
</p>



<p align="center">
  <img src="images/img_52.png" alt="Imagen 52" />
</p>

<div align="justify">
 `3.3. Gestió d'Usuaris, Rols i Permisos `<br><br>
Aquesta secció és la part central de l'avaluació del mòdul 0377. Cal implementar un sistema complet de control d'accés a la base de dades, incloent-hi la creació d'usuaris, la definició de rols i l'assignació de permisos. <br><br>
`3.3.1 Definició de Rols `<br><br>
Cal crear com a mínim els rols següents, amb els permisos indicats: <br><br>
</div>

| Rol  | Permisos principals  | Restriccions específiques |
| --- | --- | --- |
| admin  | Accés total: SELECT, INSERT, UPDATE, DELETE, CREATE,  DROP, GRANT sobre totes les taules. | Pot veure i modificar la taula  d'avisos. Pot gestionar altres  usuaris. |
| vendes  | SELECT, INSERT, UPDATE sobre taules de clients, comandes,  productes, cistell i trucades. | Pot contactar i iniciar trucades amb clients. Pot consultar l'historial de trucades dels clients. |
| administracio  | SELECT, INSERT, UPDATE sobre taules de personal, nòmines,  departaments i grup-nivell. | No pot iniciar trucades amb clients ni accedir al sistema de  videotrucades de clients. |
| treballador  | SELECT sobre taules de productes, vídeos, configuració de trucades. Pot registrar la seva activitat de trucades. | No pot modificar taules de personal, nòmines ni dades de clients. |

<div align='justify'>

 `→ Per crear aquests rols i poder assignar-los a les taules correctas, hem de crear un parell mes de taules per adaptar les necessitats de la pràctica: `<br><br>
</div>

<p align="center">
  <img src="images/img_53.png" alt="Imagen 53" />
</p>

<div align="justify">
`→ Amb les taules fetes, creem els permisos i els assignem acord a la graella que ens proporciona la pràctica: `<br><br>
</div>

<p align="center">
  <img src="images/img_54.png" alt="Imagen 54" />
</p>



<p align="center">
  <img src="images/img_55.png" alt="Imagen 55" />
</p>



<p align="center">
  <img src="images/img_56.png" alt="Imagen 56" />
</p>



<p align="center">
  <img src="images/img_57.png" alt="Imagen 57" />
</p>



<p align="center">
  <img src="images/img_58.png" alt="Imagen 58" />
</p>

<div align="justify">
`→ Per garantir i verificar que hem aplicat tots els permisos on tocava, executem la comanda “show grants for” per a cada usuari i ho anem verificant amb la graella. `<br><br>
</div>

<p align="center">
  <img src="images/img_59.png" alt="Imagen 59" />
</p>

<div align="justify">
`3.3.2 Script de Creació Automatitzada d'Usuaris `<br><br>
Cal crear un script (en Bash o Python) que automatitzi la creació d'usuaris a la base de dades. L'script ha de: <br><br>
• Permetre donar d'alta un o més usuaris alhora, introduint el mínim de dades possible. <br><br>
• Executar les sentències CREATE USER i GRANT corresponents al rol assignat. <br><br>
• Generar un fitxer .sql amb les sentències SQL resultants, de manera que pugui ser revisat i executat posteriorment al SGBD. <br><br>
• Asignar el rol correcte a cada usuari en el moment de la creació. <br><br>
• Gestionar casos d'error: usuari ja existent, rol no vàlid, etc. <br><br>
• Permisos especials per generar bloquejos alhora de fer backups.( GRANT FILE) <br><br>
`→ Per crear aquest script, primer creem un arxiu on guardem tots els usuaris que volem afegir, posant-hi unes minimes dades per cada un. `<br><br>
`Després, creem l’script responsable d’afegir els usuaris. L’script valida errors com rols no autoritzats i assigna els permisos de mysql segons el rol, i dona permisos especials (GRANT FILE) a aquells amb el rol d’administrador per als bloquejos de seguretat dels backups.  `<br><br>
`També ens ha calgut afegir un tercer arxiu, que dona suport a tots aquests processos i es responsabilitza d’afegir correctament els usuaris amb les dades i els rols assignats en primera instància. `<br><br>
`→ Arxiu “usuaris.csv”:`<br><br>
</div>

<p align="center">
  <img src="images/img_60.png" alt="Imagen 60" />
</p>

<div align="justify">
`→ Script “user_creator.yml”: `<br><br>
</div>

<p align="center">
  <img src="images/img_61.png" alt="Imagen 61" />
</p>

<div align="justify">
`→ Script d’ajuda “inner_tasks.yml”:`<br><br>
</div>

<p align="center">
  <img src="images/img_62.png" alt="Imagen 62" />
</p>

<div align="justify">
Els rols mínims a suportar per l'script són: admin, vendes, administració, treballador. <br><br>
</div>

| Nota sobre el SGBD  Podeu triar el SGBD que vulgueu per a la implementació (MySQL/MariaDB, PostgreSQL, Oracle, etc.). Recordar de no utilitzar RDS ja que té un cost elevat. Fer-ho des d’un EC2. Cal justificar l'elecció. |
| --- |

<div align='justify'>

`→ Hem escollit el SGBD de ``MySQL per la seva simplesa i integració nativa dels triggers i scripts de Linux. Per evitar els elevats costos d'Amazon AWS, hem instal·lat el servidor directament en local dins de la nostra instància EC2 d'AWS. Amb això, tenim una base de dades simple d’utilitzar, facilment compatible amb les màquines que utilitem, i amb el minim cost per a l’empresa alhora d’utilitzar l’Amazon AWS.  `<br><br>
       `3.3.3 Triggers per al Control d'Accés i Auditoria `<br><br>
Cal implementar triggers que donin suport a la seguretat i auditoria de la base de dades: <br><br>
<strong>Control de quotes d'usuari (trucades) </strong><br><br>
• Trigger que controli la quota de minuts mensuals per usuari: si s'assoleix el límit, s'ha d'impedir la inserció d'una nova trucada i registrar l'avís. <br><br>
• Trigger que controli el nombre màxim de trucades diàries per usuari: si se supera, ha d'impedir noves trucades i registrar l'avís. <br><br>
`→ Per fer aquests triggers, creem la taula de “LOG_AUDITORIA” per poder aplicar els triggers a sobre.`<br><br>
</div>

<p align="center">
  <img src="images/img_63.png" alt="Imagen 63" />
</p>

<div align="justify">
`→ I després efectuem els triggers a sobre: `<br><br>
</div>

<p align="center">
  <img src="images/img_64.png" alt="Imagen 64" />
</p>



<p align="center">
  <img src="images/img_65.png" alt="Imagen 65" />
</p>

<div align="justify">
<strong>Taula d'avisos i auditoria </strong><br><br>
• Existència d'una taula d'avisos (log d'auditoria) on es registren els intents no autoritzats d'accés o modificació. <br><br>
• Trigger que, quan un usuari amb rol treballador o vendes intenti modificar taules restringides (per exemple, nòmines, configuració de rols, dades de salaris), registri l'intent a la taula d'avisos amb: usuari, taula afectada, operació intentada, data i hora. <br><br>
• Trigger que, quan un usuari amb rol administració intenti accedir o modificar les taules del sistema de trucades de clients, registri l'intent a la taula d'avisos. <br><br>
</div>

<p align="center">
  <img src="images/img_66.png" alt="Imagen 66" />
</p>



<p align="center">
  <img src="images/img_67.png" alt="Imagen 67" />
</p>



<p align="center">
  <img src="images/img_68.png" alt="Imagen 68" />
</p>



<p align="center">
  <img src="images/img_69.png" alt="Imagen 69" />
</p>

<div align="justify">
<strong>Gestió de bloqueig d'usuaris </strong><br><br>
• Trigger que impedeixi realitzar o rebre trucades si l'usuari es troba en estat bloquejat. • El bloqueig es pot aplicar de manera temporal o indefinida. <br><br>
</div>

<p align="center">
  <img src="images/img_70.png" alt="Imagen 70" />
</p>



| Ampliació opcional (valorada positivament)  Es valorarà positivament implementar un procés que revisi la taula d'avisos i envii notificacions per correu electrònic, Telegram o Discord als administradors quan es detectin intents d'accés no autoritzat. |
| --- |

<div align='justify'>

<u>`3.3.4 Events Periòdics (Còpies de Seguretat)`</u> <br><br>
Cal crear almenys un event d'execució periòdica que realitzi còpies de seguretat de les dades crítiques. L'event ha de: <br><br>
• Executar-se de manera automàtica amb una periodicitat definida (diària, setmanal, etc. — cal justificar l'elecció). <br><br>
• Utilitzar la sentencia SELECT ... INTO OUTFILE (o equivalent al SGBD escollit) per desar les dades en un fitxer de backup. <br><br>
• Incloure com a mínim les taules de: empleats, clients, comandes i registre d'activitat de trucades. <br><br>
• Registrar a una taula de control els events de backup realitzats (data, hora, taules incloses, resultat). <br><br>
`→ Primer creem de nou una taula especifica per a l’execució d’aqeusst backups: `<br><br>
</div>

<p align="center">
  <img src="images/img_71.png" alt="Imagen 71" />
</p>



<p align="center">
  <img src="images/img_72.png" alt="Imagen 72" />
</p>

<div align="justify">
`3.4. Disseny Entitat-Relació i Model Relacional `<br><br>
A partir dels requisits especificats a les seccions anteriors, cal realitzar: 1. Diagrama Entitat-Relació (E/R) complet que representi totes les entitats, atributs i relacions de la base de dades. El diagrama ha de ser clar, llegible i correctament cardinalitzat. <br><br>
</div>

<p align="center">
  <img src="images/img_73.png" alt="Imagen 73" />
</p>

<div align="justify">
2. Transformació al model relacional: a partir del diagrama E/R, cal obtenir l'esquema relacional complet, indicant per a cada taula: nom, atributs, clau primària (PK) i claus foranes (FK). <br><br>
</div>

<p align="center">
  <img src="images/img_74.png" alt="Imagen 74" />
</p>

<div align="justify">
3. Implementació en el SGBD: creació de totes les taules amb les restriccions adequades (PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE, CHECK), amb un nombre significatiu de dades de prova inserides. <br><br>
Cal incloure en la documentació captures de pantalla que demostrin que les taules s'han creat correctament i que les dades s'han inserit. <br><br>
4 Lliurament i presentació <br><br>
<strong>1. És obligatòria la presentació per poder avaluar les RAs. </strong><br><br>
2. Vídeo de 3 minuts el qual ha de tenir: <br><br>
a. Una Introducció on es plantegi un problema, una necessitat … i la solució proposada (Poc temps de duració) <br><br>
b. Una part amb la demo on es vegin el servidor i els clients en funcionament, i el manegament de les dades. <br><br>
c. Una conclusió, finalització del vídeo / presentació on justifiqueu perquè el vostre desplegament funciona i serveix per … <br><br>
3. Exposició de duració de 10-15 minuts explicant els punts i aspectes més importants del projecte transversal. Es valorarà: <br><br>
a. La qualitat del material de la presentació: claredat, estructura, faltes ortografia. <br><br>
b. Exposició realitzada del projecte i cenyida al temps disponible. c. Participació de tots els membres del grup de forma equitativa. d. Interacció i resposta a les preguntes al respecte. <br><br>
4. Enllaç publicat al GitHub del document en Markdown amb el recull d’evidències de tots els apartats i les respostes teòriques justificades <br><br>
<strong>Institut Tecnològic de Barcelona </strong><br><br>
https://www.itb.cat/ <br><br>
@iTecBcn<br><br>
<strong>CFGS Administració de sistemes Informàtics en Xarxa </strong><br><br>
<strong>Mòduls </strong>0371, 0377, 0378 i 1665 <strong>Curs 25/26 Primera convocatòria Grups </strong>A/B/C/D <br><br>
<strong>Formador/a: </strong><em>Equip docent ASIXc1A ,</em><em> </em><em>ed-asixc1b@itb.cat Equip docent ASIXc1C ,</em><em> </em><em>Equip docent ASIXc1D </em><br><br>


</div>

# 7. Hét: Hálózati Határvédelem és Felhasználó- / Jogosultságkezelés (AAA, AD) - Összefoglaló

Ez a dokumentum a 7. heti tananyagot foglalja össze, amely két fő témakört ölel fel: a hálózati határvédelmi technológiákat, valamint a felhasználó- és jogosultságkezelést AAA és Active Directory környezetben.

## I. Hálózati Határvédelem

A hálózati határvédelem az IT Biztonsági Szabályzat hálózati követelményeit megvalósító fizikai és logikai eszközök összessége. Célja a hozzáférés-vezérlés biztosítása preventív és detektív módon.

### 1. Tűzfalak típusai és működésük

-   **Csomagszűrők (Packet Filters)**:
    -   **Működési elv**: Az átmenő csomagokat engedélyezik vagy tiltják az IP és Transport rétegek paraméterei (forrás/cél IP, port, protokoll) alapján.
    -   **Előnyök**: Gyors, egyszerű szabályrendszer.
    -   **Hátrányok**: Alkalmazási szinten vak (nem látja a forgalom tartalmát), sok szabály (válaszok kezelése), ismeretlen protokoll elemek továbbítása (teljes L7).
-   **Állapotmegőrző Csomagszűrők (Stateful Packet Filters / SPF)**:
    -   **Működési elv**: Csomagszűrés mellett követik a kapcsolat állapotát (SEQ és ACK számok követése). Csak a létező kapcsolatokhoz tartozó csomagokat engedélyezik.
    -   **Előnyök**: Biztonságosabb, mint a sima csomagszűrő, gyors, egyszerű szabályrendszer.
    -   **Hátrányok**: Alkalmazási szinten még mindig vak, nem értelmez ismert protokoll elemeket.
-   **Proxy Tűzfalak (Application Layer Gateways)**:
    -   **Működési elv**: A kliens a tűzfalon futó alkalmazással kommunikál, a proxy alkalmazás pedig a szerverrel. A kliens a tűzfalat, a tűzfal a szervert címzi.
    -   **Előnyök**: Mélyebb védelem (L7 protokoll értelmezés, többcsatornás protokollok kezelése), protokoll manipuláció (tartalom szűrése, vírus/spam szűrés).
    -   **Hátrányok**: Nem transzparens (a kliens a tűzfalat címzi), protokollban támogatás szükséges, nagyobb erőforrás igény.
-   **Transzparencia**:
    -   **Transzparens működés**: A kliens közvetlenül a szerverrel kommunikál (azt hiszi). A tűzfal a forgalmat eltéríti az eredeti céljától, de a kliens a proxyval kommunikál.
    -   **Nem transzparens működés**: A kliens tudja, hogy a tűzfallal kommunikál.
-   **UTM (Unified Threat Management) és Next Generation Firewall (NGFW)**:
    -   **Működési elv**: Több technológiát egyesítenek egy eszközben (állapotmegőrző csomagszűrés, protokoll lehallgatás és felismerés, UID control, URL és applikáció szűrés, tartalomszűrés, vírus/spam szűrés).
    -   **Előnyök**: Komplett védelem egy felületről, nagy rugalmasság.
    -   **Hátrányok**: Signature frissítés (korrektív), SPF, ismeretlen protokoll elemek kezelése.

### 2. Címfordítás (NAT - Network Address Translation)

-   **Működési elv**: A hálózati csomagok forrás- vagy cél IP-címét (és/vagy portját) megváltoztató eljárás.
    -   **SNAT (Source NAT)**: Forrás IP-cím fordítása (kifelé menő forgalom esetén, pl. belső hálózat Internet felé).
    -   **DNAT (Destination NAT)**: Cél IP-cím fordítása (bejövő forgalom esetén, pl. Internetről DMZ szerverre, port forwarding).

### 3. Tűzfalak a felhőben

-   Alapvetően IaaS (Infrastructure as a Service) esetében értelmezhető.
-   PaaS (Platform as a Service) és SaaS (Software as a Service) esetében inkább WAF (Web Application Firewall) és API védelem, szűrés.
-   A fizikai szeparáció jelentőségét veszti (VLAN, MPLS, SDN).
-   A határok elmosódnak.

### 4. Authentikáció Tűzfalon

-   **Működési elv**: A felhasználók azonosítása és az azonosítási adatok felhasználása a döntéshozatalban (csoporttagság).
-   **Azonosítás helye**:
    -   **Protokollon belül (inband)**: A protokollba beépített autentikáció (pl. HTTP Basic Auth).
    -   **Protokollon kívül (outband)**: Külső eszközzel (dedikált, rejtjelezett csatornán, agent segítségével).

### 5. PAM (Privileged Access Management) Technológiák

-   **Cél**: A privilegizált (magas jogosultságú) felhasználók (pl. rendszergazdák) hozzáférésének ellenőrzése és felügyelete.
-   **Funkciók**: Hozzáférés-vezérlés (idő, UID, 4-eye elv, gateway autentikáció), tevékenység rögzítése, tartalom szűrés, viselkedéselemzés (UBA), Password Manager integráció.
-   **Megvalósítások**: Bastion host, Sniffer, Agent, Proxy.

## II. Felhasználó- és Jogosultságkezelés (AAA és Active Directory)

### 1. Hozzáférés-vezérlés

Korlátozza, hogy ki vagy mi használhat bizonyos erőforrásokat, és milyen műveleteket hajthat végre. Az eseményeket és hozzáféréseket logfájlokban vizsgálhatóvá teszi.

### 2. AAA (Authentication, Authorization, Accounting)

-   **Authentication (Hitelesítés)**: A felhasználóknak (vagy rendszergazdáknak) igazolniuk kell személyazonosságukat, mielőtt hozzáférnének a hálózathoz és erőforrásaihoz. Lehet jelszó-alapú, token-alapú, stb.
-   **Authorization (Engedélyezés)**: Meghatározza, hogy egy hitelesített felhasználó mely erőforrásokhoz férhet hozzá, és milyen műveleteket hajthat végre.
-   **Accounting (Könyvelés/Naplózás)**: Rögzíti a felhasználó tevékenységeit, beleértve a hozzáférés idejét, a használt erőforrásokat és az esetleges módosításokat.

### 3. Címtár Szolgáltatások (Directory Services)

Központosított felhasználó- és erőforráskezelést tesznek lehetővé.
-   **Előnyök**:
    -   A felhasználóknak nem kell emlékezniük az erőforrások fizikai címére.
    -   Minden erőforrás objektumként kezelhető, információkat tárolunk róluk.
    -   Az erőforrásokhoz csak megfelelő jogosultságokkal rendelkező felhasználók férhetnek hozzá.
    -   Központosított adminisztráció.
-   **X.500 szabvány**: Az LDAP alapja, hierarchikusan rendezett bejegyzések (DIT - Directory Information Tree), Distinguished Name (DN) azonosítók.
-   **LDAP (Lightweight Directory Access Protocol)**: Keresésre optimalizált speciális adatbázis, ami faszerkezetben tárolja az információt.

### 4. Active Directory (AD)

A Microsoft saját X.500 alapú címtárszolgáltatás implementációja Windows környezetben.
-   **Alapja**: LDAP protokollra épül, Kerberos protokoll-alapú autentikációt használ. Szorosan összefügg a DNS szolgáltatással.
-   **Előnyök**:
    -   Központosított adminisztráció a hálózat minden publikált erőforrásához (fájlok, megosztások, perifériák, felhasználók, csoportok).
    -   Erőforrásokhoz való hozzáférés szabályozása.
    -   Házirendek (Group Policies) kiosztása, szoftverek és frissítések telepítése.
-   **Objektumok**: Erőforrások (nyomtatók, megosztott tárhelyek), szolgáltatások (levelezés), felhasználók és csoportok.
-   **Sérülékenység**: Ha a Domain Controller (DC) leáll, semmilyen szolgáltatás nem érhető el (redundancia szükséges).

### 5. Kerberos Protokoll

Számítógépes hálózati hitelesítési protokoll, amely biztonságos módon igazolja a csomópontok közötti kommunikációban résztvevők személyazonosságát, nem biztonságos hálózaton keresztül is.
-   **Működése**: Szimmetrikus kulcsú titkosításon (AES) alapul. Védi az üzeneteket a lehallgatások és az ismétlődő támadások ellen.

### 6. Felhasználó- és Jogosultságkezelési Gyakorlat (Példa egy fejlesztő cég esetén)

A gyakorlati feladat egy fejlesztő cég számára egy központosított felhasználó- és jogosultságkezelési rendszer kialakítását célozza.
-   **Felmérés**: Munkakörök (vezető fejlesztő, fejlesztő, tesztelő, HR-es, pénzügyes, vezető), folyamatok, információk, adatok.
-   **Kérések**: Fájlmegosztás mappastruktúrájában ne lehessen új fájlt/mappát létrehozni a fő mappában, felhasználónevek email-struktúrához igazítása, partnerek/ellenőrök hozzáférése.
-   **Tervezés**: Szervezeti egységek (Fejlesztés, Adminisztráció, Menedzsment) és projektek (Arcfelismerő app, Gyerekfelügyelő app) alapján hierarchikus fájl- és jogosultságstruktúra.
-   **Jogosultságstruktúra**: Olvasási és írási/olvasási jogok meghatározása mappákra és csoportokra (pl. HR csoport: írás/olvasás a HR mappára, Pénzügy csoport: írás/olvasás a Pénzügy mappára, Projekt csoportok: olvasás a projektek mappáira).
-   **Hálózati terv**: Két verzió (egyszerűsített és elosztott szolgáltatás).

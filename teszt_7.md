# 7. Hét: Ellenőrző Teszt - Hálózati Határvédelem és Felhasználó- / Jogosultságkezelés (AAA, AD)

Ez a teszt a 7. heti "Hálózati Határvédelem és Felhasználó- / Jogosultságkezelés" tananyagra épül. Válaszaidat az összefoglaló és a tananyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (AAA Komponensek)**

Nevezd meg az **AAA** három komponensét, és mindegyikhez adj egy rövid definíciót vagy példát!

---

**2. Kérdés (Active Directory Előnyei)**

Sorolj fel legalább három olyan előnyt, amelyet az **Active Directory** biztosít egy vállalati környezetben a felhasználók és erőforrások kezelésében!

---

**3. Kérdés (Kerberos Protokoll)**

Mi a **Kerberos protokoll** elsődleges célja, és melyik kriptográfiai eljáráson alapul a biztonságos működése?

---

**4. Kérdés (Tűzfal Típusok Összehasonlítása)**

Hasonlítsd össze a **Csomagszűrő (Packet Filter)**, az **Állapotmegőrző Csomagszűrő (Stateful Packet Filter)** és a **Proxy Tűzfal** típusokat egy-egy kulcsfontosságú előny/hátrány alapján!

---

**5. Kérdés (NAT/PAT)**

Mi a különbség a **SNAT (Source NAT)** és a **DNAT (Destination NAT)** között a hálózati címfordítás (NAT) során? Melyiket mikor alkalmazzuk tipikusan?

---

**6. Kérdés (PAM Célja)**

Mi a **Privileged Access Management (PAM)** technológiák elsődleges célja egy informatikai rendszerben?

---

**7. Kérdés (Szoftverfejlesztő Cég Szcenárió - Jogosultságok)**

A fejlesztő cég példájában a `/Fájlmegosztás/Pénzügy/Kimutatások` mappában a `Pénzügy csoport` tagjai milyen minimális hozzáférési jogokkal rendelkezzenek, és miért?

---

**8. Kérdés (Szoftverfejlesztő Cég Szcenárió - Projekt Mappa Struktúra)**

A cég kérései között szerepel, hogy a fájlmegosztás mappastruktúrájának első szintjén (fő mappában, pl. `/Fájlmegosztás/Projektek`) **ne lehessen új fájlokat vagy mappákat létrehozni**. Milyen jogosultságot állítanál be a `/Fájlmegosztás/Projektek` mappán, és kire/melyik csoportra vonatkozóan, hogy ezt elérd?

---

**9. Kérdés (Tűzfalak a Felhőben)**

Milyen kihívásokat vagy megfontolásokat jelent a tűzfalak implementálása **IaaS (Infrastructure as a Service)** felhőkörnyezetben a hagyományos (on-premise) hálózati tűzfalakhoz képest? Említs meg legalább egyet!

---

**10. Kérdés (Kerberos Működés)**

Magyarázd el röviden a Kerberos protokoll működésének alapvető lépéseit egy felhasználó szemszögéből, aki egy szolgáltatáshoz szeretne hozzáférni egy hálózaton!

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
-   **Authentication (Hitelesítés)**: Annak igazolása, hogy a felhasználó az, akinek mondja magát. *Példa:* Jelszó beírása a bejelentkezéskor.
-   **Authorization (Engedélyezés)**: Meghatározza, hogy egy hitelesített felhasználó mely erőforrásokhoz férhet hozzá, és milyen műveleteket hajthat végre. *Példa:* Egy mappához való olvasási vagy írási jog.
-   **Accounting (Könyvelés/Naplózás)**: Rögzíti a felhasználó tevékenységeit, a használt erőforrásokat és az esetleges módosításokat. *Példa:* Rendszernaplók, amelyek rögzítik a fájlokhoz való hozzáférést.

**2. Kérdés:**
1.  **Központosított adminisztráció**: Egységesen kezelhetők a felhasználók, csoportok, erőforrások a teljes hálózaton.
2.  **Skálázhatóság**: Nagyobb felhasználói bázist és több erőforrást képes kezelni.
3.  **Házirendek és csoportok**: Lehetővé teszi a biztonsági és konfigurációs házirendek (Group Policy) központosított alkalmazását felhasználókra és gépekre, csoportokba rendezve az adminisztráció megkönnyítésére.
4.  **Integrált szolgáltatások**: Szorosan integrálódik más Microsoft szolgáltatásokkal (pl. DNS, Kerberos autentikáció), egységes belépési pontot biztosítva.

**3. Kérdés:**
A **Kerberos protokoll** elsődleges célja, hogy biztonságos módon igazolja a hálózaton kommunikáló csomópontok (felhasználók és szolgáltatások) személyazonosságát, még egy nem biztonságos hálózaton keresztül is. A biztonságos működése **szimmetrikus kulcsú titkosításon** (pl. AES) alapul.

**4. Kérdés:**
-   **Csomagszűrő (Packet Filter)**:
    *   *Réteg:* Hálózati és Transport réteg (L3-L4).
    *   *Előny:* Gyors, egyszerű.
    *   *Hátrány:* Alkalmazási szinten vak, nem látja a forgalom tartalmát.
-   **Állapotmegőrző Csomagszűrő (Stateful Packet Filter)**:
    *   *Réteg:* Hálózati és Transport réteg (L3-L4), de követi a kapcsolat állapotát.
    *   *Előny:* Biztonságosabb, mint a sima csomagszűrő, blokkolja a nem kezdeményezett bejövő forgalmat.
    *   *Hátrány:* Alkalmazási szinten még mindig vak.
-   **Proxy Tűzfal**:
    *   *Réteg:* Alkalmazási réteg (L7).
    *   *Előny:* Mélyebb forgalomelemzés, protokoll-specifikus szűrés, tartalommanipuláció.
    *   *Hátrány:* Lassabb, nagyobb erőforrásigény, nem transzparens lehet.

**5. Kérdés:**
-   **SNAT (Source NAT)**: A kimenő forgalomban a belső hálózati cím (forrás IP) átírása egy külső, publikus IP-címre. *Alkalmazás:* Belső hálózatból induló Internet elérés.
-   **DNAT (Destination NAT)**: A bejövő forgalomban a külső IP-cím (cél IP) átírása egy belső hálózati címre. *Alkalmazás:* Porttovábbítás, külső szerverek elérése a DMZ-ben.

**6. Kérdés:**
A **Privileged Access Management (PAM)** technológiák elsődleges célja a rendszerben lévő privilegizált (magas jogosultságú) felhasználói fiókok és hozzáférések (pl. rendszergazda, root) ellenőrzése, felügyelete, kezelése és biztonságának megerősítése, minimalizálva az ezekkel járó kockázatokat.

**7. Kérdés:**
| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Interfész (forrás -> cél) | Megjegyzés |
| :------ | :------ | :-------- | :-------- | :---------- | :------ | :-------- | :------------------------ | :--------- |
| 1       | Allow   | TCP       | 192.168.60.250 | Any         | 192.168.50.240 | 3306    | DMZ -> Internal LAN     | Adatbázis hozzáférés webszerverről |

*(Megjegyzés: Ahhoz, hogy minden más forgalmat tiltani kelljen, egy "Deny Any Any" szabálynak kellene követnie ezt a Belső LAN felé irányuló forgalmon, vagy a Default Policy-nak kellene Deny-nak lennie.)*

**8. Kérdés:**
A `/Fájlmegosztás/Projektek` mappán a **Létrehozás/Törlés** jogokat kellene tiltani az összes felhasználó számára (vagy csak a `Tartományi felhasználók` csoportnak), miközben az **Olvasás/Végrehajtás** jogokat engedélyezni. Ezzel megakadályozható, hogy a fő mappában új fájlokat/mappákat hozzanak létre, de az alatta lévő projektek mappáit elérhetik. Az alatta lévő projektek mappáinál pedig a `Projekt csoportok` (pl. `Fejlesztők`, `Vezető fejlesztők`) számára kellene engedélyezni a létrehozást/módosítást.

**9. Kérdés:**
Egy kulcsfontosságú kihívás, hogy a fizikai szeparáció a felhőben másképp valósul meg (virtuális hálózatok, VLAN-ok, stb.), mint egy hagyományos hálózatban. A határok elmosódnak, és a hipervizor réteg bevezetésével új támadási felületek jelenhetnek meg (pl. Meltdown, Spectre). Emiatt a hagyományos tűzfal koncepciót újra kell gondolni, és a szoftveresen definiált hálózatok (SDN) és a mikroszegmentáció felé kell elmozdulni.

**10. Kérdés:**
Egy felhasználó szeretne hozzáférni egy szolgáltatáshoz (`Service Server - SS`).
1.  A `Client` elküld egy hitelesítési kérelmet az `Authentication Server (AS)`-nek (pl. felhasználónév, jelszó hash).
2.  Az `AS` ellenőrzi a felhasználó hitelességét (jelszóval). Ha sikeres, visszaküld a kliensnek egy **Ticket-Granting Ticket (TGT)**-t, amit a kliens titkos kulcsával titkosít.
3.  A `Client` ezután elküldi a `TGT`-t a **Ticket-Granting Server (TGS)**-nek, hogy jegyet kérjen a kívánt szolgáltatáshoz.
4.  A `TGS` a `TGT` és a szolgáltatás kulcsa alapján generál egy **szolgáltatási jegyet (Service Ticket)**, amit titkosítva visszaküld a kliensnek.
5.  A `Client` elküldi a `Service Ticket`-et a `Service Server`-nek. A `Service Server` a saját kulcsával dekódolja, és ellenőrzi a felhasználó azonosságát, majd engedélyezi a hozzáférést a szolgáltatáshoz.
Ez a folyamat elkerüli, hogy a jelszó soha ne utazzon a hálózaton, és minden lépésnél kölcsönös hitelesítés történik.
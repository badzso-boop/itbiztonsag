# 4. Hét: Ellenőrző Teszt - Fejlettebb Kriptológia és Tűzfalak

Ez a teszt a 4. heti "Fejlettebb Kriptológia és Tűzfalak" tananyagra épül. Válaszaidat az összefoglaló és a megadott gyakorlati anyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (RSA Algoritmus)**

Sorold fel az RSA algoritmus kulcsválasztásának főbb lépéseit (a `p` és `q` prímek kiválasztásától a nyilvános és titkos kulcsok meghatározásáig)!

Megoldas: Hát a p és q egy kulonbozo de nagy szam. Ki kell szamitani a szorzatokat = N. Majd euler fuggvenyt is szamiutunk. lesz egy e nyilvanos kitevo es ki kell szamitani a d-t mint titkos kitevo

---

**2. Kérdés (Hash Függvények Elvárásai)**

Egy kriptográfiai hash függvénynek három alapvető biztonsági elvárásnak kell megfelelnie. Nevezd meg és röviden magyarázd el ezeket!

Megoldas: 1. one way tehat ha egy szoveget tiksotiunk hash-re akkor azt mar vissza ne lehessen fejteni. 2. ne lehessen ket szovegnek ugyan az a hashje vagy ket hashnek ugyan az a szovege. 3. Mindig fix hosszusagu a hash

---

**3. Kérdés (Digitális Aláírás vs. MAC)**

Mi a fő különbség a **Digitális Aláírás** és a **MAC (Message Authentication Code)** között? Milyen helyzetben melyiket érdemes használni?

Megoldas: A digitalis alairas azt tamasztja ala hogy a dokumentum ugyan az tehat az integritasa megmarad es a hitelesseget biztositja. Barki a publikus kulcs alapjan dekodolhatja. A MAC az egy összeg ami egy titkos koddal jon ki es ez biztositja, hogy a tamado ne tudja feltorni. asszem

---

**4. Kérdés (Tűzfal Topológia)**

Az `M1: Cél architektúra modell` ábra alapján nevezz meg legalább két, a **DMZ-ben** (Demilitarizált Zónában) elhelyezkedő hálózati komponenst, és magyarázd el röviden a DMZ szerepét a hálózat biztonságában!

Megoldas: Webszerver, Fájlszerver A DMZ azert fontos mert ide nem tud senki se bemenni csak az engedelyezett alhalozatrol viszont barki eleri az engedelyezett portokat igy a webszerver es a fajlszerver is elerheto de semmi mas nem

---

**5. Kérdés (Tűzfal Szabálylista Típusok)**

Mi a különbség a **Blacklist (feketelista)** és a **Whitelist (fehérlista)** alapú tűzfal szabályzatok között? Melyik nyújt magasabb biztonsági szintet, és miért?

Megoldas: A blacklist alapertelmezetten mindent enged csak azt nem ami bele van irva. Ez gyengebb biztonsag. A whitelist alapertelmezetten mindent tilt csak azt nem ami bele van irva -> ez nagyobb biztonsag

---

**6. Kérdés (Tűzfalszabály írása - Nyilvános Webszerver elérése)**

A gyakorlati feladat célja, hogy a külső kliensek elérhessék a `Publikus Webszerver` weboldalát (HTTP és HTTPS forgalom). A szerver IP-címe `192.168.60.250`, a DMZ LAN `192.168.60.0/24`, a WAN interfész az Internet felé néz.

Írj egy tűzfalszabályt, amely lehetővé teszi ezt a forgalmat! (Formátum: Sorrend, Művelet, Protokoll, Forrás IP, Forrás port, Cél IP, Cél port, Megjegyzés)

Megoldas: 
| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés |
| 1. | allow | udp | * | * | 192.168.60.250 | 80 | webszerver engedelyezes |

---

**7. Kérdés (Tűzfalszabály írása - Kimenő forgalom szűrése)**

A feladatleírás szerint az egyik probléma a jelenlegi állapotban, hogy "Kifelé minden mehet szűrés nélkül".
Írj egy tűzfalszabályt, amely tiltja a belső hálózatból (Internal LAN: `192.168.50.0/24`) induló, Internet felé irányuló minden forgalmat, kivéve a DNS (UDP 53) és a webböngészés (HTTP 80, HTTPS 443) forgalmát! Tételezz fel egy utolsó, mindent tiltó szabályt, ha szükséges.

Megoldas: 

| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés
| 1. | allow | udp | 192.168.50.0/24 | * | internet | 53 | nemtudom fejbol az internet ip-jet de ez engedelyezi a dns-t
| 2. | allow | udp | 192.168.50.0/24 | * | internet | 80 | nemtudom fejbol az internet ip-jet de ez engedelyezi a web protokolt
| 3. | * | * | 192.168.50.0/24 | * | * | * | ez mindent tilt

---

**8. Kérdés (Tűzfal Szabályok Sorrendje)**

Miért kritikus a tűzfalszabályok sorrendje? Adj egy rövid példát arra, hogy egy szabály rossz helyen milyen biztonsági problémát okozhat!

Megoldas: Mivel ha az elejere kerul egy deny es aztmondja a tuzfal hogy je ez az en uzenetemnek pont jo akkor csak szimplan letiltja meg akkor is ha alatta pont kivetelkent engedelyzve lenne az az egy keres.

---

**9. Kérdés (Port Forwarding)**

Mi a **Port Forwarding (Porttovábbítás)** lényege, és miért van rá szükség egy olyan hálózati topológiában, mint a gyakorlati feladatban?

Megoldas: Hogy egy halozatbol csak a megfelelo porton futo szolgaltatasokat erjek  el kivulrol. Ez azert fontos mert ezzel megorizheto annak a biztonsaga hogy mas porton nem fog senki se illetektelenul behatolni

---

**10. Kérdés (Aszimmetrikus kriptográfia előnye)**

Az aszimmetrikus kulcsú titkosítás egyik legnagyobb előnye, hogy megoldja a **kulcscsere problémáját**. Magyarázd el röviden, mit jelent ez a probléma a szimmetrikus kriptográfiában, és hogyan küszöböli ki ezt az aszimmetrikus megközelítés!

Megoldas: Ezt mar nemtudom :(
Javitas: 
A kulcscsere problémája a szimmetrikus kriptográfiában az, hogy a kommunikáló feleknek valamilyen biztonságos módon meg kell osztaniuk egymással a titkos kulcsot, még mielőtt a titkosított kommunikáció megkezdődne. Az aszimmetrikus kulcsú titkosítás ezt úgy küszöböli ki, hogy mindenki nyilvánosságra hozhatja a titkosításhoz használt nyilvános kulcsát. Bárki titkosíthat üzenetet ezzel a nyilvános kulccsal, de csak a kulcs tulajdonosa (aki ismeri a titkos kulcsot) tudja azt dekódolni. Így nincs szükség titkos kulcsok előzetes biztonságos megosztására.

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
Az RSA algoritmus kulcsválasztásának főbb lépései:
1.  Válasszunk két nagy, különböző prím számot (`p` és `q`).
2.  Számítsuk ki `N = p * q`.
3.  Számítsuk ki `φ(N) = (p-1) * (q-1)`.
4.  Válasszunk egy `e` (nyilvános kitevő) számot, ami relatív prím `φ(N)`-hez.
5.  Számítsuk ki `d` (titkos kitevő) értékét úgy, hogy `e * d ≡ 1 (mod φ(N))`.
A nyilvános kulcs `(N, e)`, a titkos kulcs `(p, q, d)`.

**2. Kérdés:**
1.  **Egyirányúság (One-Wayness)**: A hash értékből gyakorlatilag lehetetlen visszafejteni az eredeti bemenetet.
2.  **Gyenge ütközés-ellenállóság (Second Preimage Resistance)**: Adott bemenethez (`x`) szinte lehetetlen találni egy másik bemenetet (`x'`), amelynek ugyanaz a hash értéke (`h(x) = h(x')`).
3.  **Erős ütközés-ellenállóság (Collision Resistance)**: Gyakorlatilag lehetetlen találni két tetszőleges, különböző bemenetet (`x` és `x'`), amelyeknek ugyanaz a hash értéke (`h(x) = h(x')`).

**3. Kérdés:** A **MAC** (Message Authentication Code) egy titkos kulcsot használ az üzenet hitelesítésére, és mind a feladónak, mind a vevőnek ismernie kell. Emiatt nem biztosít letagadhatatlanságot. A **Digitális Aláírás** ezzel szemben aszimmetrikus kulcsú titkosítást használ, a feladó a *titkos kulcsával* írja alá az üzenetet, amit bárki a *nyilvános kulcsával* ellenőrizhet. Ez biztosítja a letagadhatatlanságot is. Digitális aláírást használnak nyilvános dokumentumok hitelesítésére, MAC-et belső rendszerekben, ahol a kulcsok biztonságosan megoszthatók.

**4. Kérdés:**
A DMZ-ben elhelyezkedő komponensek az ábra alapján:
-   **Publikus Webszerver (192.168.60.250)**
-   Magát a **DMZ LAN**-t (`192.168.60.0/24`) is ide soroljuk.
A **DMZ (Demilitarizált Zóna)** szerepe, hogy egy puffer zónát képezzen a külső (Internet) és a belső hálózat között. Az itt elhelyezett szerverek szolgáltatásokat nyújtanak a külső felhasználóknak, de izoláltan működnek a belső hálózattól, így egy esetleges támadás esetén nem jutnak át közvetlenül a belső, érzékeny erőforrásokhoz.

**5. Kérdés:**
-   **Blacklist (Feketelista)**: Alapértelmezésben **mindent engedélyez**, és csak a kifejezetten tiltott forgalmat blokkolja.
-   **Whitelist (Fehérlista)**: Alapértelmezésben **mindent blokkol**, és csak a kifejezetten engedélyezett forgalmat engedi át.
A **Whitelist** nyújt magasabb biztonsági szintet, mert sokkal szigorúbb: csak azt engedi át, amit expliciten megengedtünk, így minimálisra csökken a nem kívánt forgalom. A blacklist könnyebben kihagyhat olyan, újonnan felmerülő fenyegetéseket, amelyek nincsenek rajta a tiltólistán.

**6. Kérdés:**
| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés |
| :------ | :------ | :-------- | :-------- | :---------- | :------ | :-------- | :--------- |
| 1       | Allow   | TCP       | Any       | Any         | 192.168.60.250 | 80, 443 | Külső weboldal elérése |

**7. Kérdés:**
| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés |
| :------ | :------ | :-------- | :-------- | :---------- | :------ | :-------- | :--------- |
| 1       | Allow   | UDP       | 192.168.50.0/24 | Any         | Any     | 53      | Belső LAN DNS |
| 2       | Allow   | TCP       | 192.168.50.0/24 | Any         | Any     | 80, 443 | Belső LAN web |
| 3       | Deny    | Any       | 192.168.50.0/24 | Any         | Any     | Any     | Minden más tiltása kifelé |

**8. Kérdés:** A tűzfalszabályok sorrendje kritikus, mert a tűzfal a szabályokat **fentről lefelé** értékeli ki, és az **első egyező szabály alapján cselekszik**, majd leáll a kiértékeléssel.
**Példa:** Ha egy általános `Allow Any Any` szabály van egy specifikus `Deny HTTP forrás: x.x.x.x` szabály *előtt*, akkor a tiltott HTTP forgalom is átjutna, mert az `Allow` szabály előbb érvényesül. A `Deny` szabálynak kellene előbb lennie.

**9. Kérdés:** A **Port Forwarding (Porttovábbítás)** lényege, hogy egy külső IP-címen és porton érkező hálózati kérést egy belső hálózaton lévő gép (belső IP-cím) egy adott portjára irányít át. Erre azért van szükség a gyakorlati feladatban, mert a belső hálózaton (pl. DMZ-ben) lévő szerverek privát IP-címmel rendelkeznek, amelyek közvetlenül nem érhetők el az Internetről. A tűzfalon keresztül a porttovábbítás teszi lehetővé, hogy a külső felhasználók elérjék ezeket a belső szolgáltatásokat (pl. Publikus Webszerver).

**10. Kérdés:**
A **kulcscsere problémája** a szimmetrikus kriptográfiában az, hogy a kommunikáló feleknek valamilyen biztonságos módon meg kell osztaniuk egymással a titkos kulcsot, még mielőtt a titkosított kommunikáció megkezdődne. Ez gyakran bonyolult és kockázatos, különösen, ha a felek fizikailag távol vannak egymástól, vagy ha sok szereplő vesz részt a kommunikációban (minden párnak egyedi kulcs kell).
Az **aszimmetrikus kulcsú titkosítás** ezt úgy küszöböli ki, hogy mindenki nyilvánosságra hozhatja a titkosításhoz használt nyilvános kulcsát. Bárki titkosíthat üzenetet ezzel a nyilvános kulccsal, de csak a kulcs tulajdonosa (aki ismeri a titkos kulcsot) tudja azt dekódolni. Így nincs szükség titkos kulcsok előzetes biztonságos megosztására.
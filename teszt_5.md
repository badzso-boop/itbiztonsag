# 5. Hét: Ellenőrző Teszt - Felhasználók azonosítása, Jelszókezelés, DMZ és VPN

Ez a teszt az 5. heti "Felhasználók azonosítása, Jelszókezelés, DMZ és VPN" tananyagra épül. Válaszaidat az összefoglaló és a tananyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (Azonosítási Módok)**

Sorold fel a felhasználói azonosítás három alapvető módját, és mindegyikhez nevezz meg egy-egy példát, valamint egy előnyét és hátrányát!

Megoldas: 1. Tudas alapu -> jelszo A biztonsagos jelszavak nehezen megjegyezhetok, viszont univerzalisan barhol lehet hasznalni 2. Birtok alapu -> kulcs hatrany el lehet hagyni viszont elony ha ellopjak hamar eszre lehet venni es le lehet tiltani 3. Biometrikus -> ujjlenyomat a legbiztonsagosabb viszont draga a megvalositasa

---

**2. Kérdés (Jelszavak Problémái)**

Miért jelent a felhasználók jelszóval kapcsolatos gyakori szokása (pl. jelszó-újrahasznosítás, gyenge jelszavak) komoly biztonsági kockázatot? Említs meg legalább két ilyen problémás szokást!

Megoldas: Ha egy jelszo nem tul bonyolult akkor akar brute forceval is konnyen feltorheto. Foleg ha hetkoznapi szavakat is hasznalnak benne. Valamint pishingel vagy social engineeringgel is konnyen kinyerheto

---

**3. Kérdés (Jelszótárolás)**

Miért javasolt a jelszavakat **hash-elve és sózva (salted hash)** tárolni `plain-text` vagy `titkosított` formában történő tárolás helyett? Magyarázd el röviden a salted hash lényegét!

Megoldas: Mert a plain textet ha feltorik egybol megkapjak a szelszavakat a hasheles elve azt segiti elo hogy a jelszot mi alapbol sosem taroljuk csak a hashelt reszet ezzel ha feltorik akkor sem lehet kitalalni a sozva az egy plusz biztonsag, hisz azt csak a fejleszto tudja mit tesz hozza a felhasznalo es a betoro sem igy plusz biztositast adva

---

**4. Kérdés (Erős Jelszó)**

Milyen kritériumoknak kell megfelelnie egy "erős" jelszónak? Említs meg legalább hármat!

Megoldas: 8-12 karakter. Kis es nagy betu szam kulonleges karakter es nem letezo szo vagy olyan szo ami kapcsolodik a felhasznalohoz

---

**5. Kérdés (DMZ Célja)**

Mi a **DMZ (Demilitarizált Zóna)** elsődleges célja egy hálózatban, és milyen típusú szervereket szokás ide elhelyezni?

Megoldas: Ez egy plusz vedelmi fal, ha valaki a dmz-ben levo szervereket feltori akkor sem tud bemenni a belso halozatba hiszen az kulon van. Ezek a legerzekenyebbek a feltoresre, hiszen ezek elerhetok az internet szamara

---

**6. Kérdés (VPN Használat)**

Egy vállalat alkalmazottai otthonról szeretnének biztonságosan hozzáférni a belső hálózaton lévő privát szolgáltatásokhoz. Milyen technológiát javasolnál erre, és miért?

Megoldas: A vpn erre tokeletes hiszen virtualisan letrehoz egy privat halozatot es ez olyan mintha az otthonrol dolgozo kollega ott lenne szemelyesen es igy eleri a belso halozatot. Ez azert is jo mert a vpn titkositva van igy az interneten keresztul barhonnan biztonsagosan el lehet erni

---

**7. Kérdés (Tűzfalszabály írása - DMZ-ből a Belső LAN felé)**

A hálózati topológia alapján a `Publikus Webszerver` (`192.168.60.250` a DMZ-ben) gyakran kommunikál a `Belső Szolgáltatásszerverrel` (`192.168.50.240` a Belső LAN-ban) adatbázis hozzáférés céljából, a `TCP 3306` porton. Minden más forgalmat a DMZ-ből a Belső LAN felé tiltani kell.

Írj egy tűzfalszabályt, amely engedélyezi ezt a specifikus adatbázis forgalmat! (Formátum: Sorrend, Művelet, Protokoll, Forrás IP, Forrás port, Cél IP, Cél port, Megjegyzés)

Megoldas: 
| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés
| 1. | allow | TCP | 192.168.60.250 | 3306 | 192.168.50.240 | 3306 | az adatbazis kapcsolat engedelyezese
| 2. | deny | any | 192.168.60.250 | any | 192.168.50.0/24 | any | minden mast tiltunk
 
---

**8. Kérdés (Tűzfalszabály írása - VPN felhasználók hozzáférése)**

A VPN kapcsolatok a tűzfal WAN interfészén keresztül épülnek fel, és a VPN-en csatlakozó felhasználók hozzáférést kapnak a Belső LAN-hoz. A `Belső Szolgáltatásszerveren` (`192.168.50.240`) fut egy belső alkalmazás a `TCP 2020` porton, amelyet a VPN felhasználóknak el kell érniük. Az összes többi Belső LAN felé irányuló forgalmat a VPN felől tiltani kell.

Írj egy tűzfalszabályt, amely engedélyezi ezt a belső alkalmazás elérést a VPN felhasználók számára! (Tételezzük fel, hogy a VPN kapcsolat létrejötte után a forgalom "VPN interfészről" érkezik a tűzfalra.)

Megoldas: 

| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés
| 1. | allow | TCP | wan | 2020 | 192.168.50.240 | 2020 | engedelyezes a belso szerver eleresehez

---

**9. Kérdés (Jelszótörő Módszerek)**

Mi a különbség a **Brute Force** és a **Szótár alapú** jelszótörő támadások között? Melyik a hatékonyabb általában, és miért?

Megoldas: 
A brute force egy oriasi poolbol csak probalgatja egymas utan a jelszavakat es ha bejut akkor sikeres. Ez altalaban hosszu es eroforras igenyes feladat es gyakran nincs is vegeredmenye
Szotar alapu: Elore osszeallitott szavak es szotoredekek probalgatasa

---

**10. Kérdés (Azonosítási Módok Kombinálása)**

Miért gyengíti a biztonságot az azonosítási módszerek "rossz" kombinálása? Adj egy példát a tananyagból egy ilyen rossz kombinációra, és magyarázd el, miért problémás!

Megoldas: Peldaul egy eros jelszohoz kotnek egy kep alapu arcfelismerest amit konnyen ki lehet jatszani egy sima fotoval.

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
1.  **Tudás alapú (pl. jelszó):**
    *   *Példa:* Jelszó, PIN-kód.
    *   *Előny:* Egyszerű, olcsó.
    *   *Hátrány:* Könnyen elfelejthető, lehallgatható, kitalálható.
2.  **Birtok alapú (pl. kulcs):**
    *   *Példa:* Mágneskártya, token, OTP eszköz.
    *   *Előny:* Fizikai birtokláshoz kötött, lopás érzékelhető.
    *   *Hátrány:* Elveszthető, ellopható, másolható (bizonyos típusoknál).
3.  **Biometrián alapuló (pl. ujjlenyomat):**
    *   *Példa:* Ujjlenyomat, íriszszkennelés, arcfelismerés.
    *   *Előny:* Nehéz hamisítani, kényelmes (jelszómentes).
    *   *Hátrány:* Drága, adatvédelmi aggályok, hamis pozitív/negatív arány, egyedi jellemző elvesztése végleges probléma.

**2. Kérdés:**
A felhasználók gyakori problémás jelszóhasználati szokásai:
1.  **Jelszó-újrahasznosítás**: Ugyanazt a jelszót több szolgáltatásnál is használják. Ha egy adatbázis kompromittálódik, az összes többi fiókjuk is veszélybe kerül.
2.  **Gyenge, könnyen kitalálható jelszavak**: Egyszerű szavak, személyes adatok, dátumok használata, amelyek könnyen feltörhetők szótár- vagy Brute Force támadásokkal.

**3. Kérdés:**
A jelszavakat **hash-elve és sózva** javasolt tárolni a `plain-text` vagy `titkosított` formában történő tárolás helyett, mert:
-   **Plain-text**: Kompromittálás esetén azonnal hozzáférhetővé válnak az összes jelszó.
-   **Titkosított**: Bár védettebb, a visszafejtéshez szükséges kulcs tárolása problémás, és a kulcs megszerzése esetén a jelszavak ismét olvashatóvá válnak.
-   **Hash-elve és sózva**: A hash egy egyirányú függvény, nem fejthető vissza. A "só" egy véletlen érték, amelyet a jelszóhoz fűznek hash-elés előtt, így azonos jelszavakhoz is különböző hash értékek tartoznak. Ez megnehezíti a szótár- és szivárványtábla-támadásokat, és még egy adatbázis kompromittálása esetén is időigényes a jelszavak megfejtése.

**4. Kérdés:**
Egy "erős" jelszó jellemzői:
-   Minimum 8-12 karakter hosszú (minél hosszabb, annál jobb).
-   Tartalmaz nagy- és kisbetűket, számokat és speciális karaktereket.
-   Nem tartalmaz hétköznapi szavakat, szótöredékeket vagy személyes adatokat.
-   Minden hozzáféréshez (szolgáltatáshoz) egyedi, más jelszót használunk.
-   Időnként megváltoztatjuk.

**5. Kérdés:**
A **DMZ (Demilitarizált Zóna)** elsődleges célja, hogy egy kontrollált átmeneti zónát hozzon létre a külső, nem megbízható hálózat (Internet) és a belső, megbízható hálózat között. A DMZ-ben olyan szervereket helyeznek el, amelyeknek kívülről is elérhetőnek kell lenniük (pl. web-, mail-, DNS szerverek, FTP). Ezáltal, ha egy DMZ-ben lévő szerver kompromittálódik, a támadó nem jut be közvetlenül a belső hálózatba.

**6. Kérdés:**
Erre a célra a **VPN (Virtual Private Network)** technológiát javasolnám. A VPN egy titkosított "alagutat" hoz létre a felhasználó számítógépe és a vállalati hálózat között a nyilvános Interneten keresztül. Ez biztosítja, hogy a távoli felhasználó biztonságosan, titkosított csatornán keresztül érheti el a belső hálózati erőforrásokat, mintha fizikailag is a cégnél lenne.

**7. Kérdés:**
| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés |
| :------ | :------ | :-------- | :-------- | :---------- | :------ | :-------- | :--------- |
| 1       | Allow   | TCP       | 192.168.60.250 | Any         | 192.168.50.240 | 3306 | Webszerver adatbázis hozzáférés |
| 2       | Deny    | Any       | 192.168.60.0/24 | Any         | 192.168.50.0/24 | Any     | Minden más forgalom tiltása DMZ -> LAN |

**8. Kérdés:**
| Sorrend | Művelet | Protokoll | Forrás IP | Forrás port | Cél IP | Cél port | Megjegyzés |
| :------ | :------ | :-------- | :-------- | :---------- | :------ | :-------- | :--------- |
| 1       | Allow   | TCP       | VPN_Interface_IP_Range | Any         | 192.168.50.240 | 2020    | VPN felhasználó applikáció elérés |
| 2       | Deny    | Any       | VPN_Interface_IP_Range | Any         | 192.168.50.0/24 | Any     | Minden más VPN -> LAN forgalom tiltása |
*(Megjegyzés: a VPN_Interface_IP_Range a VPN klienseknek kiosztott IP tartományt jelöli, ami a tűzfalon "VPN interfészként" jelenik meg.)*

**9. Kérdés:**
-   **Brute Force (nyers erő)**: Szisztematikusan, az összes lehetséges karakterkombinációt végigpróbálja, amíg meg nem találja a helyes jelszót. Időigénye a jelszó hosszával és komplexitásával exponenciálisan nő.
-   **Szótár alapú támadás**: Előre összeállított szavakat, szótöredékeket, gyakori jelszavakat próbálgat el. Sokkal gyorsabb lehet, ha a jelszó szerepel a szótárban, de nem találja meg azokat a jelszavakat, amelyek nem részei a szótárnak.
A **szótár alapú** támadás általában hatékonyabb és gyorsabb a gyakori, gyenge jelszavak ellen, míg a Brute Force minden jelszót feltörhet elvileg, de sokkal több időt igényel.

**10. Kérdés:**
A "rossz" kombinálás egy példája a mágneskártya és PIN-kód együttes használata, ha a PIN-kódot a mágneskártyán tárolják. Ez azért problémás, mert ha a támadó megszerzi a kártyát, azonnal megkapja a PIN-kódot is, így a két azonosítási faktor nemhogy erősítené, hanem gyengítené egymást, mivel egyetlen ponton (a kártyán) mindkét faktor kompromittálódik. Az azonosítási faktoroknak függetleneknek kell lenniük egymástól.
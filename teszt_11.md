# 11. Hét: Ellenőrző Teszt - Webalkalmazások Biztonsága és AppScan Tesztelés

Ez a teszt a 11. heti "Webalkalmazások Biztonsága és AppScan Tesztelés" tananyagra épül. Válaszaidat az összefoglaló és a tananyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (Webalkalmazások Sérülékenységei)**

Miért váltak a webalkalmazások a támadók elsődleges célpontjává, és hol található a legtöbb biztonsági hiba egy átlagos alkalmazásban?

---

**2. Kérdés (Cross-Site Scripting - XSS)**

Mi az a **Cross-Site Scripting (XSS)** támadás? Hogyan működik (röviden), és milyen típusú károkat okozhat (adj egy példát)?

---

**3. Kérdés (SQL Injection)**

Mi az **SQL Injection** támadás lényege? Milyen hibákat használnak ki a fejlesztők oldalán, és milyen védelmi intézkedést kell alkalmazni ellene?

---

**4. Kérdés (Buffer Overflow)**

Definiáld a **Puffer Túlcsordulás (Buffer Overflow)** fogalmát! Hogyan tudja egy támadó kihasználni ezt a sérülékenységet, és mi lehet a következménye?

---

**5. Kérdés (Információszivárgás)**

Hogyan tud egy támadó a webalkalmazásokban előforduló **információszivárgásból** hasznos adatokat gyűjteni a rendszerről? Adj egy konkrét példát a tananyag alapján!

---

**6. Kérdés (Beviteli Ellenőrzés)**

Miért kritikus biztonsági hiba a **nem megfelelő beviteli ellenőrzés (Unvalidated Input)** egy webalkalmazásban? Milyen típusú ellenőrzésre nem szabad támaszkodni?

---

**7. Kérdés (AppScan Célja és Működése)**

Mi az **IBM Rational AppScan** elsődleges célja a webalkalmazások biztonsági tesztelésében? Hogyan működik alapvetően egy automatikus scan?

---

**8. Kérdés (AppScan Policy-k)**

Nevezz meg legalább két AppScan-ben elérhető **előre definiált policy-t**, és röviden magyarázd el a céljukat!

---

**9. Kérdés (AppScan Információgyűjtés)**

Az AppScan (vagy egy támadó) a felderítőfázisban milyen típusú információkat tud megállapítani egy webalkalmazásról a tananyag szerint? Sorolj fel legalább hármat!

---

**10. Kérdés (Webszerver Oldali Védelem)**

Sorolj fel legalább három olyan biztonsági intézkedést, amelyet a **webszerver oldalán** kell implementálni a webalkalmazás biztonságának növelése érdekében!

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
A webalkalmazások azért váltak a támadók elsődleges célpontjává, mert a hálózati és operációs rendszeri szintű védelmek fejlődésével a támadók ide irányították figyelmüket. A statisztikák szerint a biztonsági hibák 92%-a az alkalmazásrétegben található, és a hacker támadások 75%-a ebből a rétegből indul ki.

**2. Kérdés:**
A **Cross-Site Scripting (XSS)** támadás lényege, hogy a támadó kártékony JavaScript kódot injektál egy weboldalra, amit a felhasználó böngészője lefuttat.
*   **Működés**: A kód futtatásával a támadó hozzáférhet a felhasználó session cookie-jaihoz, ami lehetővé teszi, hogy eltérítse a munkamenetét, vagy a felhasználó nevében végezzen műveleteket.
*   **Kár**: Például a felhasználó session cookie-jainak ellopása.

**3. Kérdés:**
Az **SQL Injection** támadás lényege, hogy a támadó SQL parancsokat juttat be egy webalkalmazás beviteli mezőin keresztül (pl. felhasználónév, jelszó mező) az adatbázisba.
*   **Kihasznált hiba**: A fejlesztők nem ellenőrzik megfelelően a felhasználói beviteli paramétereket, és azokat vakon továbbítják az SQL API-nak.
*   **Védelem**: Szerver oldali beviteli ellenőrzés, parametrizált lekérdezések használata (prepared statements), és adatbázis hibaüzenetek elrejtése a kliens elől.

**4. Kérdés:**
A **Puffer Túlcsordulás (Buffer Overflow)** akkor következik be, amikor egy program megpróbál egy számára lefoglalt ideiglenes memóriaterületre (pufferre) a méreténél nagyobb adatot írni.
*   **Kihasználás**: A támadó a puffer utáni memóriaterületre írva adatokat (nem tudni, milyeneket) tud módosítani.
*   **Következmény**: Az alkalmazás összeomolhat, vagy a támadó saját kódot futtathat a rendszeren, ezzel hozzáférést szerezve.

**5. Kérdés:**
Egy támadó a webalkalmazásokban előforduló **információszivárgásból** úgy tud hasznos adatokat gyűjteni, hogy például a nem megfelelően kezelt hibaüzenetekből (adatbázis hibaüzenetek, függvényhívások) információkat szerez az operációs rendszerről, annak verziójáról, a rendszeren futó alkalmazásokról, azok verzióiról, vagy a fájlrendszer struktúrájáról (pl. `/etc/passwd` elérési útja).

**6. Kérdés:**
A **nem megfelelő beviteli ellenőrzés (Unvalidated Input)** kritikus biztonsági hiba, mert a webfejlesztők a felhasználó által adott paraméterek ellenőrzését a kliens böngészőjére bízzák, vagy egyáltalán nem ellenőrzik. A támadó a kliens oldali ellenőrzéseket könnyedén megkerülve rosszindulatú adatokat juttathat a szerverre, aminek következtében a rendszer nem kezeli megfelelően a helytelen értékeket, és ez sérülékenységekhez vezethet.

**7. Kérdés:**
Az **IBM Rational AppScan** elsődleges célja a webalkalmazások biztonsági tesztelésében a potenciális sérülékenységek automatizált és kézi módszerekkel történő felderítése, azonosítása és jelentése. Egy automatikus scan alapvetően végigjárja az oldalt, felderíti annak struktúráját, majd különböző paraméterekkel meghívja az alkalmazást, és a válaszüzenetek alapján elemzi, hogy tartalmaznak-e problémára utaló jeleket.

**8. Kérdés:**
1.  **Default Policy**: Minden tesztet tartalmaz, kivéve az invazív és a portfigyelő teszteket (out-of-band metódusú SQL injection teszteléséhez).
2.  **Application Only Policy**: Kizárólag az alkalmazásszintű teszteket futtatja.
3.  **Infrastructure Only Policy**: Csak az infrastruktúra teszteket futtatja.
4.  **Invasive Tests**: Kiszűrten azokat a teszteket tartalmazza, amelyek a szerver stabilitását érinthetik.

**9. Kérdés:**
A felderítőfázisban egy behatolástesztelő (vagy az AppScan) a webalkalmazásról a következő típusú információkat gyűjtheti:
1.  **Platform és technológiák**: Pl. .NET, Java, IIS, Apache, Windows, Linux, adatbázis típusa (MS SQL, Access).
2.  **Webszerver és alkalmazás verziója**: Pontos verziószámok.
3.  **Autentikáció típusa**: Pl. Form alapú, HTTP alapú, NTLM.
4.  **URL-struktúra, elérési útvonalak**: Adminisztrátori portál elérhetősége.
5.  **Hibaüzenetekből kinyerhető információk**: Rendszerszintű hibaüzenetek (adatbázis, fájlrendszer).

**10. Kérdés:**
1.  **Megfelelő beviteli ellenőrzés és validáció**: Minden felhasználói bevitelt szigorúan ellenőrizni és validálni kell szerver oldalon, mielőtt feldolgoznánk (pl. speciális karakterek szűrése, típusellenőrzés, hosszellenőrzés).
2.  **Részletes hibaüzenetek letiltása**: Ne jelenítsünk meg részletes, rendszerszintű hibaüzeneteket a kliensnek, helyette általános, felhasználóbarát üzeneteket adjunk vissza.
3.  **Kártékony kód (pl. `<script>`, `<object>`, `<embed>`) szűrése**: Ha nem feltétlenül szükséges, ezeket az elemeket távolítsuk el a webszerverre érkező adatokból, vagy a kimenő oldalon HTML entitásokra alakítsuk.
4.  **Viszonyazonosítás (CSRF token)**: Használjunk CSRF tokeneket az űrlapokban, hogy megakadályozzuk a Cross-Site Request Forgery (CSRF) támadásokat.
5.  **Biztonságos HTTP fejlécek**: Pl. X-XSS-Protection, Content-Security-Policy.
6.  **Frissítések és patchek**: A webszerver szoftverét és az operációs rendszert rendszeresen frissíteni kell.

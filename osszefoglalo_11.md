# 11. Hét: Webalkalmazások Biztonsága és AppScan Tesztelés - Összefoglaló

Ez a dokumentum a 11. heti tananyagot foglalja össze, amely a webalkalmazások biztonságának kihívásaival, a leggyakoribb támadási formákkal és az ellenük való védekezéssel, valamint az IBM Rational AppScan nevű eszköz alkalmazásával foglalkozik.

## I. Webalkalmazások Biztonsága

Az informatikai biztonsági intézkedések fejlődésével a támadók egyre inkább az alkalmazásrétegre fókuszálnak, mivel a hálózati és operációs rendszeri szintű védelmek fejlődtek. A statisztikák szerint a biztonsági hibák 92%-a az alkalmazásrétegben található, és a hacker támadások 75%-a ebből a rétegből indul.

### 1. Alapvető fejlesztési hibák

-   **Hibakezelés hiánya**: A hibakezelés hiánya információkat szivárogtathat ki a rendszerről (pl. PHP verzió, elérési útvonalak, adatbázis hibaüzenetek).
    -   *Megoldás*: Csak a létező, engedélyezett oldalak betöltése, URL paraméterek ellenőrzése, hibaüzenetek elrejtése a kliens elől.
-   **Nem megfelelő beviteli ellenőrzés**: A felhasználó által megadott paraméterek ellenőrzését a fejlesztők gyakran a kliens böngészőjére bízzák, vagy egyáltalán nem foglalkoznak vele.
    -   *Megoldás*: Szerver oldali beviteli ellenőrzés, speciális karakterek szűrése.
-   **Nem megfelelően védett oldalak**: Bejelentkezési funkció megkerülése (pl. közvetlen URL-lel), védett oldalak elérése hitelesítés nélkül.
    -   *Megoldás*: Minden védendő oldal elején ellenőrizni kell a bejelentkezett státuszt.
-   **Gyenge bejelentkezési mechanizmus**: A felhasználónév és jelszó egy lekérdezésben történő ellenőrzése, vagy az adminisztrátor első bejegyzésként való tárolása a felhasználókat tartalmazó táblában.
    -   *Megoldás*: Felhasználónév és jelszó külön ellenőrzése, SQL Injection ellen védekezés, adminisztrátor fiók nem első bejegyzésként.

### 2. Leggyakoribb támadási formák (Webalkalmazások ellen)

-   **Cross-Site Scripting (XSS)**: Kártékony JavaScript kód bejuttatása egy weboldalba.
    -   *Működés*: A böngésző lefuttatja a kódot, ami adathalászathoz (pl. cookie-k kinyerése), munkamenet eltérítéshez vezethet.
    -   *Védekezés*: Bejövő és kimenő adatok szűrése (HTML entitásokra alakítás), speciális karakterek szűrése.
-   **Információszivárgás**: A rendszerre vagy az alkalmazásra vonatkozó bizalmas információk kinyerése (pl. hibaüzenetekből, URL-ekből).
    -   *Példa*: Operációs rendszer, szerver verziója, fájlelérési utak, adatbázis hibakódok.
    -   *Védekezés*: Részletes hibaüzenetek letiltása a kliens oldalon, csak általános üzenetek megjelenítése.
-   **SQL Injection**: SQL parancsok bejuttatása beviteli mezőkön keresztül az adatbázisba.
    -   *Működés*: Adatbázis rekordok feltöltése, törlése, módosítása, információk kinyerése.
    -   *Védekezés*: Szerver oldali beviteli ellenőrzés, parametrizált lekérdezések használata, adatbázis hibaüzenetek elrejtése.
-   **Beviteli korlátozások megkerülése (Unvalidated Input)**: A kliens oldali ellenőrzések megkerülése.
    -   *Működés*: Hibás vagy rosszindulatú adatok juttatása a szerverre.
    -   *Védekezés*: Soha ne bízzunk a kliens oldali ellenőrzésben, mindig végezzünk szerver oldali validációt.
-   **Puffer túlcsordulás (Buffer Overflow)**: Egy pufferbe a számára lefoglaltnál több adat írása.
    -   *Működés*: Az alkalmazás összeomolhat, vagy a támadó kódot futtathat a rendszeren.
-   **Váratlan kód kombináció**: Ártatlannak tűnő parancsok kombinálásával programok befolyásolása.
-   **Szolgáltatásmegtagadási támadás (DoS)**: A szolgáltatás elérhetetlenné tétele túlterheléssel.

### 3. Védekezési Intézkedések (Webalkalmazások ellen)

-   **Böngésző oldalán**:
    -   Scriptek automatikus futtatásának letiltása.
    -   Linkek tartalmának és forrásának ellenőrzése kattintás előtt.
-   **Webszerver oldaláról**:
    -   Minimális adatbekérés, korlátozás.
    -   Böngészőnek visszaküldött adatok felső korlátjának beállítása.
    -   Beágyazott scriptek, objektumok szűrése (ha nem szükségesek).
    -   Csak HTTP POST kérések elfogadása adatbevitelre.
    -   Sütik tartalmának ellenőrzése.
    -   Viszonyazonosítás (pl. CSRF token).
    -   Meghatározott kódolás használata a weboldalon.
    -   Speciális karakterek szűrése a bejövő és kimenő adatokból.

## II. IBM Rational AppScan Tesztelés

Az IBM Rational AppScan egy webalkalmazás biztonsági tesztelő eszköz, amely automatizált és kézi technikákkal keresi a sérülékenységeket.

### 1. Felderítőfázis (Information Gathering)

-   Kézi és automatizált technikákkal gyűjt információt a rendszerről (pl. alkalmazási oldalak, HTTP fejléc, hibaüzenetek, szerver verziója, autentikáció típusa).
-   Példa: A `demo.testfire.net` oldalon a támadó megállapíthatja, hogy `.NET` alkalmazás, `IIS` webszerverrel, `form alapú` autentikációval, és `MS SQL` adatbázist használ.

### 2. Alkalmazás Sérülékenységének Keresése

-   **XSS (Cookie kinyerés)**: Az XSS sérülékenység kihasználásával (script injektálás) kinyerhetők a felhasználói munkamenet cookie-k, amelyekkel a támadó munkamenetet eltéríthet.
-   **Adminisztrátori portál feltörése**: Erőteljes böngészéssel és információszivárgással (pl. forráskódból talált jelszó) próbál belépni az adminisztrátori felületre.

### 3. AppScan Konfigurálás és Működés

-   **Scan konfigurálása**: URL és szerverek beállítása, bejelentkezési menedzsment (felhasználónév/jelszó, kétfaktoros hitelesítés, NTLM, HTTP), tesztelési policy-k kiválasztása.
-   **Policy-k**: Előre definiált szabályrendszerek a tesztelésre (pl. Default Policy, Infrastructure Only, Application Only, Invasive Tests, Complete).
-   **Scan indítása**: Teljes automatikus scan, vagy automatikus/manuális felderítés utáni tesztelés.
-   **Eredmények**: Az AppScan GUI-n keresztül megtekinthetők a biztonsági problémák (Security Issues), a javítási javaslatok (Remediation Tasks) és az alkalmazás adatai (Application Data).
-   **Riportok**: Összegző jelentések (Executive Summary, Detailed Report), szabványoknak való megfelelőségi riportok (Industry Standard Report, Regulatory Compliance Report), Delta Analysis (két scan összehasonlítása).
-   **Funkciók**: Brute force eszközök, cookie analizátor, SQL Injection, integráció AMP-vel (Assessment Management Platform) és TestDirectorral.

# 5. Hét: Felhasználók azonosítása, Jelszókezelés, DMZ és VPN - Összefoglaló

Ez a dokumentum az 5. heti tananyagot foglalja össze, amely két fő témakört ölel fel: a felhasználók azonosításának módjait és a jelszókezelés problémáit, valamint a tűzfalakkal kapcsolatos DMZ és VPN gyakorlatot.

## I. Felhasználók Azonosítása és Jelszókezelés

A felhasználók azonosítása (autentikáció) kritikus fontosságú a rendszerek biztonsága szempontjából. Három alapvető azonosítási módszer létezik:

### 1. Tudás alapú azonosítás (pl. jelszó)

-   **Előnyök**: Egyszerű, olcsó, könnyen használható.
-   **Hátrányok**: Észrevétlenül másolható, eltulajdonítható (leolvasható, kicsalható, kitalálható). Nehéz erős jelszavakat megjegyezni.

### 2. Birtok alapú azonosítás (pl. kulcs, token, chipkártya)

-   **Előnyök**: Általában egyszerű használat, lopás esetén érzékelhető (letiltható a kulcs).
-   **Hátrányok**: Eltulajdonítható, védekezni kell a másolás ellen. Intelligens eszközök (kriptográfiai műveletekre képesek) drágábbak, de jobb másolásvédelmet nyújtanak.

### 3. Biometrián alapuló azonosítás (pl. ujjlenyomat, íriszszkennelés)

-   **Előnyök**: A felhasználó fizikai-biológiai tulajdonságán alapul, nehézkesebb, de nagyon megbízható azonosítás (a komoly megvalósítások).
-   **Hátrányok**: Drága a komoly megvalósítás, az egyszerűbbek könnyen kijátszhatók. Jogi és adatvédelmi problémák (pl. biometrikus adatok tárolása).

### Azonosítási Módszerek Kombinálása (Többfaktoros autentikáció)

-   A kellő biztonsághoz legalább két különböző, de független módszer egyidejű használata javasolt (pl. jelszó és token).
-   Rossz példa: Mágneskártya PIN-kóddal, ha a PIN a kártyán van tárolva.

### Jelszavak Problémái

-   **Jelszó incidensek**: Naponta több millió jelszó kerül nyilvánosságra. Ezek tárolási módja (plain-text, titkosított, hash-elt) befolyásolja a kockázatot.
-   **Felhasználói szokások**: Sok felhasználó kevés, gyenge jelszót használ több szolgáltatáshoz, ritkán cseréli.
-   **Erős jelszó**: Min. 8-12 karakter, nagy- és kisbetű, szám, speciális karakter, nem tartalmaz hétköznapi szavakat, személyes adatokat. Időnként változtatni kell, és minden hozzáférésnél legyen különböző.

### Jelszavak Tárolási Módjai és Verifikációja

1.  **Plain-text (titkosítás nélkül)**:
    -   **Előny**: Egyszerű és gyors implementáció.
    -   **Hátrány**: A legveszélyesebb. Rendszerkompromittálás esetén azonnal hozzáférhetővé válnak a jelszavak.
2.  **Titkosított jelszavak**:
    -   **Előny**: Illetéktelen hozzáférés esetén nem kompromittálódik azonnal.
    -   **Hátrány**: A kulcskezelés problémás. A titkosított jelszót vissza lehet fejteni.
3.  **Hash-elt jelszavak**:
    -   **Előny**: Egyirányú eljárás, a jelszót nem tároljuk, hanem csak a hash értékét. Nem fejthető vissza.
    -   **Hátrány**: Ütközések előfordulhatnak (két különböző jelszó ugyanazt a hash-t adja). Ezért a hash függvényeknek ütközés-ellenállónak kell lenniük.
    -   **Só (Salt)**: Egy véletlen karakterlánc, amit a jelszóhoz fűzünk a hash-elés előtt. Ez megnehezíti a szótár- és szivárványtábla-támadásokat.

### Jelszótörő Módszerek

-   **Brute Force (nyers erő)**: Szisztematikusan végigpróbálja az összes lehetséges kombinációt. Időigényes, a jelszó hosszától és komplexitásától függ.
-   **Szótár alapú támadás**: Előre összeállított szavak és szótöredékek próbálgatása. Gyorsabb, de nem mindig vezet eredményre.
-   **Jelszóadatbázis felhasználása**: Hozzáférnek a tárolt (hash-elt) jelszavakhoz, majd offline próbálják megfejteni (pl. Rainbow Table).
-   **Phishing**: Hamisított weboldalakkal vagy üzenetekkel kicsalják a jelszavakat.
-   **Keylogger**: Billentyűleütéseket rögzítő program, ami megszerzi a beírt jelszavakat.
-   **Jelszó kilesés (Shoulder Surfing)**: A jelszó leolvasása a képernyőről, vagy a felhasználó háta mögül.

## II. Tűzfalak: DMZ és VPN

A 4. heti gyakorlati feladat hálózati modelljének folytatása, ahol a DMZ és a VPN kialakítása kerül fókuszba.

### 1. DMZ (Demilitarizált Zóna) Kialakítása

-   **Cél**: A külső (Internet) és belső hálózat közötti biztonságos átmenet megteremtése. Ide kerülnek azok a szerverek, amelyek külső forgalmat bonyolítanak le (pl. web-, mail-, DNS szerverek).
-   **Előny**: Ha a DMZ-ben lévő szerver feltörésre kerül, a belső hálózat még védett marad.
-   **Kialakítás**: A tűzfalon külön interfésszel csatlakozik a DMZ alhálózat, és szigorú szabályokkal van elválasztva mind az Internet, mind a belső LAN felől.

### 2. VPN (Virtual Private Network) Kialakítása

A VPN egy titkosított "alagutat" hoz létre két hálózati pont között (pl. kliens és tűzfal), így egy nyilvános hálózaton (Internet) keresztül is biztonságos és privát kommunikáció valósítható meg.

-   **Cél**: Biztonságos távoli hozzáférés biztosítása belső szolgáltatásokhoz. A felhasználó (pl. otthonról dolgozó alkalmazott) úgy érheti el a belső hálózat erőforrásait, mintha fizikailag is ott lenne.
-   **Kialakítás**:
    -   **VPN szerver a tűzfalon**: A tűzfalon konfigurálunk egy VPN szervert, amely fogadja a bejövő VPN kapcsolatokat (általában a WAN interfészen).
    -   **Kliens oldali VPN beállítás**: A felhasználó gépére VPN kliens szoftvert telepítünk és konfigurálunk.
    -   **Forgalom:** A VPN alagúton átmenő forgalom titkosított, így az Interneten utazva is bizalmas marad.
-   **Előny**: Biztonságos távoli hozzáférés a privát szolgáltatásokhoz, bizalmas kommunikáció.

### 3. Tűzfalszabályok Beállítása

A DMZ és VPN kialakításával együtt a tűzfalszabályokat is módosítani kell:
-   **Külső szolgáltatások elérése**: Engedélyezni kell a szükséges forgalmat a WAN interfészről a DMZ-ben lévő szerverekre (pl. HTTP/HTTPS a Publikus Webszerverre), és minden mást tiltani. Ez történhet porttovábbítással is.
-   **DMZ és Belső hálózat közötti forgalom**: Szigorúan korlátozni kell a DMZ és a Belső LAN közötti forgalmat, csak a feltétlenül szükséges kommunikációt engedélyezve (pl. a Publikus Webszerver csak a Belső Szolgáltatásszervert érheti el az adatbázis miatt).
-   **VPN forgalom**: Engedélyezni kell a VPN kapcsolatok létrejöttét a WAN felől a tűzfal VPN szerverére, majd a VPN-en keresztül érkező forgalomnak a belső hálózat felé (pl. a Belső Szolgáltatásszerver felé) haladását is szabályozni kell. Általában csak a belső szerver és azon belül is csak speciális alkalmazás (pl. 2020-as port) elérése engedélyezett.

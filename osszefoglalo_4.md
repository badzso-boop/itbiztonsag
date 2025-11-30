# 4. Hét: Fejlettebb Kriptológia és Tűzfalak - Összefoglaló

Ez a dokumentum a 4. heti tananyagot foglalja össze, amely két fő témakört ölel fel: a fejlettebb kriptográfiai eljárásokat (aszimmetrikus kulcsú titkosítás, hash függvények, üzenethitelesítés, digitális aláírás), valamint a tűzfalak működését és alkalmazását.

## I. Aszimmetrikus (Nyilvános Kulcsú) Kriptográfia

Az aszimmetrikus kriptográfiában két különböző, de matematikailag összetartozó kulcspárt használunk: egy **nyilvános kulcsot (public key)** és egy **titkos kulcsot (private key)**.

-   **Alapötlet**: A kódoló és a dekódoló kulcs nem számítható ki könnyen egymásból. Olyan műveleteken alapul, amelyek egy irányban könnyen elvégezhetők, de visszafelé szinte lehetetlenek (pl. nagy prímek összeszorzása vs. faktorizálása).
-   **Előny**: A kódoló kulcs nyilvánosságra hozható, így nincs szükség titkos kulcscserére.
-   **Történet**: Az 1970-es évekig minden titkosítás szimmetrikus volt.
    -   1973: Clifford Cocks (GCHQ) kitalálta.
    -   1976: Diffie-Hellman kulcscsere protokoll.
    -   1977: Ron Rivest, Adi Shamir, Leonard Adleman bemutatja az **RSA algoritmust**.

### RSA Algoritmus

Az RSA (Rivest-Shamir-Adleman) a legismertebb aszimmetrikus kulcsú titkosítási algoritmus.

-   **Kulcsválasztás lépései**:
    1.  Válasszunk két nagy, különböző prím számot (`p` és `q`).
    2.  Számítsuk ki `N = p * q`. (N manapság ~1024-4096 bit).
    3.  Számítsuk ki `φ(N) = (p-1) * (q-1)` (Euler-függvény).
    4.  Válasszunk egy `e` (nyilvános kitevő, titkosítási kulcs) számot, ami relatív prím `φ(N)`-hez.
    5.  Számítsuk ki `d` (titkos kitevő, dekódolási kulcs) értékét úgy, hogy `e * d ≡ 1 (mod φ(N))`.
-   **Kulcsok**:
    -   **Nyilvános kulcs**: `(N, e)` – Ez adható ki bárkinek.
    -   **Titkos kulcs**: `(p, q, d)` – Ezt szigorúan titokban kell tartani.
-   **Kódolás**: `C = M^e mod N` (ahol `M` a nyílt üzenet, `C` a rejtett üzenet).
-   **Dekódolás**: `M = C^d mod N`.
-   **Biztonság**: A nagy számok faktorizálásának nehézségén alapul. Kvantumszámítógépek (Shor-algoritmus) jelentenek veszélyt rá.

### Elliptikus Görbe Kriptográfia (ECC)

-   Bonyolult matematikán alapul.
-   **Előnye**: Rövidebb kulcsokkal is hasonló biztonsági szintet nyújt, mint az RSA, ezért jobban illeszkedik kis kapacitású eszközökhöz (pl. okoskártyák).

## II. Hash Függvények (részletesebben)

A hash függvények olyan matematikai eljárások, amelyek tetszőleges hosszúságú bemenetből fix hosszúságú kimenetet (hash érték, lenyomat) generálnak. Fő céljuk az adatok **integritásának** biztosítása.

-   **Elvárások (kriptográfiai szempontból)**:
    1.  **Egyirányúság (One-Wayness / Preimage Resistance)**: A hash értékből szinte lehetetlen visszafejteni az eredeti bemenetet.
    2.  **Gyenge ütközés-ellenállóság (Second Preimage Resistance)**: Adott bemenethez (`x`) szinte lehetetlen találni egy másik bemenetet (`x'`), amelynek ugyanaz a hash értéke (`h(x) = h(x')`).
    3.  **Erős ütközés-ellenállóság (Collision Resistance)**: Szinte lehetetlen találni két tetszőleges, különböző bemenetet (`x` és `x'`), amelyeknek ugyanaz a hash értéke (`h(x) = h(x')`). Ez a legerősebb elvárás.
-   **Születésnapi Paradoxon**: Azt mondja ki, hogy egy `n` bites hash érték esetén már `2^(n/2)` próbálkozással valószínűleg találunk két olyan bemenetet, amelyek ugyanarra a hash értékre képződnek. Ezért fontos, hogy a hash függvények kimeneti mérete elég nagy legyen (pl. 128-160 bit vagy több, SHA-256 esetén 256 bit).
-   **Iteratív Hash Függvények (Merkle-Damgård konstrukció)**: A legtöbb hash függvény iteratív módon épül fel, egy kompressziós függvény ismételt alkalmazásával. Fontos, hogy az üzenet hossza is beletartozzon a számításba.
-   **Példák**: MD5 (már nem biztonságos), SHA-1 (már nem biztonságos), SHA-2 (SHA-256, SHA-512), SHA-3 (biztonságosnak számítanak).

## III. Üzenethitelesítés és Digitális Aláírás

-   **Cél**: Az üzenet **integritásának** (változatlanság) és a feladó **hitelességének** biztosítása, valamint a **letagadhatatlanság** megvalósítása.
-   **MAC (Message Authentication Code)**: Egy kriptográfiai ellenőrző összeg, ami egy titkos kulcsot is felhasznál. Ezzel biztosítható, hogy a támadó ne tudja módosított üzenethez kiszámolni a helyes MAC-et.
-   **Digitális aláírás**: Aszimmetrikus kulcsú kriptográfiát használ. A feladó a **titkos kulcsával** aláírja az üzenet hash értékét. Bárki ellenőrizheti az aláírást a feladó **nyilvános kulcsával**.
    -   **Előnye**: Hitelesítés, integritásvédelem és letagadhatatlanság (a feladó nem tagadhatja le, hogy ő írta alá az üzenetet).

## IV. Tűzfalak

A tűzfalak hálózati biztonsági eszközök, amelyek monitorozzák és ellenőrzik a bejövő és kimenő hálózati forgalmat előre meghatározott szabályok alapján. Céljuk, hogy megakadályozzák az illetéktelen hozzáférést a belső hálózatokhoz.

### 1. Hálózati Architektúra

A gyakorlati feladatban szereplő hálózati topológia a következő elemeket tartalmazza:
-   **Internet**: Külső hálózat.
-   **Tűzfal**: Elválasztó elem az Internet, a DMZ és a Belső LAN között.
-   **DMZ LAN (Demilitarizált Zóna)**: Külső hálózatról elérhető szolgáltatásokat (pl. `Publikus Webszerver`) tartalmazó alhálózat. `192.168.60.0/24`.
-   **Belső LAN (Internal LAN)**: Belső hálózati felhasználók (`Belső kliens`, `Belső szolgáltatásszerver`) és erőforrások alhálózata. `192.168.50.0/24`.
-   **Publikus Webszerver**: `192.168.60.250` (DMZ-ben) – kívülről elérhető weboldalt szolgáltat.
-   **Belső Szolgáltatásszerver**: `192.168.50.240` (Belső LAN-ban) – belső webalkalmazást futtat.
-   **Belső Kliens**: `192.168.50.10` (Belső LAN-ban) – a felhasználók gépe.

### 2. Tűzfal Működése

A tűzfal a szabálylisták alapján dönti el, hogy egy adott forgalom **átengedhető (Allow)** vagy **blokkolható (Deny)**. A szabályokat sorrendben, fentről lefelé értékeli ki, és az első egyező szabály alapján cselekszik.
-   **Tiltó szabály esetén**: `visszautasítás (reject)` (üzenetet küld a forrásnak) vagy `eldobás (drop)` (csendes eldobás).

### 3. Szabálylisták Típusai

-   **Blacklist (Feketelista)**: Alapértelmezésben mindent engedélyez, és csak a kifejezetten tiltott forgalmat blokkolja. Kisebb biztonsági szint.
-   **Whitelist (Fehérlista)**: Alapértelmezésben mindent blokkol, és csak a kifejezetten engedélyezett forgalmat engedi át. Magasabb biztonsági szint, de bonyolultabb kezelés.

### 4. Port Forwarding (Porttovábbítás)

Lehetővé teszi, hogy a külső hálózatról (Internet) érkező kéréseket a tűzfal egy belső hálózati címre és portra továbbítsa. Gyakran használják DMZ-ben lévő szerverek eléréséhez.
-   Példa: A külső `publikus_IP:80` kérés a DMZ-ben lévő `Publikus Webszerver:80` címre továbbítódik.

### 5. Jelenlegi állapot (Gyakorlatból)

-   **Internetelérés**: Kliensekről és szerverekről is van.
-   **Belső hálózati szolgáltatások**: Elérhetők.
-   **Problémák**:
    -   Kifelé minden mehet szűrés nélkül (Blacklist alapú kimenő forgalom, de nincs tiltó szabály).
    -   A publikus weboldal kívülről nem elérhető.
    -   A privát szolgáltatások otthonról nem elérhetők.
    -   Tűzfal admin felületének elérése problémás a külső elérés esetén.

### 6. Cél (Gyakorlatból)

-   Engedélyezett Internet felé publikálandó szolgáltatások: Web (HTTP, HTTPS), levelezés (IMAP, POP, SMTP), időlekérés (NTP). Minden más tiltása.
-   Ezen célok eléréséhez kell majd a tűzfalszabályokat konfigurálni.

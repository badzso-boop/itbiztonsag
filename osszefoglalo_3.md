# 3. Hét: Kriptológia Alapjai és Klasszikus Rejtjelek - Összefoglaló

Ez a dokumentum a 3. heti kriptológiai anyag (Ferenci Tamás Kriptológia előadás) alapfogalmait és a klasszikus rejtjeleket, valamint a gyakorlati feladatokban szereplő példákat foglalja össze.

## I. Alapfogalmak a Kriptológiában

-   **Kriptológia**: A titkos kommunikáció tudománya. Két fő ága van:
    -   **Kriptográfia**: A titkosítás módszereivel foglalkozik, azaz az üzenetek érthetetlenné tételével.
    -   **Kriptoanalízis**: A titkosított üzenetek megfejtésével, a titkosítás feltörésével foglalkozik.
-   **Nyílt szöveg (Plaintext)**: Az eredeti, olvasható üzenet.
-   **Rejtett szöveg (Ciphertext)**: A titkosított, olvashatatlan üzenet.
-   **Kulcs (Key)**: A titkosítási algoritmus működését befolyásoló titkos információ.

### A Támadás Fajtái
-   **Passzív támadás (Lehallgatás)**: A támadó csak figyeli a kommunikációt, de nem avatkozik be. Cél a **titkosítás** megtörése.
-   **Aktív támadás (Beavatkozás, Forgalom módosítása)**: A támadó módosítja az üzenetet vagy a kommunikációt. Cél az **integritásvédelem**, **hitelesítés** és **letagadhatatlanság** megtörése.

### Kerckhoffs-elv
A kriptográfia egyik alapelve. Kimondja, hogy egy kriptográfiai rendszer biztonságának a kulcson kell múlnia, nem pedig az algoritmus titkosságán. A támadó a kulcs kivételével mindent ismer.
-   **Okai**: Egyszerűbb a kis kulcsot titokban tartani, mint az algoritmust; könnyebb a kulcsot cserélni; könnyebben kiderülnek a hibák, ha nyílt az algoritmus.
-   **Ellentéte**: "Security by obscurity" (biztonság a homály révén), ami hibás megközelítés.

### Támadási Modellek
-   **Ciphertext only**: Csak a rejtett szöveg ismert.
-   **Known plaintext**: Ismert egy nyílt szöveg - rejtett szöveg páros.
-   **Chosen plaintext**: A támadó által választott nyílt szöveget titkosítjuk.
-   **Chosen ciphertext**: A támadó által választott rejtett szöveget dekódoljuk.
-   Ezek mellett léteznek **nem algoritmikus támadások** is, mint a Social Engineering vagy Side-channel attack.

## II. Szimmetrikus Kulcsú Rejtjelezés

Ugyanazt a kulcsot használjuk a titkosításhoz és a dekódoláshoz is.

### Kulcsfolyam rejtjelezők (Stream Ciphers)
-   Az OTP (One-Time Pad) logikájára épülnek, de pszeudovéletlen kulcsfolyamot használnak.
-   Bármilyen méretű üzenet titkosítható, mechanikailag is jól implementálható (pl. rotor cipher-ek).
-   **Probléma**: azonos kulcsok használata (pl. Lorenz feltörése).

### Blokk rejtjelezők (Block Ciphers)
A nyílt szöveget fix (általában 64 vagy 128 bit) blokkokra osztjuk, és minden blokkot önállóan titkosítunk.

-   **Szubsztitúciós (Helyettesítő) rejtjelek**: A karakterek pozíciója marad, de lecserélődnek.
    -   **Monoalfabetikus helyettesítés**: Egy adott betű mindig ugyanarra a betűre cserélődik (pl. Caesar kód).
        -   **Caesar kód**: Az angol ABC minden betűjét egy fix értékkel eltolva helyettesítjük.
            -   *Példa (gyakorlatból):* `CSAK FEHER` (kulcs: 4) -> `GWEODJILIV`
            -   *Feltörés*: Betűgyakoriság-elemzéssel könnyen feltörhető, mivel megőrzi a betűgyakoriságokat.
        -   **Affin rejtjelező**: A Caesar kód általánosítása (lineáris algebrai alapokkal), de szintén monoalfabetikus, tehát betűgyakoriság-elemzéssel támadható.
    -   **Polialfabetikus helyettesítés**: Egy adott betű nem mindig ugyanarra cserélődik.
        -   **Vigenère kód**: Egy kulcsszót ismétlünk a nyílt szöveg hossza alatt, és minden betűt az aktuális kulcsbetű alapján tolunk el (több Caesar-kód egymás után).
            -   *Példa (gyakorlatból):* `SARGA` (kulcs: `nik`) -> ...
            -   *Feltörés*: Fedi a betűgyakoriságokat, de nem tökéletesen (kulcsszó hossza periodikus). Kasiski- vagy Friedman-töréssel feltörhető.
        -   **Csoportos helyettesítés**: Randomizált ABC-t tartalmazó táblázatokkal dolgozik.
            -   *Példa (gyakorlatból):* `ZOLD` kulcs, táblázatból `ACC, CBB, BCA, CBC` visszafejtés.
-   **Transzpozíciós (Átrendező) rejtjelek**: A karakterek ugyanazok maradnak, csak a pozíciójuk cserélődik meg.
    -   **Egyszerű transzpozíció**: A szöveget blokkokra osztjuk, és minden blokkon belül egy permutáció szerint átrendezzük a karaktereket. Kulcstér mérete `t!`.
    -   **Oszlop-transzpozíciós rejtjelező**: Egy kulcsszó (pl. ZEBRAS) betűinek ábécé sorrendje határozza meg az oszlopok olvasási sorrendjét.
    -   **Kétszeres alkalmazása**: Az '50-es évekig az egyik legjobb "papír-ceruza" rejtjelnek számított.
        -   *Példa (gyakorlatból):* Titkosítandó: `KEK` (kulcs: `4123`, kiegészítő karakter: `_`) -> ...
-   **Shannon keverő transzformációja (Confusion/Diffusion)**:
    -   Célja a titkosítandó szöveg és a kulcs közötti statisztikai kapcsolat elrejtése (confusion), illetve a nyílt szöveg egy bitjének változása az egész rejtett szövegre terjedjen ki (diffusion).
    -   *Példa (gyakorlatból):* `PIROS` (kulcs elt: 3, k1: 312, k2: 321, ciklus: 2) -> ...

## III. Blokk-rejtjelezési Módok (Block Cipher Modes)

A blokk-rejtjelezők (pl. AES) önmagukban csak fix méretű blokkokat tudnak titkosítani. Azonban az üzenetek általában hosszabbak. Erre szolgálnak a blokk-rejtjelezési módok, amelyekkel hosszabb üzenetek titkosíthatók, láncolva az egyes blokkok titkosítását.

-   **ECB (Electronic Code Book)**:
    -   A blokkokat egymástól függetlenül titkosítjuk.
    -   **Biztonság**: Gyenge. Azonos nyílt blokkokból azonos rejtett blokkok lesznek, ami felfedi a mintázatokat (replay attack). Felcserélhetők a rejtett blokkok.
    -   **Hatékonyság**: Párhuzamosítható a kódolás/dekódolás, véletlen hozzáférés is lehetséges.
    -   **Hibaterjedés**: Egy bitcsere csak az adott blokkot érinti, kerethiba az összes rákövetkezőt.
-   **CBC (Cipher Block Chaining)**:
    -   Minden nyílt blokk titkosítása előtt XOR-oljuk az előző rejtett blokkal. Az első blokkhoz egy **inicializációs vektor (IV)** kell.
    -   **Biztonság**: Jobb, mint az ECB. Azonos nyílt blokkokból eltérő rejtett blokkok jönnek létre. IV-t üzenetenként változtatni kell. Növelt entrópia.
    -   **Hatékonyság**: A kódolás nem, de a dekódolás párhuzamosítható.
    -   **Hibaterjedés**: Egy bithiba az adott és a következő blokkot is érinti.
-   **CFB (Cipher Feedback)**:
    -   Önszinkronizáló kulcsfolyamatos rejtjelezőként viselkedik. A blokk titkosítóját használja a kulcsfolyam generálásához.
    -   **IV**: Nyíltan is elküldhető.
    -   **Hibaterjedés**: Önszinkronizáló, N/S lépés után helyreáll a rendszer.
-   **OFB (Output Feedback)**:
    -   Szinkron, kulcsfolyamatos rejtjelező. A blokk titkosító kimenetét használja a következő kulcsfolyam blokk generálásához.
    -   **Cél**: átviteli hiba csak egy karaktert érintsen (zajos csatornáknál előnyös).
    -   **Hibaterjedés**: Egy bithibának "tökéletesen" ellenáll.
-   **CTR (Counter)**:
    -   Szinte mint az OFB, de shift-regiszter helyett egy számlálót használ a blokk titkosító bemenetén.
    -   **Hatékonyság**: Mind a kódolás, mind a dekódolás párhuzamosítható.
    -   **Hibaterjedés**: Mint az OFB.

### Üzenetkitöltés (Padding)
-   Szükséges, ha az utolsó blokk hossza nem éri el a blokk rejtjelező blokkméretét.
-   Fontos, hogy a vevő azonosítani tudja a kitöltést, és ha egyszer alkalmazunk kitöltést, mindig alkalmazni kell.

## IV. Hash Függvények (Bevezetés)

-   **Cél**: Integritásvédelem, hitelesítés, letagadhatatlanság.
-   **Fogalom**: Egy irányú függvény, ami tetszőleges hosszúságú bemenetből fix hosszúságú kimenetet (lenyomatot, hash értéket) generál.
-   **Elvárások**:
    -   **Egyirányúság**: Nehéz az ősképtérbeli elemet visszaállítani a hash értékből.
    -   **Ütközés-ellenállóság (Collision Resistance)**: Nehéz két különböző bemenetet találni, amelyeknek ugyanaz a hash értéke.
        -   **Gyenge ütközés-ellenállóság**: Adott `x` bemenethez nehéz `x'`-et találni, hogy `h(x) = h(x')`.
        -   **Erős ütközés-ellenállóság**: Nehéz találni bármely két `x` és `x'`-et, hogy `h(x) = h(x')`.
-   **Születésnapi paradoxon**: Azt mutatja be, hogy sokkal hamarabb találunk ütközést, mint gondolnánk (kb. `2^(n/2)` próbálkozás `n` bites hash esetén). Ezért a hash függvények kimenetének hossza legalább 128-160 bit kell legyen.
-   **Alkalmazások**: Jelszó-hash-elés (salt-tal), hitelesítés, Proof-of-Work.
-   **Példák**: MD5 (már feltörhető), SHA-1 (már feltörhető), SHA-2, SHA-3, BLAKE2 (elfogadhatóak).

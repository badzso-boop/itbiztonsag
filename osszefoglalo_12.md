# 12. Hét: Adatvédelem és Adatmentés - Összefoglaló

Ez a dokumentum a 12. heti tananyagot foglalja össze, amely az adatvédelem jogi, szervezeti és informatikai aspektusait, az adatbiztonság és titokvédelem fogalmait, valamint az adatmentés különböző típusait és gyakorlati rendjét tárgyalja.

## I. Adatvédelem

Az adatvédelem a személyes adatok gyűjtésének, feldolgozásának és felhasználásának korlátozását, az érintett személyek védelmét biztosító alapelvek, szabályok, eljárások, adatkezelési eszközök és módszerek összessége. Célja, hogy megvédje az egyének magánszféráját és kontrollt biztosítson adataik felett.

### 1. Adatvédelem fogalma és aspektusai

-   **Jogszabályi vonatkozások**: Törvények, jogszabályok, a megsértésük szankcionálása (pl. Keretjellegű Adatvédelmi törvény, szektorális/területspecifikus törvények).
-   **Szervezeti vonatkozások**: Belső szabályozás (adatvédelmi szabályzat), adatvédelmi felelős kinevezése és feladatai.
-   **Informatikai vonatkozások**: A személyes adatokat kezelő számítógépes rendszerek tervezése és működtetése.
-   **Gyakorlati adatkezelési vonatkozások**: Az adatkezelés mindennapi aspektusai.

### 2. Adatvédelmi Problémák

-   Az adatvédelmi előírások részletes lebontása az informatikai rendszer szintjéig gyakran hiányzik.
-   A személyes adatokat kezelő rendszerek tervezésénél és működtetésénél az adatvédelmi előírásokkal ellentétesen ható üzleti vagy igazgatási érdek dominálhat.

### 3. Adatbiztonság

Az adatok jogosulatlan megismerése, megszerzése, továbbítása, módosulása és tönkremenetele elleni intézkedések, valamint a hitelességük, integritásuk, bizalmasságuk és rendelkezésre állásuk biztosítása. Jogi és szabályozási vetületei is vannak, nemcsak műszaki és szervezési aspektusa.

### 4. Titokvédelem

Valamilyen "titok" (pl. üzleti titok, államtitok, orvosi titok, banktitok) védelme, megismerésének korlátozása.

### 5. Az Adatvédelem gyakorlati megvalósítása és GDPR

A szakirodalom szerint négy elvi lehetőség:
1.  **Jogi szabályozás**: Törvények, jogszabályok, szankcionálás.
    -   **Nemzetközi szinten**: Európa Tanács adatvédelmi egyezménye, EU adatvédelmi direktíva.
    -   **GDPR (General Data Protection Regulation)**: 2018. május 25-én lépett hatályba, униós adatvédelmi rendelet.
        -   **Teendők**: Adatkezelési nyilvántartás készítése, jogcímek (jogi kötelezettség, jogos érdek) meghatározása, adattisztítás, adatok biztonságának garantálása (technikai és szervezési intézkedésekkel).
        -   **Adatvédelmi incidens**: Bírságolási ok (pl. céges telefon elvesztése).
2.  **Önszabályozás**: Üzleti szektor belső szabályzatai, etikai kódexei.
3.  **Fejlett adatvédelmi technológiák (PET - Privacy Enhancing Technologies)**:
    -   Cél: Védik a felhasználók identitását (anonimitás, pszeudonimitás), erőforrások használatát, kommunikáció tényének megfigyelhetetlenségét.
    -   Biztosítják a személyes adatok bizalmasságát és integritását.
    -   Példák: Biometrikus rejtjelezés (bioscrypt), Chaum-féle Mix-ek, onion routing.
4.  **Oktatás**: Adatalanyok és informatikusok képzése.

### 6. Adatkezelési szabályzat

-   Rögzíti a cég dolgozóira és partnereire vonatkozó adatkezelési szabályokat.
-   Tiltja az adatok másolását, nyomtatását, e-mailben való küldését az ügyrendben meghatározottakon túl.
-   Illetéktelen külső hozzáférés tilos.
-   Távmunka során fokozottan ügyelni kell, adatmásolás a távoli gépre tilos.
-   Ideiglenes fájlok megsemmisítése.
-   Adatsérülés jelentése.
-   Szigorú szabályok a céges gépeken telepíthető programokra és az internetes forgalomra.

## II. Adatmentés

Az adatmentés (Data Backup) az adatok másolatának elkészítése, melyből bármilyen hiba (hardver, szoftver) esetén az adatok visszanyerhetők, és a munka minimális időveszteséggel folytatható.

### 1. Adatmentés okai és adatvesztés

-   **Okok**: Tervszerű, folyamatos mentés; funkcionális hardveregység hibája.
-   **Adatvesztés okai**: Fájlok törlése, vírus, korrupt fájlrendszer, áramkimaradás, elfelejtett jelszó, lemezproblémák, eltávolított/elérhetetlenné vált partíció, tűz/víz, rövidzárlat, mechanikai problémák.
-   **Leggyakoribb hibák**: Mechanikai (60%), logikai, elektronikai.

### 2. Adatmentés típusai

-   **Online mentés**: A diszk működik, miközben mentést készítünk róla.
-   **Offline mentés**: A fájlok olyan médiumon vannak tárolva, amit használat előtt csatlakoztatni kell.
-   **Teljes mentés**: Minden információt tartalmaz az adott diszkről (fájlokat, rendszerállapotot, registry adatbázist).
-   **Inkrementális mentés**: Az utóbbi mentés óta módosult fájlokat tartalmazza. Először teljes mentés, majd az inkrementumok sorban.
-   **Differenciális mentés**: A legutóbbi teljes mentés óta módosult adatokat tartalmazza.
-   **Szelektív mentés**: Csak bizonyos fájlokat tartalmaz (pl. dokumentumokat).

### 3. Hova mentsünk?

-   **Másodlagos merevlemez**: Belső vagy külső.
-   **ZIP és Szalagos meghajtó**: Népszerűek.
-   **Írható DVD és CD**.
-   **Beépített Compact Flash/SD/MMC/MS kártyaolvasó**: Kisebb adatokra.
-   **Magneto-optikai tárolók**.
-   **Hálózati mentés**: Központi szerverre.

### 4. A biztonsági adatmentés rendje

-   **Felelős személy**: Ki kell jelölni a mentésért felelős személyt.
-   **Adatok köre**: Minden cég számára fontos állományt be kell vonni.
-   **Gyakoriság**: Rendszeres időközönként, az adatok keletkezési ütemétől függően (napi, heti, havi).
-   **Generációk**: Mindig legyen több generációnk a mentésből (utolsó és utolsó előtti).
-   **Titkosítás**: A mentett adatokat célszerű titkosítani.
-   **Tárolás helye**: Ne a gépben tároljuk, a mentéseket biztonságos, külön helyen kell tárolni (páncélszekrényben, másik telephelyen).
-   **Ellenőrzés**: A mentéseket ellenőrizni kell (pl. külön helyre való visszatöltéssel).
-   **Megsemmisítés**: A már nem használt média (régi mentések) megsemmisítését is szabályozni kell.
-   **Munkaidőn kívüli automatikus mentés**: Ellenőrizni kell, hogy nem ütközik-e más programok futásával.

### 5. Gyakori adatkezelési hibák

-   Nincs adatkezelési szabályzat.
-   A használaton kívül kerülő gépeken fontos adatok maradnak.
-   Az adatkezelés nem a minőségirányítási rendszer része.
-   Nem minden fontos adat kerül be a mentésbe.
-   Nincs kijelölve a mentésért felelős személy.
-   A dolgozók nem tudják, mely mappák és fájlok kerülnek a mentésbe.

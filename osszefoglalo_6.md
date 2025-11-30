# 6. Hét: Programozott Kártevők és a Fenyegetések Fejlődése - Összefoglaló

Ez a dokumentum a 6. heti tananyagot foglalja össze, amely az informatikai kártevők (malware) fejlődésével, típusaival, terjedésével és az ellenük való védekezéssel foglalkozik.

## I. A Malware (Kártevő Szoftver) Fogalma és Típusai

A **malware** olyan szoftver, amelyet kifejezetten rosszindulatú célokra (pl. adatok lopása, rendszerek károsítása, illetéktelen hozzáférés) hoztak létre.

### Főbb Kategóriák:

1.  **Vírusok (Viruses)**:
    -   Más programokhoz (gazdaprogramokhoz) csatolják magukat.
    -   Terjedésükhöz **emberi beavatkozás** (pl. fájl megnyitása) szükséges.
    -   Céljuk általában a károkozás, adatok törlése, rendszerösszeomlás.
2.  **Férgek (Worms)**:
    -   **Önálló programok**, nem igényelnek gazdaprogramot.
    -   Hálózati sérülékenységeket kihasználva **önmagukat másolják és terjesztik** a hálózaton keresztül, emberi beavatkozás nélkül.
    -   Céljuk lehet a hálózat túlterhelése, hátterek létrehozása, DoS támadások indítása.
3.  **Trójai programok (Trojan Horses)**:
    -   Hasznosnak, ártalmatlannak tűnő programok, amelyek azonban a háttérben **rosszindulatú tevékenységet** végeznek.
    -   Nem másolják önmagukat.
    -   Céljuk lehet adatok lopása, hátterek nyitása, billentyűzetfigyelés.
4.  **Rootkitek (Rootkits)**:
    -   Céljuk, hogy a támadó **rejtve maradjon** a rendszerben, miután bejutott.
    -   Elrejtik a folyamatokat, fájlokat, hálózati kapcsolatokat. Nehéz detektálni és eltávolítani.
5.  **Spyware (Kémprogramok)**:
    -   Titokban **információkat gyűjtenek** a felhasználóról vagy a rendszerről (pl. böngészési szokások, jelszavak, e-mailek) és elküldik egy harmadik félnek.
6.  **Adware (Reklámprogramok)**:
    -   Nem kívánt **reklámokat jelenítenek meg**, gyakran pop-up ablakok formájában. Gyakran a spyware-rel együtt terjed.
7.  **Ransomware (Zsarolóvírusok)**:
    -   **Titkosítják a felhasználó adatait** vagy lezárják a rendszert, majd váltságdíjat követelnek az adatok feloldásáért.
    -   Nagyon pusztító és jövedelmező támadási forma.
8.  **Botnetek (Botnets)**:
    -   Fertőzött számítógépek hálózata (ún. "zombi" gépek), amelyeket a támadó (botmaster) távolról irányít.
    -   Céljuk tömeges támadások (pl. DDoS), spam küldése, adathalászat.
9.  **Keyloggerek (Billentyűzetfigyelők)**:
    -   Rögzítik a felhasználó által begépelt billentyűleütéseket, így megszerezve jelszavakat, bankkártyaadatokat, stb.
10. **Exploitok (kihasználások)**:
    -   Olyan programkód, amely egy szoftverben vagy hardverben lévő **sérülékenységet** használ ki a rendszer feltörésére vagy károsítására.
11. **Adatlopó szoftverek (Infostealers)**:
    -   Kifejezetten bizalmas adatok (jelszavak, bankkártyaadatok, személyes adatok) gyűjtésére és továbbítására specializálódtak.

## II. Terjedési Módszerek és Fertőzési Vektorok

A kártevők terjedésének számos módja van:
-   **E-mail mellékletek**: Fertőzött fájlok küldése.
-   **Weboldalak**: Drive-by download (honlap látogatásakor automatikus letöltés), hirdetések (malvertising).
-   **Adathordozók**: Fertőzött USB meghajtók.
-   **Hálózati sérülékenységek**: Szoftverekben lévő hibák kihasználása (férgek).
-   **Social Engineering**: Emberi megtévesztés (pl. adathalászat, megtévesztő üzenetek).
-   **Törvényes szoftverek**: Egyes kártevők beépülhetnek látszólag legális programokba.
-   **Fájlmegosztó hálózatok**: Fertőzött fájlok cseréje.

## III. A Fenyegetések Fejlődése

A kártevők folyamatosan fejlődnek, egyre kifinomultabbá és célzottabbá válnak:

-   **Korai fázis (egyszerű vírusok)**: Főleg bosszankodás, látható károkozás, kevésbé célzottak.
-   **Pénzügyi motiváció**: Megjelennek az adatok lopására, zsarolásra (ransomware) specializálódott kártevők.
-   **Rejtőzködés**: A rootkitek megjelenésével a kártevők egyre nehezebben detektálhatók.
-   **Célzott támadások (APT - Advanced Persistent Threats)**: Hosszan tartó, szervezett, specifikus célpontra irányuló támadások (pl. ipari kémkedés, állami támadások).
-   **IoT (Internet of Things) fenyegetések**: Az okoseszközök elterjedésével új támadási felületek és célpontok jelennek meg.
-   **Polimorf és metamorf kódok**: A kártevők képesek változtatni a kódjukat, megnehezítve az antivírus szoftverek detektálását.
-   **Zero-day exploitok**: Olyan sérülékenységek kihasználása, amelyekről a szoftver gyártója még nem tud.

## IV. Védekezés Programozott Kártevők Ellen

-   **Antivírus szoftverek**: Detektálás és eltávolítás (signature-alapú, heurisztikus).
-   **Tűzfalak**: Hálózati forgalom szűrése, illetéktelen hozzáférés blokkolása.
-   **IDS/IPS (Intrusion Detection/Prevention Systems)**: Behatolás detektálása/megelőzése.
-   **Szoftverfrissítések és patch-ek**: A sérülékenységek javítása.
-   **Rendszeres biztonsági mentések**: Adatok védelme a zsarolóvírusok ellen.
-   **Felhasználói tudatosság és képzés**: Social Engineering támadások felismerése.
-   **E-mail és webes szűrés**: Kártékony e-mailek és weboldalak blokkolása.
-   **Least Privilege elv**: A felhasználók csak a szükséges jogosultságokkal rendelkezzenek.
-   **Többfaktoros autentikáció**: Erősíti a fiókok védelmét.
-   **Sandbox környezetek**: Programok izolált futtatása a kártékony viselkedés elemzésére.

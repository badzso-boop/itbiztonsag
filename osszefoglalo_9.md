# 9. Hét: PKI és Felhőbiztonság / Social Engineering - Összefoglaló

Ez a dokumentum a 9. heti tananyagot foglalja össze, amely két fő témakört ölel fel: a nyilvános kulcsú infrastruktúrát (PKI) és a felhőbiztonsággal kapcsolatos tudnivalókat, különös tekintettel a Social Engineering támadásokra.

## I. Nyilvános Kulcsú Infrastruktúra (PKI)

A PKI egy olyan keretrendszer, amely lehetővé teszi az aszimmetrikus (nyilvános kulcsú) kriptográfia biztonságos és hiteles használatát elosztott rendszerekben. Célja az adatvagyon védelme a hitelesítés, bizalmasság, sértetlenség, letagadhatatlanság és rendelkezésre állás megteremtésével.

### 1. PKI jellemzői és szolgáltatásai

-   **Alapfeltétele a digitális aláírásnak**: Kétkulcsos (aszimmetrikus) titkosításon alapul.
-   **Kulcsmenedzsment**: Lehetővé teszi a kulcsok (új kibocsátása, frissítése, visszavonása) és tanúsítványok menedzselését.
-   **Nyilvános kulcsok nyilvánossága**: Biztosítja a nyilvános kulcsok megtalálását és letöltését.
-   **Konzisztens és átlátható biztonság**: Szervezeti környezetben a végfelhasználói alkalmazásokig bezárólag.
-   **Magas fokú rendelkezésre állás és méretezhetőség**: 7x24 órás működés, katasztrófatűrő működés.
-   **Biztonságos üzemeltetési infrastruktúra**: Óvja a szervezet jó hírnevét.
-   **Külső kapcsolatok kezelése**: Különböző szervezeteket, közösségeket szolgálhat ki.
-   **Hardvertámogatás**: A kritikus alkalmazások hardveres kriptográfiai modulokat használnak (pl. intelligens kártyák).

### 2. PKI Architektúra Elemei

-   **Tanúsítvány alanya és használója**: A legalapvetőbb elem. Lehet egy személy, szervezet, rendszer vagy alkalmazás, akinek/aminek tanúsított nyilvános kulcsa van.
-   **Tanúsító Hatóság (CA - Certificate Authority)**: A PKI legfontosabb eleme. Feladata a tanúsítványtulajdonosok azonosságának megállapítása és igazolása, tanúsítványok kibocsátása, visszavonása. A CA saját privát kulcsával digitálisan aláírja a kibocsátott tanúsítványokat, ezzel hitelesítve azokat.
-   **Regisztrációs Hatóságok (RA - Registration Authority)**: A CA alárendelt szerverei, amelyekre a CA a felhasználók regisztrációjával kapcsolatos menedzselési funkciókat delegálja.
-   **PKI Adattárak (Repository)**:
    -   **Archív adattárak**: A kibocsátott, érvényes, lejárt és visszavont kulcsok biztonsági másolatainak tárolására szolgálnak, magas védettségi fokon, hálózattól elzárt helyen.
    -   **Címtár integráció**: Kulcsok és tanúsítványok tárolására, elosztására, keresésére. Az LDAP támogatása alapkövetelmény.
-   **Visszavonási listák (CRL - Certificate Revocation List / OCSP - Online Certificate Status Protocol)**: A CA köteles visszavonni a hitelességüket elvesztett tanúsítványokat. Ezen listák biztonságos fenntartása és terjesztése kulcsfontosságú.
-   **Kulcs- és tanúsítványmenedzselési eszközök**: Biztosítják a kiadott tanúsítványok és kulcsok nyilvántartását, frissítését, archiválását és biztonságos megsemmisítését.

### 3. Bizalmi Kapcsolatok és modellek

-   **Egyirányú bizalmi kapcsolat**: Két tartomány között létrejött egyirányú hitelesítési útvonal. Az A tartomány felhasználói elérhetik a B tartomány erőforrásait, de fordítva nem. Lehet tranzitív vagy nem tranzitív.
-   **Kétirányú bizalmi kapcsolat**: Mindkét tartomány megbízik a másikban, így a hitelesítési kérelmek mindkét irányban továbbíthatók. Tranzitív is lehet.
-   **Tanúsítvány hierarchia**: A legfelső szintű (root) CA megbízik egy vagy több alsóbb szintű (intermediate) CA-ban, akik további tanúsítványokat bocsátanak ki. A bizalmi lánc ellenőrzése történik.

## II. Felhőbiztonság és Social Engineering

### 1. Social Engineering Támadások Fajtái

A Social Engineering (társadalmi mérnökség) az emberi tényező kihasználható tulajdonságaira építő támadás. Az emberek befolyásolására, manipulálására alapozva teszi lehetővé bizalmas információk megszerzését, vagy kártékony program terjedését.

-   **Pretexting**: A támadó egy kitalált forgatókönyvet (ürügyet) használ, hogy személyes vagy pénzügyi adatokra tegyen szert.
-   **Phishing**: E-mailt küld, amely legitim forrásból származónak tűnik, hogy rávegye a címzettet kártékony program telepítésére vagy bizalmas információk megadására.
    -   **Spear Phishing**: Célzott adathalász támadás egy adott személyre vagy szervezetre szabva.
-   **Spam**: Kéretlen e-mail, amely gyakran tartalmaz kártékony hivatkozásokat vagy megtévesztő tartalmat.
-   **Baiting**: Beetetés, pl. egy rosszindulatú programmal fertőzött pendrive elhelyezése nyilvános helyen.
-   **Impersonation**: A támadó valaki másnak adja ki magát, hogy elnyerje az áldozat bizalmát.
-   **Vishing és Smishing**: Telefonon (vishing) vagy SMS-ben (smishing) történő megtévesztés.
-   **Tailgating**: A támadó egy felhatalmazott személyt követve jut be egy biztonságos, beléptető rendszerrel védett helyre.
-   **Shoulder Surfing**: A támadó valakinek a válla fölött nézi le a jelszavát vagy más bizalmas információit.
-   **Dumpster Diving**: A kukák közötti turkálás bizalmas dokumentumok után.
-   **Pig Butchering**: Pénzügyi csalás, ahol a támadó hosszú távú kapcsolatot épít ki, és befektetésekre (hamis kereskedési platformon) ösztönzi az áldozatot.
-   **Stalkerware**: Titkos mobilos zaklató program, amely helymeghatározási adatokat, üzeneteket, hívásokat gyűjt.
-   **Pegasus**: Hírhedt művésznevű kémprogram.

### 2. A Social Engineering sikere és védekezés

-   **Miért működik?**: A megszerzett ismeretek (az áldozatról) alapján gyorsan épít kapcsolatot, magasabb profit lehetőséget ígér, pszichológiai manipulációval él.
-   **A biztonság leggyengébb láncszeme**: Az ember. A Social Engineering az emberi tényező kihasználható tulajdonságaira épít.
-   **Védekezés lehetőségei**:
    -   **Oktatás és Tudatosítás**: A felhasználók képzése a Social Engineering kockázataira.
    -   **Stratégiák kidolgozása**: A személyazonosság ellenőrzésének biztonságos módszerei telefonon, e-mailben.
    -   **Soha ne adja meg a hitelesítésre szolgáló adatokat**.
    -   **Minden e-mailt és üzenetet paranoiával kezeljünk**.
    -   **Kétséges jelek felismerése**: Gyenge nyelvhasználat, furcsa feladó, sürgetés, megfélemlítés, túl jó ajánlatok.
    -   **Soha ne használjuk újra a jelszavainkat**.
    -   **Mindig lépjünk ki és zároljuk a számítógépet**.
    -   **Többfaktoros azonosítás**.

### 3. Felhőbiztonság tudnivalók

A felhőalapú szolgáltatások (IaaS, PaaS, SaaS) új biztonsági kihívásokat és megfontolásokat vezetnek be. Bár a gyakorlati anyag főleg a Social Engineeringre fókuszál, a felhőalapú rendszerek is potenciális célpontjai lehetnek ezeknek a támadásoknak. Fontos a "megosztott felelősség" modelljének megértése, ahol a felhőszolgáltató és az ügyfél egyaránt felelős a biztonság bizonyos aspektusaiért.

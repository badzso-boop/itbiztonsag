# 12. Hét: Ellenőrző Teszt - Adatvédelem és Adatmentés

Ez a teszt a 12. heti "Adatvédelem és Adatmentés" tananyagra épül. Válaszaidat az összefoglaló és a tananyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (Adatvédelem Fogalma)**

Definiáld az "Adatvédelem" fogalmát, kiemelve a személyes adatok gyűjtésével, feldolgozásával és felhasználásával kapcsolatos korlátozásokat! Milyen aspektusokat tartalmaz a komplex adatvédelmi átvilágítás?

---

**2. Kérdés (GDPR Teendők)**

A GDPR bevezetése kapcsán egy cégnek több teendője is van. Sorolj fel legalább három olyan kulcsfontosságú lépést, amelyet meg kell tennie az adatkezelés biztonságának garantálása érdekében!

---

**3. Kérdés (Adatkezelési Szabályzat)**

Az adatkezelési szabályzat számos előírást tartalmaz. Nevezz meg két olyan alapvető szabályt vagy tilalmat, amely a cég dolgozóira vonatkozik az adatok másolása vagy külső hozzáférése tekintetében!

---

**4. Kérdés (Adatbiztonság vs. Titokvédelem)**

Mi a különbség az "Adatbiztonság" és a "Titokvédelem" fogalma között?

---

**5. Kérdés (PET Technológia)**

Mi a "PET (Privacy Enhancing Technologies)" célja az adatvédelemben? Adj egy példát ilyen technológiára!

---

**6. Kérdés (Adatmentés Okai)**

Sorolj fel legalább három okot, amiért az adatmentés elengedhetetlen egy szervezet számára!

---

**7. Kérdés (Gyakori Adatmentési Hibák)**

Melyek a leggyakoribb adatmentési hibák, amelyek adatvesztéshez vagy sikertelen helyreállításhoz vezethetnek? Sorolj fel legalább hármat!

---

**8. Kérdés (Adatmentés Típusai)**

Hasonlítsd össze a "Teljes mentés", "Inkrementális mentés" és "Differenciális mentés" típusokat a mentett adatok mennyisége és a helyreállítási folyamat szempontjából!

---

**9. Kérdés (Biztonsági Adatmentés Rendje)**

Milyen két kulcsfontosságú alapelvet kell figyelembe venni egy biztonsági adatmentési rend (gyakoriság és generációk) kialakításakor?

---

**10. Kérdés (Adatkezelési Hibák)**

Melyek a leggyakoribb "adatkezelési hibák" (nem adatmentési!), amelyek az adatvédelmi problémákhoz vezetnek egy szervezetnél? Sorolj fel legalább kettőt!

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
Az "Adatvédelem" a személyes adatok gyűjtésének, feldolgozásának és felhasználásának korlátozását, az érintett személyek védelmét biztosító alapelvek, szabályok, eljárások, adatkezelési eszközök és módszerek összessége. A komplex adatvédelmi átvilágítás kiterjed a jogi és belső szabályozási dokumentumok vizsgálatára, az adatalanyok jogainak érvényesíthetőségére, az informatikai rendszer adatvédelmi szempontú elemzésére, valamint a rendszer felépítésére és működésére vonatkozó javaslatok megfogalmazására is.

**2. Kérdés:**
Három kulcsfontosságú lépés a GDPR-megfelelés garantálásához:
1.  **Felmérés és Adatkezelési Nyilvántartás készítése**: Fel kell mérni, milyen adatokat kezelnek, hol és milyen jogcímen. Részletes nyilvántartást kell vezetni az adatkezelési tevékenységekről.
2.  **Adattisztítás**: Ha a jogcím vagy a cél nem megfelelő, vagy ha a nyilvántartás szükségtelenül részletes, az adatokat törölni kell.
3.  **Adatok biztonságának garantálása**: Biztonságos adattovábbítás, biztonságos jelszavak és azonosítás, vírusvédelem, mobil eszközök biztonsága, biztonsági mentés, felhasználói jogosultságok nyilvántartása.

**3. Kérdés:**
1.  **Másolási tilalom**: Az adatokról nem készíthetnek másolatot, kivéve az előírt biztonsági mentéseket.
2.  **Külső hozzáférés tilalma**: Az adatokhoz nem engedhetnek illetéktelen külső hozzáférést sem közvetlenül a számítógépnél, sem hálózaton vagy interneten keresztül.
3.  **Távmunka szabályai**: Távmunka során az adatok biztonságos kezelésére fokozottan kell ügyelni, adatot a távoli gépre átmásolni tilos.

**4. Kérdés:**
-   **Adatbiztonság**: Az adatok jogosulatlan megismerése, megszerzése, továbbítása, módosulása és tönkremenetele elleni intézkedések, valamint a hitelességük, integritásuk, bizalmasságuk és rendelkezésre állásuk biztosítása. Technikai és szervezeti intézkedéseket egyaránt magában foglal.
-   **Titokvédelem**: Valamilyen "titok" (pl. üzleti titok, orvosi titok) védelmének, megismerésének korlátozását jelenti. Ez az adatbiztonság egyik aspektusa, amely a bizalmasságot célozza.

**5. Kérdés:**
A **PET (Privacy Enhancing Technologies)** célja az adatvédelemben, hogy a felhasználók identitását védjék az anonimitás, a pszeudonimitás, az erőforrások használatának, valamint a felhasználók személyének külső szemlélő általi összeköthetetlensége (unlinkability) és a kommunikáció tényének megfigyelhetetlensége (unobservability) biztosításával.
*   **Példa**: A **Tor hálózat** (onion routing), amely anonim böngészést és kommunikációt tesz lehetővé, elrejtve a felhasználó IP-címét és online tevékenységét.

**6. Kérdés:**
1.  **Tervszerű, folyamatos mentés**: Rendszeres mentések az adatok megőrzéséhez.
2.  **Funkcionális hardveregység hibája**: Hardver meghibásodása esetén az adatok elveszhetnek, ha nincsenek mentések.
3.  **Adatvesztés (pl. fájlok törlése, korrupt fájlrendszer, vírus)**: Véletlen vagy szándékos adatvesztés esetén.

**7. Kérdés:**
1.  **Csak egy vagy két folyton felülírt mentés van**: Ha egyetlen mentési pontunk van, és az is felülíródik, akkor nincs visszaállítási lehetőség.
2.  **A mentés visszatölthetőségét nem ellenőrzik**: A mentések tesztelésének hiánya miatt incidens esetén derülhet ki, hogy a mentés sérült vagy nem működik.
3.  **Nem minden fontos adat kerül be a mentésbe**: Fontos adatok kimaradnak a mentésből, ami adatvesztéshez vezethet.
4.  **Nincs kijelölve a mentésért felelős személy**: A felelősség hiánya hibákhoz vagy a mentések elmaradásához vezethet.

**8. Kérdés:**
-   **Teljes mentés**: Az összes adatot menti. Hosszú időt vesz igénybe, nagy tárhelyet igényel. Helyreállításkor egyszerű és gyors.
-   **Inkrementális mentés**: Csak az utolsó mentés óta módosult fájlokat tartalmazza. Rövid mentési idő, kis tárhely. Helyreállításkor az utolsó teljes mentésre és az összes inkrementális mentésre szükség van, ami lassíthatja és bonyolíthatja a folyamatot.
-   **Differenciális mentés**: A legutóbbi *teljes* mentés óta módosult adatokat tartalmazza. Hosszabb mentési idő, mint az inkrementálisnál. Helyreállításkor az utolsó teljes mentésre és csak az utolsó differenciális mentésre van szükség, ami gyorsabbá teszi a helyreállítást.

**9. Kérdés:**
Az **archiválás** célja az adatok hosszú távú megőrzése jogi, szabályozási vagy történeti okokból, amelyekre már nincs szükség a mindennapi működéshez. Főleg ritkábban szükséges hozzányúlni, és a helyreállításuk (ha szükséges) lassabb, mint a hagyományos mentésekből. Ezzel szemben a **hagyományos adatmentés** a rövid- és középtávú helyreállításra fókuszál, az üzletmenet folytonosságának biztosítása érdekében.

**10. Kérdés:**
1.  **Egyáltalán nincs adatkezelési szabályzat**: A szabályok hiánya anarchiához és következetlenséghez vezet az adatkezelésben.
2.  **A használaton kívül kerülő gépeken fontos adatok maradnak**: A selejtezett eszközökről nem törlik biztonságosan az adatokat.
3.  **Az adatkezelés nem a minőségirányítási rendszer része**: Az adatkezelést nem integrálják a vállalat minőségbiztosítási folyamataiba.
4.  **Nem minden fontos adat kerül be a mentésbe**: Hibás felmérés miatt egyes kritikus adatokról nem készül mentés.
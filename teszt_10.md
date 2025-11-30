# 10. Hét: Ellenőrző Teszt - Jogosultságkezelés és Adatmentés

Ez a teszt a 10. heti "Jogosultságkezelés és Adatmentés" tananyagra épül. Válaszaidat az összefoglaló és a tananyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (Jogosultságkezelés)**

Mi az a **Biztonsági Leíró (Security Descriptor)**, és hol tárolódik tipikusan egy Windows tartományi környezetben?

---

**2. Kérdés (Objektumengedélyek)**

Magyarázd el a különbséget az "Olvasás" és a "Módosítás" engedélyek között egy fájl vagy mappa esetében! Milyen műveleteket tesz lehetővé mindegyik?

---

**3. Kérdés (Engedélyek Öröklődése)**

Mi az **engedélyek öröklődése** egy fájlrendszerben, és hogyan lehet befolyásolni (pl. letiltani vagy szelektíven alkalmazni) ezt a mechanizmust?

---

**4. Kérdés (Hatályos Engedélyek)**

Mit értünk **Hatályos Engedélyek (Effective Permissions)** alatt, és miért fontos a szerepük a hozzáférési problémák hibaelhárításakor?

---

**5. Kérdés (RPO vs. RTO)**

Definiáld az **RPO (Recovery Point Objective)** és az **RTO (Recovery Time Objective)** fogalmait! Magyarázd el, miért kulcsfontosságú ez a két metrika az adatmentési és katasztrófa-helyreállítási tervek tervezésekor!

---

**6. Kérdés (Adatmentési Folyamat)**

Sorold fel az adatmentési folyamat főbb fázisait a "Felméréstől" a "Felülvizsgálatig"!

---

**7. Kérdés (Adatmentés Szintjei)**

Nevezz meg legalább két különböző szintjét az adatmentésnek (pl. mi az, amit menthetünk), és adj egy-egy példát mindegyikre!

---

**8. Kérdés (Adatmentés Típusai)**

Hasonlítsd össze az "Másolás", "Szinkronizálás" és "Verziókövetés" adatmentési típusokat egy-egy jellemzőjük alapján!

---

**9. Kérdés (Archiválás)**

Mi az **archiválás** célja, és miben különbözik az adatok archiválása a hagyományos adatmentéstől?

---

**10. Kérdés (Adatmentési Problémák)**

Sorolj fel legalább három gyakori problémát vagy kihívást, amelyek felmerülhetnek az adatmentési és helyreállítási folyamatok során!

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
A **Biztonsági Leíró (Security Descriptor)** egy olyan adatstruktúra, amely egy objektumhoz (pl. fájl, mappa, felhasználói fiók, számítógép) van rendelve. Tartalmazza a hozzáférési engedélyeket (ACL), az objektum tulajdonosát (Owner) és az auditálási beállításokat. Tipikusan egy Windows tartományi környezetben az **Active Directory** tárolja ezeket, központosított módon.

**2. Kérdés:**
-   **Olvasás (Read) engedély**: Lehetővé teszi a felhasználó számára egy fájl tartalmának megtekintését, vagy egy mappa tartalmának listázását, az attribútumok megtekintését. Nem engedélyezi a fájl módosítását, törlését vagy létrehozását.
-   **Módosítás (Modify) engedély**: Magában foglalja az Olvasás jogokat, és ezen felül lehetővé teszi a felhasználó számára egy fájl tartalmának módosítását, mappában lévő fájlok és almappák létrehozását, vagy egy fájl/mappa attribútumainak megváltoztatását. Nem teszi lehetővé a tulajdonos megváltoztatását vagy az engedélyek módosítását.

**3. Kérdés:**
Az **engedélyek öröklődése** azt jelenti, hogy egy mappa vagy tároló objektum (szülő) jogosultságai automatikusan ráhagyományozódnak az abban lévő fájlokra és almappákra (gyermekek). Ezt a mechanizmust befolyásolhatjuk:
-   **Letiltással**: Egy objektumon kikapcsolható az öröklődés, így az objektum nem örökli tovább a szülői engedélyeket, hanem saját, explicit engedélyeket kap.
-   **Szelektív alkalmazással**: Meghatározható, hogy mely engedélytípusok öröklődjenek, és melyek ne, illetve mely objektumtípusokra terjedjen ki az öröklődés.

**4. Kérdés:**
A **Hatályos Engedélyek (Effective Permissions)** azok a tényleges jogosultságok, amelyekkel egy adott felhasználó rendelkezik egy konkrét objektumhoz, figyelembe véve az összes rá vonatkozó engedélyt (explicit, örökölt, csoporttagságból származó, deny szabályok). Fontos szerepük van a hozzáférési problémák hibaelhárításakor, mert megmutatják a valódi, összesített jogosultságokat, így könnyebb azonosítani, hogy miért nem fér hozzá valaki egy erőforráshoz, vagy éppen miért fér hozzá valamihez, amihez nem kellene.

**5. Kérdés:**
-   **RPO (Recovery Point Objective)**: A maximális elfogadható adatvesztés mennyisége (időben kifejezve), ami egy incidens során bekövetkezhet. Azt jelöli, hogy egy katasztrófa után mennyi adatot (hány óra, perc, tranzakció értékű adatot) engedhetünk meg elveszni.
-   **RTO (Recovery Time Objective)**: Az az időtartam, ameddig egy rendszer vagy szolgáltatás maximálisan kieshet egy incidens után, mielőtt az üzletmenetre elfogadhatatlan károkat okozna. Azt az időt jelöli, amíg a normál működés helyreállításra kerül.
Ez a két metrika kulcsfontosságú, mert meghatározzák az adatmentési stratégia (gyakoriság, típus) és a helyreállítási terv (módszer, technológia) költségeit és összetettségét.

**6. Kérdés:**
1.  **Felmérés**: A védendő adatok és rendszerek azonosítása, üzleti értékük felmérése.
2.  **Specifikáció**: Az üzleti igények (RPO, RTO) és metrikák meghatározása.
3.  **Tervezés**: Adatmentési terv, katasztrófa-helyreállítási terv, rendszerterv készítése.
4.  **Kiépítés**: Az adatmentési rendszer vagy szolgáltatás megvalósítása.
5.  **Tesztelés**: A mentések és helyreállítások rendszeres tesztelése az RPO és RTO célok teljesülése érdekében.
6.  **Monitorozás és Felülvizsgálat**: Az adatmentési rendszer folyamatos figyelése és időszakos felülvizsgálata a változó igényekhez igazítva.

**7. Kérdés:**
1.  **Felhasználói/szolgáltatott adat szintje**: Csak a végfelhasználók által generált vagy szolgáltatások által használt adatokat mentjük (pl. dokumentumok, adatbázis rekordok).
2.  **Rendszervisszaállításhoz szükséges konfigurációk**: A rendszerek működéséhez elengedhetetlen konfigurációs fájlok, registry beállítások mentése.
3.  **Teljes szerver szintje**: A teljes szerver (operációs rendszer, alkalmazások, adatok) állapotának mentése, gyakran virtualizált szerverek esetén snapshotokkal.

**8. Kérdés:**
-   **Másolás**: Egyszerű másolatot készít az adatokról egy másik helyre. Az eredeti és a másolat között nincs aktív kapcsolat a másolás után.
-   **Szinkronizálás**: Folyamatosan vagy rendszeres időközönként összehasonlítja és azonossá teszi az adatokat két helyen. Az adatok mindig megegyeznek a forrás és a cél helyen.
-   **Verziókövetés**: Az adatok több korábbi állapotát is megőrzi, lehetővé téve, hogy egy adott időpontra visszamenőleg helyreállítsunk egy fájlt vagy adatot. Minden változtatás egy új "verzióként" tárolódik.

**9. Kérdés:**
Az **archiválás** célja az, hogy azokat az adatokat, amelyekre már nincs szükség a mindennapi működéshez, de jogi, szabályozási vagy történeti okokból meg kell őrizni, hosszú távon, költséghatékony módon tároljuk. Az archivált adatok jellemzően ritkábban elérhetőek, esetleg tömörítettek, és a helyreállításuk (ha szükséges) lassabb, mint a hagyományos mentésekből. A **hagyományos adatmentés** ezzel szemben a rövid- és középtávú helyreállításra fókuszál, az üzletmenet folytonosságának biztosítása érdekében.

**10. Kérdés:**
1.  **Adatmennyiség mérete**: Az egyre növekvő adatmennyiség miatt a mentések és helyreállítások időigényessé válhatnak.
2.  **Sávszélesség korlátai**: Távoli mentés vagy felhőalapú mentés esetén a rendelkezésre álló hálózati sávszélesség szűk keresztmetszetet jelenthet.
3.  **Szabályzások (pl. GDPR)**: A jogi és adatvédelmi előírások (pl. hol tárolhatóak felhasználói adatok, az adattörlés joga a mentésből és archiválásból is) jelentősen bonyolíthatják az adatmentési stratégiát.
4.  **Helyreállítás tesztelésének hiánya**: Sok szervezet ment, de ritkán vagy soha nem teszteli a helyreállítást, így incidens esetén derül ki, hogy a mentések használhatatlanok.
5.  **Felhőszolgáltatóba vetett bizalom**: Külső szolgáltatás (felhő) használata esetén a szolgáltató biztonsága és megbízhatósága kritikus, de nem mindig ellenőrizhető teljes mértékben.
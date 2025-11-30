# 10. Hét: Jogosultságkezelés és Adatmentés - Összefoglaló

Ez a dokumentum a 10. heti tananyagot foglalja össze, amely a jogosultságkezelés (hozzáférés-vezérlés) elveit és gyakorlatát, valamint az adatmentés és katasztrófa-helyreállítás alapvető aspektusait tárgyalja.

## I. Jogosultságkezelés (Hozzáférés-vezérlés)

A jogosultságkezelés (Access Control) az a folyamat, amely korlátozza, hogy ki vagy mi (felhasználó, számítógép, szervezet) használhat bizonyos erőforrásokat vagy objektumokat, és milyen műveleteket hajthat végre velük.

### 1. Rendszergazdai lehetőségek

-   **Biztonsági leírók (Security Descriptor)**: Objektumokhoz (pl. fájl, mappa, felhasználó, számítógép) rendelt beállítások, amelyek tárolják a hozzáférési engedélyeket (ACL - Access Control List), a tulajdonost (Owner) és a naplózási beállításokat. Az Active Directory (AD) tárolja ezeket.
-   **Engedélyek beállítása**: A rendszergazda beállíthatja, hogy adott felhasználók vagy csoportok milyen típusú hozzáféréssel rendelkezzenek egy objektumhoz vagy annak tulajdonságaihoz.
-   **Felhasználói hozzáférés figyelése**: Naplózással és az objektum attribútumainak elérésével nyomon követhető a felhasználói tevékenység.

### 2. Engedélyek és Objektumengedélyek

-   **Általános engedélyek**: A legtöbb objektumhoz hozzárendelhető alapvető jogosultságok, mint az Olvasás, Módosítás, Törlés, Új tulajdonos beállítása.
-   **Objektumengedélyek**: Speciálisabb jogok, amelyeket csoportokhoz, felhasználókhoz, tartományi identitásokhoz vagy helyi fiókokhoz lehet rendelni. Célszerű csoportokhoz rendelni a könnyebb adminisztráció érdekében.
-   **Összetett hozzáférési szintek**: Elemi jogokra bonthatók, pl. "Full Control" (teljes hozzáférés), "Read" (olvasás), "Write" (írás), "Create All Child Objects" (összes gyermekobjektum létrehozása), "Delete All Child Objects" (összes gyermekobjektum törlése).

### 3. Objektumok Tulajdonjoga és Engedélyek Öröklődése

-   **Tulajdonjog**: Alapértelmezés szerint az objektum létrehozója annak tulajdonosa. A tulajdonos bármikor megváltoztathatja az objektumhoz rendelt engedélyeket.
-   **Engedélyek öröklődése**: A mappastruktúrában a tárolók (mappák) engedélyei automatikusan öröklődhetnek az alatta lévő objektumokra (fájlokra, al-mappákra). Az öröklődés letiltható vagy szelektíven alkalmazható.

### 4. Hatályos Engedélyek (Effective Permissions)

A hatályos engedélyek azt mutatják meg, hogy egy adott felhasználónak vagy csoportnak ténylegesen milyen jogai vannak egy objektumhoz, figyelembe véve az összes explicit és örökölt engedélyt, valamint a csoporttagságokat.

### 5. Jogosultságok kezelése és SID (Security Identifier)

-   A jogosultságokat objektumokon érvényesítjük, és felhasználókhoz vagy csoportokhoz rendeljük.
-   Nem a felhasználó/csoport neve a meghatározó, hanem a **Security IDentifier (SID)**, amely egy egyedi azonosító.

## II. Adatmentés és Helyreállítás

Az adatmentés (Data Backup) az üzletmenet folytonosság (Business Continuity) és a katasztrófa-helyreállítás (Disaster Recovery) alapvető része. Célja az adatok megőrzése és helyreállíthatósága adatvesztés vagy rendszerhiba esetén.

### 1. Alapfogalmak

-   **Üzletmenet Folytonosság (Business Continuity)**: A szervezet képessége, hogy egy incidens (pl. katasztrófa) után is folytatni tudja alapvető működését.
-   **Üzletmenet Folytonossági Terv (Business Continuity Plan - BCP)**: Dokumentált terv az üzletmenet fenntartására incidensek esetén.
-   **Adatmentés (Data Backup)**: Az adatok másolatának elkészítése későbbi helyreállítás céljából.
-   **Adat-helyreállítás (Data Recovery)**: Az elveszett vagy sérült adatok visszaállítása a mentésekből.
-   **Katasztrófa Helyreállítási Terv (Disaster Recovery Plan - DRP)**: Részletes terv a kritikus IT-infrastruktúra és adatok helyreállítására katasztrófa után.

### 2. Kulcsmetrikák: RPO és RTO

-   **Recovery Point Objective (RPO)**: Az a maximális elfogadható adatvesztés mennyiség, ami egy incidens során bekövetkezhet. Az utolsó mentési pontot jelöli, incidens esetén az ezelőtti adatok megmaradnak, az utána lévők elvesznek.
-   **Recovery Time Objective (RTO)**: Az az időtartam, ameddig egy rendszer vagy szolgáltatás maximálisan kieshet egy incidens után, mielőtt az elfogadhatatlan károkat okozna az üzletmenetnek. Az az idő, ami a rendszer normál működésének helyreállításához szükséges.

### 3. Adatmentési Folyamat

1.  **Felmérés**: Megállapítani, mit kell menteni, mi az érték.
2.  **Specifikáció**: Metrikák (RPO, RTO) és igények meghatározása.
3.  **Tervezés**: Adatmentési terv, katasztrófa-helyreállítási terv, rendszerterv készítése.
4.  **Kiépítés**: Adatmentési rendszer/szolgáltatás kiépítése.
5.  **Tesztelés**: Adatmentés használhatóságának (RPO) és helyreállítás működőképességének (RTO) ellenőrzése.
6.  **Monitorozás**: Monitorozás beállítása, felülvizsgálat időnként.

### 4. Adatmentés szintjei, típusai, gyakorisága és helye

-   **Mentés szintjei**:
    -   Felhasználói/szolgáltatott adat.
    -   Rendszervisszaállításhoz szükséges konfigurációk.
    -   Teljes szerver (pl. virtualizált szerverek snapshot alapú visszaállítása).
-   **Mentés típusai**:
    -   **Másolás**: Egyszerű másolat készítése.
    -   **Szinkronizálás**: Az adatok folyamatos szinkronban tartása két hely között.
    -   **Verziókövetés**: Az adatok változásainak nyomon követése, több korábbi állapot visszaállításának lehetősége.
-   **Mentés gyakorisága**: Az RPO és az adatok üzletmeneti fontossága, változásának gyakorisága határozza meg (időben vagy verziószámban mérve).
-   **Mentés helye**:
    -   **Lokális**: Ugyanazon a helyszínen, de más eszközön.
    -   **Távoli**: Másik helyszínen (közeli vagy távoli, X km-en belül/kívül).
    -   **Céleszköz szerint**: Saját eszköz (pl. NAS) vagy külső szolgáltatás (pl. felhő).

### 5. Archiválás

-   Adatok hosszú távú tárolása, ritkábban szükséges hozzányúlni.
-   Fontos kérdés: meddig tároljunk adatot gyorsan elérhetően (RTO)?
-   Nem azonnali hozzáférésű, sokszor tömörített.

### 6. Adatmentési problémák és felvetődő kérdések

-   **Adatmennyiség és tárolás**: Nagy adatmennyiség, tárolás ideje, felülírás, archiválás.
-   **Sávszélesség**: Távoli mentés esetén kritikus lehet.
-   **Bizalom**: Saját eszköz vs. külső szolgáltatás.
-   **Véletlen törlés elleni védelem**: A mentési szolgáltatás nyújt-e ilyen védelmet.
-   **Szabályzások (pl. GDPR)**: Hol tárolhatók a felhasználói adatok, és a felhasználó joga az adattörlésre a mentésből és archiválásból is.
-   **Szoftveres/Hardveres sérülések**: Adatvisszaállító eljárások és szoftverek alkalmazása, szakértők bevonása hardveres sérülés esetén.

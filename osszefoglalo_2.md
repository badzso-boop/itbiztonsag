# 2. Hét: Kockázatelemzés a Gyakorlatban - Összefoglaló

Ez a dokumentum a második heti "Kockázatelemzés" témakör legfontosabb elméleti és gyakorlati tudnivalóit foglalja össze.

## Mi a kockázatelemzés és miért fontos?

A kockázatelemzés egy olyan folyamat, amely segít azonosítani a szervezet rendszerének **leggyengébb pontjait** és a legnagyobb fenyegetéseket. Célja, hogy ezek ismeretében **költséghatékony és arányos védekezést** lehessen kialakítani. Enélkül a védelmi kiadások nem biztos, hogy a leghatékonyabban hasznosulnak.

**Alapvető kérdések:**
- **MIT** védünk? → **Vagyontárgyak** (assets) azonosítása.
- **MITŐL** védjük? → **Fenyegetések** (threats) és **sérülékenységek** (vulnerabilities) feltárása.
- **HOGYAN** védjük? → **Ellenintézkedések** (controls) meghatározása.

## A Kockázatmenedzsment Folyamata

A kockázatmenedzsment általában nem konkrét pénzösszegekkel, hanem **kategóriákkal** és **szintekkel** dolgozik, hogy összehasonlíthatóvá tegye a különböző kockázatokat. A folyamat fő lépései a következők:

### 1. Vagyonelemek Azonosítása és Értékelése

Az első lépés egy **vagyonleltár** készítése. Itt azonosítjuk az összes olyan elemet, amelynek értéke van a szervezet számára. A te esetedben a rendelőintézet példájánál maradva, a vagyonelemeket 5 csoportba soroljuk:

- **Információ**: Maguk az adatok (pl. `Alap betegadatok`, `Számlázási adatok`, `Orvosok jelszavai`).
- **Szoftver**: Az információt kezelő programok (pl. `Betegnyilvántartó rendszer`, `Windows 2008 Server`).
- **Hardver**: A szoftvereket futtató fizikai eszközök (pl. `Rendelői szerver`, `Tűzfal szerver`).
- **Infrastruktúra**: A hardvert támogató környezet (pl. `Szerverterem`, `Áramszolgáltatás`).
- **Személy**: A rendszert használó és üzemeltető emberek (pl. `Orvos`, `Rendszergazda`).

Ezután minden **információ** típusú vagyonelemhez meg kell határozni a **Bizalmasság (C), Sértetlenség (I) és Rendelkezésre állás (A)** fontosságát (pl. kritikus, nagyon fontos, közepesen fontos stb.). Ez lesz a kiindulópont a kár mértékének becsléséhez.

### 2. Fenyegetések és Sérülékenységek Azonosítása

- **Sérülékenység**: A rendszer gyengesége. A felmért rendelőben rengeteg ilyen van:
    - *Szoftveres*: `Windows XP` kliensek (nem támogatott), `WEP` titkosítás a Wi-Fi-n (gyenge), `1234` alapértelmezett jelszó, 2012 óta nem frissített levelezőszerver.
    - *Hardveres*: 10 éves tűzfal szerver, nincs `RAID` a redundanciára (csak RAID 0), nincs szünetmentes táp (`UPS`).
    - *Fizikai*: Egyszerű faajtó, a rendelők kulcsait benne hagyják az ajtóban.
- **Fenyegetés**: Potenciális veszély, ami kihasználhat egy sérülékenységet (pl. `Hardveres meghibásodás`, `Szándékos jogosulatlan adatmásolás`, `Áramkimaradás`).

### 3. Kockázati Lista Létrehozása

Itt párosítjuk a vagyonelemeket a rájuk ható fenyegetésekkel. Egy kockázat tehát egy **(vagyonelem, fenyegetés)** páros.

Példa: A `Rendelői szerver` (vagyonelem) és a `Hardveres meghibásodás` (fenyegetés) párosa egy konkrét kockázatot jelent.

### 4. Kockázatok Elemzése és Értékelése

Minden kockázathoz két fő paramétert becslünk meg:

1.  **Bekövetkezési Valószínűség (P - Probability)**: Milyen gyakran fordulhat elő az esemény? (pl. Nagyon ritka, Ritka, Közepes, Gyakori, Nagyon gyakori).
2.  **Okozott Kár (D - Damage)**: Mekkora kárt okoz, ha bekövetkezik? Ezt a CIA-értékek alapján határozzuk meg. (pl. Elhanyagolható, Enyhe, Közepes, Súlyos, Kritikus).

A **Kockázat (R - Risk)** szintjét egy **kockázati mátrix (szorzótábla)** segítségével kapjuk meg, ami a `P` és `D` értékéből származtat egy kockázati szintet (pl. Minimális, Elviselhető, Mérsékelt, Lényeges, Elfogadhatatlan).

`Kockázat (R) = Valószínűség (P) × Kár (D)`

### 5. Kockázatkezelés

Az elemzés után a menedzsmentnek döntenie kell a feltárt kockázatokról. A fő stratégiák:

- **Kockázatcsökkentés (Risk Reduction)**: Ellenintézkedéseket vezetünk be a valószínűség (P) vagy a kár (D) csökkentésére. (Pl. lecseréljük a régi szervert, erősebb titkosítást használunk). Ez a leggyakoribb stratégia.
- **Kockázat-áthárítás (Risk Transfer)**: A kockázatot (vagy annak pénzügyi következményeit) átadjuk egy harmadik félnek. (Pl. biztosítás kötése).
- **Tudatos kockázatvállalás (Risk Acceptance)**: Elfogadjuk a kockázatot, mert a kezelése többe kerülne, mint a lehetséges kár. Ezt általában alacsony kockázatoknál alkalmazzák, és mindig felsővezetői döntést igényel.
- **Kockázat elkerülése (Risk Avoidance)**: Beszüntetjük a kockázatot hordozó tevékenységet. (Pl. nem üzemeltetünk saját levelezőszervert, hanem felhőszolgáltatást veszünk igénybe).

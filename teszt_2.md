# 2. Hét: Ellenőrző Teszt - Kockázatelemzés

Ez a teszt a második heti "Kockázatelemzés" tananyag gyakorlati alkalmazását méri fel a megadott feladatleírás ("M1: A rendelőintézet felmérése") alapján. Válaszaidat a tananyagra és a józan észre alapozd! A megoldásokat a lap alján találod.

---

**1. Kérdés (Vagyonazonosítás)**

Nevezz meg a feladatleírásból legalább egy-egy vagyonelemet az alábbi kategóriákhoz, a megadott Excel-struktúra szerint!

- Szoftver: Orvosi szoftver 
- Hardver: Regi szamitogep os/ levelezo rendszer
- Személy: Orvos/Nővér

---

**2. Kérdés (Sérülékenység azonosítása)**

A feladatleírás `M1.4.2. Rendelői kiszolgáló` szekciója több sérülékenységet is leír. Nevezz meg ezek közül legalább hármat!

---

**3. Kérdés (Szituációs elemzés)**

A leírás szerint a rendelői gépeken a felhasználók (`orvos`) jelszava is `orvos`. A betegnyilvántartó szoftverben pedig a jelszó mező üresen hagyható, és sokan nem is változtatták meg az alapértelmezett `1234` jelszót.

Milyen fenyegetést tesz lehetővé ez a két súlyos hiba, és ez a fenyegetés a CIA-triád melyik elemét sérti leginkább? (Rövid válasz)

Bizalmassagot serti meg leginkabb es ezt a fenygetest is teszi lehetove hogy olyan ember ferhet hozza az adatokhoz akinek nem kene

---

**4. Kérdés (Kockázat becslése)**

Elemezzük a következő kockázatot:
- **Vagyonelem:** `Rendelői szerver`
- **Fenyegetés:** `Hardveres meghibásodás`

A leírás (5+ éves hardver, RAID 0, nincs UPS) és az előadás táblázatai alapján becsüld meg a **Valószínűség (P)** és a **Kár (D)** szintjét (elég a kategória, pl. "Gyakori", "Súlyos"), majd a kockázati mátrix alapján határozd meg a **Kockázat (R)** szintjét! Térj ki mindhárom CIA elemre a kár becslésénél!

Megoldas: Hat a rendelkezesre allas serul ha hardweres meghibasodas tortenne. A valoszinuseget en a nagyon magasba raknam es a kar meg kritikus is lehet. A bizalmassag nem serul hogyha nincs szerver hisz akkor se a jogosult se a jopgosulatlan nem fer hozza. A sertetlkenseg serulhet hisz ameddig nincs szerver az adatok attol meg ugyan ugy valtoznak johet uj beteg vagy tortenhet kezeles es igy mar elternek az adatok a szerveren taroltaktol

---

**5. Kérdés (Kockázatkezelés)**

Az előző kérdésben elemzett "elfogadhatatlan" vagy "lényeges" kockázatra javasolj egy konkrét **kockázatcsökkentő ellenintézkedést**! Milyen beruházást és milyen folyamatos költséget jelentene ez?

Hat egyreszt egy szunetmentes tapegyseg jo lenne, valamint tarhely frissites hogy legalabb raid 1 ben legyenek masolva es a szerver szoftveret is erdemes frissiteni

---

**6. Kérdés (Elmélet a gyakorlatban)**

A `Rendelői szerver` meghibásodik egy péntek délután. Mutasd be egy-egy példán keresztül, mi lehet az **elsődleges, másodlagos és harmadlagos kár** ebben az esetben!

Az elsodlefes kar az lehet hogy a kulon osztalyok kozotti kapcsolat es adatatvitel megszakadhat igy akar kritikus betegek nem kapjak meg a megfelelo gyogyszert stb. Masodlagos hogy a levelezo szerver es a kulsos eleres is megszunik igy nem tudnak uj eszkozoket rendelni vagy uj beteget fogadni a rendszerbe. Harmadlagos pedig a penzugyi kar amit a rendelo szenved az uj szerver beuzemeleseert

---

**7. Kérdés (Elmélet)**

Miért a **kvalitatív (minőségi)** kockázatelemzési módszert (szintekkel, kategóriákkal) használjuk a rendelő példájában a **kvantitatív (mennyiségi)** módszer (konkrét pénzösszegekkel való számolás) helyett? Mi a kvalitatív módszer előnye és hátránya?

Hat a kvalitativ jobban elkulonitheto es nem kell mar akkor elore meghatarozni a penzugyi vonzatat eleg csak a kockazatat. Illetve idovel a penzugyi vonzata valtozhat de a minosegi nem nagyon

---

**8. Kérdés (Szituáció)**

A `M1.7.1. Az épület` leírása szerint a rendelő faajtaja egyszerű kulcsos zárral működik, amit a portán lehet felvenni aláírásért. Milyen két különböző típusú **ellenintézkedést** lehetne itt bevezetni a biztonság növelésére? (Nevezz meg egy technikai és egy adminisztratív intézkedést!)

Hat egyreszt lehetne valami belepteto rendszer ami tenyleg csak az arra jogosult szemelyeket engedi be most a portast konnyebb atverni mint egy chip leolvasot. Emellett ne csak egy egyszeru ajto legyen hanem legyen nagyobb vedelem a biztonsag erdekeben legalabb egy komplexebb zarral felszerelt fem ajto

---

**9. Kérdés (Elmélet)**

A kockázatkezelés során mit jelent a **tudatos kockázatvállalás (risk acceptance)**? Mondj egy példát a rendelő életéből egy olyan kockázatra, amit a menedzsment valószínűleg egyszerűen elfogadna!

Amikor tudja az ember hogy itt kockazatnak van kiteve de a kockazat olyan elenyeszo hogy azt meg elbirja ha megtortenik. Pl a wifi halozat a vendegeknek elerheto jelszo nelkul.

---

**10. Kérdés (Gondolkodtató)**

A leírás szerint az "Alkalmazotti wifi" `WEP` titkosítást használ. Ez ma már percek alatt feltörhető. A kockázatelemzési táblázatban ezt a "Lehallgatás" fenyegetéssel párosítva milyen Kár (D) értéket adnál a **Bizalmasságra (Confidentiality)**, és miért?

Hat kritikusat adnek mert az alkalmazotti wifin a gepek/telok kozott lehet olyan adatcsere is amihez nem kene mas embernek hozzafernie. Igy ezt kritikzusra allitanam

<br><br>
---
<br><br>

## Megoldások

1.  **Szoftver:** Windows 2008 Server, Betegnyilvántartó, Oracle 9 adatbázis motor. **Hardver:** Rendelői szerver, Tűzfal szerver, CISCO kapcsoló. **Személy:** Rendszergazda, Orvos, Pénzügyes.
2.  Lehetséges válaszok: Elavult hardver (5+ éves), a RAID 0 (összefűzés) nem biztosít redundanciát, nincs hibatűrés, a tárhely 20%-a van csak kihasználva (ez nem sérülékenység, csak info), a levelezőszerver 2012 óta nem volt frissítve, gyenge/közös jelszavak az Active Directory-ban, az FTP protokoll használata (nem biztonságos), a betegnyilvántartó alapértelmezett, gyenge jelszava.
3.  **Fenyegetés:** Illetéktelen vagy jogosulatlan hozzáférés a betegadatokhoz (akár más alkalmazottak vagy külső támadók által). **Sértett CIA elem:** Elsődlegesen a **Bizalmasság (Confidentiality)**, mivel bizalmas betegadatokhoz lehet hozzáférni. Másodlagosan a Sértetlenség is sérülhet, ha módosítják az adatokat.
4.  **Valószínűség (P):** **Gyakori**. Az 5+ éves, nem szerver célú hardver, RAID 0-val (ami növeli a hiba esélyét) és UPS nélkül nagy eséllyel meghibásodik. **Kár (D):** A **Rendelkezésre állás** szempontjából **Kritikus**, mert leáll a teljes betegellátás és számlázás. A **Sértetlenség** szempontjából **Súlyos**, mert a RAID 0 miatt adatvesztés történhet. A **Bizalmasság** nem érintett közvetlenül. **Kockázat (R):** A mátrix alapján (Gyakori P + Kritikus D) a kockázat **Elfogadhatatlan**.
5.  **Ellenintézkedés:** Új, szerver-grade hardver beszerzése RAID 1 vagy RAID 5 konfigurációval és szünetmentes tápegységgel (UPS). **Beruházási költség:** A szerver és a UPS ára (több százezer vagy milliós tétel). **Folyamatos költség:** Megnövekedett áramfogyasztás, esetleg karbantartási szerződés díja.
6.  **Elsődleges kár:** A szerver javításának vagy cseréjének költsége. **Másodlagos kár:** Az elveszett adatok helyreállításának költsége és munkaideje, a leállás miatti bevételkiesés. **Harmadlagos kár:** A betegek és partnerek bizalmának elvesztése, a rendelő hírnevének csorbulása.
7.  Azért használjuk a kvalitatív módszert, mert a károkat (pl. egy beteg bizalmának elvesztése) nagyon nehéz vagy lehetetlen **pontos pénzösszegben kifejezni**. **Előnye:** Gyorsabb és egyszerűbb. **Hátránya:** Kevésbé pontos, szubjektívebb, a szintek meghatározása tapasztalatot igényel.
8.  **Technikai intézkedés:** A faajtó lecserélése biztonsági ajtóra, és a kulcsos zár lecserélése beléptető kártyás rendszerre. **Adminisztratív intézkedés:** Szigorú szabályzat (házirend) bevezetése a kulcsok kezelésére (pl. tilos benne hagyni az ajtóban, a kulcsfelvételt szigorúbban dokumentálni).
9.  Olyan ismert, alacsony kockázat elfogadása, amelynek kezelése aránytalanul sokba kerülne. **Példa:** Annak a kockázata, hogy a pénzügyi irodában elromlik a nyomtató. A kár (nem tudnak azonnal számlát nyomtatni) és a valószínűség is alacsony, a menedzsment valószínűleg elfogadja ezt a kockázatot anélkül, hogy tartalék nyomtatót tartana készenlétben.
10. **Kár (D) a Bizalmasságra:** **Kritikus**. A WEP titkosítás elavultsága egy nagyon magas szintű sérülékenység. Ha egy támadó megszerzi a wifi jelszavát ("ERT23zte7"), akkor bejut a belső hálózatba, ahol a betegadatokat tároló szerver is van. Ezáltal a legérzékenyebb információk (betegadatok) bizalmassága kerül közvetlen veszélybe.

# 6. Hét: Ellenőrző Teszt - Programozott Kártevők és a Fenyegetések Fejlődése

Ez a teszt a 6. heti "Programozott Kártevők és a Fenyegetések Fejlődése" tananyagra épül. Válaszaidat az összefoglaló és a tananyag alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (Malware Típusok)**

Mi a fő különbség a **vírusok**, a **férgek** és a **trójai programok** terjedési mechanizmusa között?

Megoldas:  A virusokhoz kell emberi beavatkozas hogy lefussanak, a fergek automatikusan maguktol terjednek a halozati gyengesegeket kihasznalva, a trojai programok artalmatlannak tuno programok mikozben a hasznalatuk kozben ertekes adatokat kuldenek tovabb a letrehozojanak

---

**2. Kérdés (Ransomware)**

Mi az a **ransomware (zsarolóvírus)**, és hogyan működik tipikusan? Mi a fő motivációja a támadóknak?

Megoldas: Lezarja a fajljainkat majd penzert cserebe feloldja. nyilvan fizetni kriptoban kell ami nem lekovetheto illetve az sem biztositek hogy fizetes utan visszakapjuk az adatokat

---

**3. Kérdés (Rootkit)**

Mi a **rootkit** elsődleges célja a fertőzött rendszeren belül? 

Megoldas: Az a feladata hogy eltuntesse azt hogy mas is tartozkodik a gepen igy minden log fajlt es hasonlot elrejt a felhasznalo es antivirus elol is

---

**4. Kérdés (Botnet)**

Mit jelent a **botnet** kifejezés az informatikai biztonságban, és mire használják jellemzően a támadók?

Megoldas: tobb szamitogep felett atveszik az iranyitast de akar a hatterbol is mehet es ezzel terheleses tamadasokat inditanak pl ddos tamadasokat.

---

**5. Kérdés (Spyware és Adware)**

Döntsd el, hogy az alábbi tevékenységek **spyware** vagy **adware** típusú kártevőre jellemzőek-e!
megoldas: 
- a) Billentyűleütések rögzítése és továbbítása: spyware
- b) Nem kívánt felugró ablakok megjelenítése: adware



---

**6. Kérdés (Fertőzési Vektorok)**

Sorolj fel legalább három gyakori fertőzési vektort, amelyen keresztül a kártevők a rendszerekbe juthatnak!

Megoldas:
Ellenorizetlen program letoltese, halozaton belul egy masik geprol, adwarevel vagy egy weboldal bongeszese soran letoltodik a hatterben

---

**7. Kérdés (Fenyegetések Fejlődése)**

Hogyan változott a kártevők fő motivációja a korai "bosszantó" vírusoktól a modern fenyegetésekig (pl. APT)?

Megoldas:
Az apt az hosszan tarto szervezett es egy celpontot kiszemelo tamadas. De az elejen a bosszantastol elindult penzszerzesi lehetosegig, majd utana mar a zero day exploitig kozben volt meg iot kihasznalasa stb

---

**8. Kérdés (Védekezés)**

Nevezz meg legalább három olyan védekezési módszert vagy eszközt, amelyet a kártevők elleni védelemre használnak!

megoldas: S
Virusirto, tuzfal szabalyzat, vpn

---

**9. Kérdés (Social Engineering és Malware)**

Hogyan kapcsolódik a **Social Engineering (társadalmi mérnökség)** a kártevők terjesztéséhez? Adj egy rövid példát!

Megoldas:
Valaki megprobal ravenni arra hogy egy altala eladott pendriveon van egy tok jo szoftver ami megkonnyiti a mindennapjaidat majd amikor bedugod a gepedbe es elinditod a szoftvert mar fent is van a virus

---

**10. Kérdés (Polimorf és Metamorf Kártevők)**

Miért jelentenek kihívást az antivírus szoftverek számára a **polimorf** és **metamorf** kártevők? Magyarázd el röviden a lényegüket!

Megoldas:
Mert a polimorf es a metamorf kartevok a futasuk soran kepesek a sajat kodjukat megvaltoztatni nagyon gyakran meg mielott felismernek vagy amikor mar felismertek es ezzel ismetelten eltunnek

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
-   **Vírusok:** Más programokhoz csatolják magukat, terjedésükhöz emberi beavatkozás (pl. futtatás) szükséges.
-   **Férgek:** Önálló programok, hálózati sérülékenységeket kihasználva automatikusan terjednek (önmagukat másolják).
-   **Trójai programok:** Hasznosnak álcázzák magukat, de a háttérben rosszindulatú tevékenységet végeznek. Nem másolják önmagukat.

**2. Kérdés:**
A **ransomware** (zsarolóvírus) egy olyan kártevő, amely titkosítja a felhasználó adatait vagy lezárja a rendszert, majd váltságdíjat követel az adatok feloldásáért vagy a rendszer feloldásáért. A fő motivációja a támadóknak a **pénzszerzés**.

**3. Kérdés:**
A **rootkit** elsődleges célja, hogy a támadó rejtve maradjon a fertőzött rendszeren belül, elrejtve a saját jelenlétét (fájlokat, folyamatokat, hálózati kapcsolatokat) a rendszeradminisztrátor vagy a biztonsági szoftverek elől.

**4. Kérdés:**
A **botnet** fertőzött számítógépek hálózata (ún. "zombi" gépek), amelyeket a támadó (botmaster) távolról irányít. Jellemzően tömeges támadásokra (pl. DDoS), spam küldésére, adathalászatra, vagy más kártevők terjesztésére használják.

**5. Kérdés:**
a) Billentyűleütések rögzítése és továbbítása: **Spyware**
b) Nem kívánt felugró ablakok megjelenítése: **Adware**

**6. Kérdés:**
1.  E-mail mellékletek (phishing üzenetekben)
2.  Weboldalak (drive-by download, malvertising)
3.  Fertőzött USB meghajtók
4.  Hálózati sérülékenységek kihasználása
5.  Social Engineering (megtévesztés)

**7. Kérdés:**
A kártevők fő motivációja a korai vírusoktól (amelyek gyakran a károkozás, bosszankodás céljával készültek) a modern fenyegetésekig egyre inkább a **pénzügyi haszonszerzés** (pl. adatok lopása, zsarolás, banki csalások), valamint az **információgyűjtés** (kémkedés, ipari titkok megszerzése), illetve a **politikai/állami motivációk** (APT támadások, kritikus infrastruktúrák elleni akciók) felé tolódott el.

**8. Kérdés:**
1.  Antivírus szoftverek (folyamatos frissítéssel)
2.  Tűzfalak (hálózati forgalom szűrése)
3.  Szoftverfrissítések és patch-ek (sérülékenységek javítása)
4.  IDS/IPS rendszerek (behatolás detektálás/megelőzés)
5.  Felhasználói tudatosság és képzés (Social Engineering elleni védelem)

**9. Kérdés:**
A **Social Engineering (társadalmi mérnökség)** az emberek megtévesztésén keresztül (pl. bizalom kiépítése, sürgősség, félelem keltése) veszi rá őket arra, hogy olyan cselekedeteket hajtsanak végre, amelyek veszélyeztetik a biztonságot, például rákattintanak egy fertőzött linkre, megnyitnak egy kártevőt tartalmazó mellékletet, vagy bizalmas információkat adnak ki. **Példa:** Egy banki értesítésnek álcázott e-mail, amely fertőzött mellékletet tartalmaz.

**10. Kérdés:**
-   **Polimorf kártevők**: Képesek megváltoztatni a kódjukat minden egyes fertőzés alkalmával, miközben funkcionalitásuk változatlan marad.
-   **Metamorf kártevők**: Nem csak a kódjukat, hanem a belső szerkezetüket is átírják, komplexebb átalakításokat végeznek.
Mindkettő azért jelent kihívást az antivírus szoftverek számára, mert nehezebb azonosítani őket a hagyományos **szignatúra alapú** detektálási módszerekkel, mivel a kódjuk vagy a szerkezetük folyamatosan változik, így az antivírus adatbázisában lévő ismert mintázatok nem illeszkednek. Általában heurisztikus vagy viselkedés alapú elemzést igényelnek.
# 3. Hét: Ellenőrző Teszt - Kriptológia Alapjai és Klasszikus Rejtjelek

Ez a teszt a 3. heti "Kriptológia Alapjai és Klasszikus Rejtjelek" tananyagra épül. Próbálj meg válaszolni a kérdésekre a tananyag és a gyakorlati példák alapján. A megoldásokat a lap alján találod.

---

**1. Kérdés (Elmélet)**

Mi a Kerckhoffs-elv lényege a kriptográfiában, és miért fontos a modern rejtjelezés szempontjából? (2-3 mondat)

Megoldas: a kriptografia biztonsaganak a kulcson kell mulnia nem pedig a titkosito algoritmuson

---

**2. Kérdés (Caesar Kódolás)**

Titkosítsd a következő nyílt szöveget Caesar-kódolással, a megadott kulccsal! Az ABC az angol ABC, ékezet és szóköz nélkül.

**Nyílt szöveg:** `TITKOS UZENET`
**Kulcs:** `5`

Megoldás: YNYPTX ZEJSJY

---

**3. Kérdés (Caesar Dekódolás)**

Dekódold a következő rejtett szöveget Caesar-kódolással, a megadott kulccsal!

**Rejtett szöveg:** `FWJFWTY`
**Kulcs:** `8`

Megoldas: XOBXOLQ

---

**4. Kérdés (Vigenère Kódolás)**

Titkosítsd a következő nyílt szöveget Vigenère-kódolással, a megadott kulccsal! (Angol ABC, szóköz nélkül)

**Nyílt szöveg:** `HELLO WORLD`
**Kulcs:** `KULCS`

Megoldas: RYWNG GICNV

---

**5. Kérdés (Vigenère Dekódolás)**

Dekódold a következő rejtett szöveget Vigenère-kódolással, a megadott kulccsal! (Angol ABC, szóköz nélkül)

**Rejtett szöveg:** `UGPUMM`
**Kulcs:** `TESZT`

Megoldas: BCXVTT

---

**6. Kérdés (Transzpozíciós Kódolás)**

Titkosítsd a következő nyílt szöveget oszlop-transzpozíciós módszerrel, a megadott kulccsal és kiegészítő karakterrel!

**Nyílt szöveg:** `ADATVEDELEM`
**Kulcs:** `3142` 
**Kiegészítő karakter (padding):** `X`

Megoldas: DTAAEEVDEXLM

---

**7. Kérdés (Transzpozíciós Dekódolás)**

Dekódold a következő rejtett szöveget oszlop-transzpozíciós módszerrel, a megadott kulccsal és a megadott eredeti hosszúsággal!

**Rejtett szöveg:** `LTOEDT`
**Kulcs:** `213`
**Eredeti nyílt szöveg hossza:** `6`

TLODET

---

**8. Kérdés (Blokk-rejtjelezési Módok)**

Magyarázd el röviden, miért veszélyes az **ECB (Electronic Code Book)** blokk-rejtjelezési mód képfájlok titkosításánál, és miért előnyösebb ilyen esetben a **CBC (Cipher Block Chaining)** mód? (2-3 mondat)

Megoldas: Az ECB könnyen feltörhető, hisz ugyan abbol a kepbol mindig ugyan az a kod lesz, a CBC nehezebben feltorheto hiszen mindig az elozo kimenetet xor-ral megvaltoztatjuk majd utan aegy vektorral eltoljuk a lenyeg hogy a vektort cserelgetni kell neha neha

---

**9. Kérdés (Hash Függvények)**

Sorolj fel két alapvető elvárást (tulajdonságot), amit egy kriptográfiai hash függvénynek teljesítenie kell, és magyarázd el a **Születésnapi Paradoxon** jelentőségét a hash függvények biztonsága szempontjából!

Barmilyen szovegbol ugyan olyan hosszu hasht kell keszitenie illetve kerulendo hogy ket kulonbozo szovegnek is ugyan az legyen a hash-je. A szuletesnapi paradoxon azt mondja ki, hogy sokkal hamarabb talalunk utkozest mint gondolnank ezert a hashnek legalabb 140-160 bit hosszunak kell lennie

---

**10. Kérdés (Shannon Transzformáció)**

Shannon két alapvető titkosítási tulajdonságát, a **zavarást (confusion)** és a **szétszóródást (diffusion)**, a gyakorlatban milyen céllal alkalmazzák? (1-2 mondat)

Megoldás: Zavaras: a kulcs es a kuldendo uzenet kozti statisztikai azonossag megszuntetese. Szetszorodas a nyilt szoveg egy bitjenek megvaltoztatasa teljesen mas vegeredmenyhez vezessen

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:** A Kerckhoffs-elv szerint egy kriptográfiai rendszer biztonságának a kulcs titkosságán kell múlnia, nem pedig az algoritmus titkosságán. Ez azért fontos, mert az algoritmusok előbb-utóbb nyilvánosságra kerülhetnek, és csak a titkos kulcsra épülő biztonság garantálja a rendszer ellenállását.

**2. Kérdés:**
Nyílt szöveg: TITKOSUZENET (szóköz nélkül)
Kulcs: 5
T+5 = Y
I+5 = N
T+5 = Y
K+5 = P
O+5 = T
S+5 = X
U+5 = Z
Z+5 = E
E+5 = J
N+5 = S
E+5 = J
T+5 = Y

**Rejtett szöveg:** `YNYPTXZJEJSY`

**3. Kérdés:**
Rejtett szöveg: FWJFWTY
Kulcs: 8 (azaz -8 a dekódoláshoz)
F-8 = X
W-8 = O
J-8 = B
F-8 = X
W-8 = O
T-8 = L
Y-8 = Q

**Nyílt szöveg:** `XOBXO LQ` (Valószínűleg valamilyen értelmes szó volt, pl. `XOBXOLQ`.)

**4. Kérdés:**
Nyílt szöveg: HELLOWORLD (szóköz nélkül)
Kulcs: KULCS (ismétlődik: KULCSKULC)
H+K = 7+10 = 17 = R
E+U = 4+20 = 24 = Y
L+L = 11+11 = 22 = W
L+C = 11+2 = 13 = N
O+S = 14+18 = 32 mod 26 = 6 = G
W+K = 22+10 = 32 mod 26 = 6 = G
O+U = 14+20 = 34 mod 26 = 8 = I
R+L = 17+11 = 28 mod 26 = 2 = C
L+C = 11+2 = 13 = N
D+S = 3+18 = 21 = V

**Rejtett szöveg:** `RYWNGGICNV`

**5. Kérdés:**
Rejtett szöveg: UGPUMM
Kulcs: TESZT (ismétlődik: TESTTE)
U-T = 20-19 = 1 = B
G-E = 6-4 = 2 = C
P-S = 15-18 = -3 mod 26 = 23 = X
U-T = 20-19 = 1 = B
M-T = 12-19 = -7 mod 26 = 19 = T
M-E = 12-4 = 8 = I

**Nyílt szöveg:** `BCXBTI` (Valószínűleg valamilyen értelmes szó volt, pl. `BCXBTI`.)

**6. Kérdés:**
Nyílt szöveg: ADATVEDELEM (11 karakter)
Kulcs: 3142 (4 oszlop)
Hossz: 11, oszlopok száma: 4. A blokk mérete 4, így 3 sorra van szükség (3*4 = 12, egy X padding karakter).
Tördelés:
A D A T
V E D E
L E M X

Kulcs 3142 (oszlopok sorrendje: 3, 1, 4, 2):
1. oszlop (A, V, L)
2. oszlop (D, E, E)
3. oszlop (A, D, M)
4. oszlop (T, E, X)

Rejtett szöveg olvasása a kulcs sorrendje szerint (3. oszlop, 1. oszlop, 4. oszlop, 2. oszlop):
(ADM) (AVL) (TEX) (DEE)

**Rejtett szöveg:** `ADMAVLTEXDEE`

**7. Kérdés:**
Rejtett szöveg: LTOEDT (6 karakter)
Kulcs: 213 (3 oszlop). Hossz 6, 3 oszlop, tehát 2 sor.
Az oszlopok eredeti sorrendje a kulcs alapján:
Oszlop 1: kulcs '2'
Oszlop 2: kulcs '1'
Oszlop 3: kulcs '3'

Ahhoz, hogy visszaállítsuk az eredeti sorrendet, a 2-1-3 kulcs inverzét kell alkalmaznunk, ami megadja, hogy honnan hova kerültek az oszlopok:
Az olvasott sorrend: 2, 1, 3
Az eredeti sorrend: 1, 2, 3

Tehát az eredeti 1-es oszlop a 2. helyre került, a 2-es az 1. helyre, a 3-as a 3. helyre.
A rejtett szöveg felosztása 3 oszlopra (6 karakter / 3 oszlop = 2 sor):
1. oszlop: LT
2. oszlop: OE
3. oszlop: DT

A kulcs (213) azt jelenti, hogy az oszlopokat ebben a sorrendben (2, 1, 3) kell összerakni. Ahhoz, hogy visszaállítsuk az eredeti sorrendet, az olvasás inverzét kell alkalmaznunk, azaz:
- A rejtett szöveg 1. oszlopa (L, O) az eredeti 2. oszlop volt.
- A rejtett szöveg 2. oszlopa (T, E) az eredeti 1. oszlop volt.
- A rejtett szöveg 3. oszlopa (D, T) az eredeti 3. oszlop volt.

Eredeti oszlopok visszaállítása:
1. oszlop: T D
2. oszlop: L O
3. oszlop: E T

Nyílt szöveg olvasása soronként: `TOLDE T`

**Nyílt szöveg:** `TOLDET`

**8. Kérdés:** Az ECB mód képfájlok titkosításánál veszélyes, mert az azonos színű (azonos nyílt szövegű) blokkokból azonos rejtett blokkok jönnek létre, így a kép eredeti mintázata részben felismerhető marad. A CBC mód ezzel szemben minden blokkot az előző rejtett blokkal XOR-oz, így az azonos nyílt blokkokból is különböző rejtett blokkok keletkeznek, ami teljesen elrejti a mintázatot, és biztonságosabb.

**9. Kérdés:**
1.  **Egyirányúság (One-Wayness)**: A hash értékből gyakorlatilag lehetetlen visszafejteni az eredeti bemenetet (preimage resistance).
2.  **Ütközés-ellenállóság (Collision Resistance)**: Gyakorlatilag lehetetlen két különböző bemenetet találni, amelyeknek ugyanaz a hash értéke.
A **Születésnapi Paradoxon** azt mutatja be, hogy sokkal kevesebb próbálkozással (kb. a hash kimenet hosszának négyzetgyökével arányosan, `2^(n/2)`), mint gondolnánk, találhatunk ütközést egy hash függvényben. Ezért a hash függvények kimeneti méretének jóval nagyobbnak kell lennie, mint a támadók számítási kapacitása (pl. legalább 128-160 bit), hogy az ütközések keresése továbbra is számítási szempontból lehetetlen legyen.

**10. Kérdés:** Shannon **zavarás (confusion)** tulajdonsága a nyílt szöveg és a rejtett szöveg közötti, valamint a kulcs és a rejtett szöveg közötti statisztikai kapcsolat elrejtésére törekszik, hogy ne lehessen egyszerűen kapcsolatot találni. A **szétszóródás (diffusion)** célja, hogy a nyílt szöveg egyetlen bitjének megváltoztatása a rejtett szöveg minél több bitjét befolyásolja, ezzel elrejtve a nyílt szöveg szerkezetét. Ezt a két elvet a titkosítási algoritmusok robosztusságának növelésére alkalmazzák.
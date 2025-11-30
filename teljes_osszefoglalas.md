# Informatikai Biztonság - Teljes Tematikus Összefoglaló

Ez a dokumentum a féléves "Informatikai biztonság" tárgy teljes elméleti és gyakorlati anyagát foglalja össze, különös tekintettel a zárthelyi dolgozaton (ZH) várható feladattípusokra.

---

## I. Biztonsági Alapfogalmak (CIA és AAA)

Minden biztonsági intézkedés alapja a **CIA triád** és az **AAA modell**.

### 1. CIA Triád (A védelem céljai)
*   **Bizalmasság (Confidentiality):** Csak az férhet hozzá az adathoz, akinek joga van hozzá.
    *   *Sértése:* Adatszivárgás, jelszólopás, lehallgatás.
    *   *Védelem:* Titkosítás, jogosultságkezelés.
*   **Sértetlenség (Integrity):** Az adat nem módosulhat illetéktelenül (véletlenül vagy szándékosan). Pontos és teljes marad.
    *   *Sértése:* Adatok átírása, vírus általi fertőzés, hibás átvitel.
    *   *Védelem:* Hash függvények (ellenőrző összegek), digitális aláírás, mentések.
*   **Rendelkezésre állás (Availability):** Az adat/rendszer elérhető legyen, amikor a jogosult felhasználónak szüksége van rá.
    *   *Sértése:* DoS (Denial of Service) támadás, hardverhiba, áramszünet.
    *   *Védelem:* Redundancia (RAID, cluster), szünetmentes táp (UPS), DDoS védelem.

### 2. AAA Modell (Hozzáférés-vezérlés)
1.  **Identification (Azonosítás):** "Ki vagy te?" (Pl. Felhasználónév beírása).
2.  **Authentication (Hitelesítés):** "Bizonyítsd be!" (Pl. Jelszó, ujjlenyomat, token).
3.  **Authorization (Felhatalmazás/Jogosultság):** "Mit tehetsz meg?" (Pl. Olvasás, írás, futtatás jogok).
4.  **Accounting (Elszámoltathatóság/Naplózás):** "Mit tettél?" (Logok: ki, mikor, mit csinált).

---

## II. Kockázatelemzés (Gyakorlati Útmutató)

A ZH-n várhatóan egy esettanulmány alapján kell kockázatelemzést végezni.

### Fogalmak
*   **Vagyonelem (Asset):** Bármi, ami értéket képvisel (Hardver, Szoftver, Adat/Információ, Ember, Szolgáltatás).
*   **Fenyegetés (Threat):** Potenciális esemény, ami kárt okozhat (pl. tűz, hacker, vírus, felhasználói hiba).
*   **Sérülékenység (Vulnerability):** Gyengeség, amit a fenyegetés kihasznál (pl. patch-eletlen Windows, gyenge jelszó).
*   **Kockázat (Risk):** Annak valószínűsége, hogy a fenyegetés kihasználja a sérülékenységet és kárt okoz.
    *   *Képlet:* **Kockázat = Valószínűség × Hatás (Kárérték)**

### Step-by-Step Megoldás (ZH Feladathoz)

**1. Lépés: Vagyonelemek azonosítása**
Olvasd el a szöveget és gyűjtsd ki a vagyonelemeket kategóriák szerint:
*   **Információ:** Betegadatok, Jelszavak, Pénzügyi táblázatok.
*   **Szoftver:** Windows Server 2008, Számlázó program, Oracle adatbázis.
*   **Hardver:** Szerver PC, Recepciós laptop, Router.
*   **Ember:** Rendszergazda, Orvos, Recepciós.
*   **Infrastruktúra:** Szerverszoba hűtés, Internet kapcsolat.

**2. Lépés: Fenyegetések párosítása**
Melyik vagyonelemet mi fenyegeti?
*   *Szerver:* Hardverhiba, Túlmelegedés.
*   *Adatbázis:* SQL Injection, Véletlen törlés.
*   *Laptop:* Ellopás, Kávé kiöntés.

**3. Lépés: Kockázati Mátrix (Számolás)**
Általában megadnak egy skálát (pl. 1-5).
*   **Valószínűség (V):** Milyen gyakran fordulhat elő? (1: soha, 5: nagyon gyakran).
*   **Hatás/Kár (H):** Mekkora a baj, ha bekövetkezik? (1: jelentéktelen, 5: kritikus/csőd).
*   **Kockázati érték (K):** `K = V × H`.

*Példa táblázat:*

| Vagyonelem | Fenyegetés | Valószínűség (1-5) | Hatás (1-5) | Kockázat (V×H) | Intézkedés |
| :--- | :--- | :---: | :---: | :---: | :--- |
| Betegadatok | Adatszivárgás (Hacker) | 2 | 5 | **10** (Magas) | Titkosítás, Tűzfal |
| Szerver PC | Hardverhiba | 3 | 4 | **12** (Magas) | Redundancia, Backup |
| Recepciós gép | Kávé kiöntés | 4 | 2 | **8** (Közepes) | Házirend, Csere gép |

**4. Lépés: Kockázatkezelési döntés**
Mit kezdünk a kockázattal?
*   **Csökkentés (Mitigate):** Védelmi intézkedés bevezetése (pl. vírusirtó).
*   **Elkerülés (Avoid):** A tevékenység megszüntetése (pl. nem használunk wifit).
*   **Áthárítás (Transfer):** Biztosítás kötése vagy kiszervezés (outsourcing).
*   **Elfogadás (Accept):** Ha a védelem drágább, mint a kár (csak alacsony kockázatnál!).

---

## III. Kriptográfia és Kódolás (Számolási Példák)

A ZH legkritikusabb része a titkosítási eljárások papíron történő elvégzése.

### 1. Caesar-kód (Monoalfabetikus helyettesítés)
Minden betűt eltolunk az ábécében egy fix `k` értékkel.
*   **Kódolás:** `C = (M + k) mod 26`
*   **Dekódolás:** `M = (C - k) mod 26`

**Példa:**
*   Üzenet: `HELLO`
*   Kulcs (eltolás): `3`
*   *Megoldás:*
    *   H -> I, J, **K**
    *   E -> F, G, **H**
    *   L -> M, N, **O**
    *   L -> M, N, **O**
    *   O -> P, Q, **R**
*   Eredmény: `KHOOR`

### 2. Csoportos helyettesítés (Vigenère Táblázattal)
A feladatban egy **standard Vigenère táblát** (Tabula Recta) kell használni a kódoláshoz és dekódoláshoz. A táblázat a következőképpen néz ki (a mellékelt kép alapján):

A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z
B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A
C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B
D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C
E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D
F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E
G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F
H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G
I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H
J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I
K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J
L	M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K
M	N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L
N	O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M
O	P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N
P	Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O
Q	R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P
R	S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q
S	T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R
T	U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S
U	V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T
V	W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U
W	X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V
X	Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W
Y	Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X
Z	A	B	C	D	E	F	G	H	I	J	K	L	M	N	O	P	Q	R	S	T	U	V	W	X	Y

**Kódolás menete (Pl. `ALMA` kulcs: `KEY`):**
1.  Írd fel az üzenetet, és alá ismételve a kulcsot:
    ```text
    Üzenet: A L M A
    Kulcs:  K E Y K
    ```
2.  Az egyes betűpárokhoz (Kulcs betűje, Üzenet betűje) keresd meg a metszéspontot a táblázatban.
    *   `A` (Üzenet) + `K` (Kulcs): Keresd a `K` sorban az `A` oszlopot -> **K**.
    *   `L` (Üzenet) + `E` (Kulcs): Keresd az `E` sorban az `L` oszlopot -> **P**.
    *   `M` (Üzenet) + `Y` (Kulcs): Keresd az `Y` sorban az `M` oszlopot -> **K**.
    *   `A` (Üzenet) + `K` (Kulcs): Keresd a `K` sorban az `A` oszlopot -> **K**.
*   **Titkosított üzenet:** `KPKK`

**Dekódolás menete (Pl. `KPKK` kulcs: `KEY`):**
1.  Ismerjük a kulcsot (`KEY`) és a rejtett szöveget (`KPKK`).
2.  Az egyes rejtett betűkhöz és a kulcs betűjéhez keresd meg a nyílt betűt a táblázatban.
    *   `K` (Titkosított) + `K` (Kulcs): Keresd a `K` sorban a `K` betűt. A betűhöz tartozó oszlop fejléce -> **A**.
    *   `P` (Titkosított) + `E` (Kulcs): Keresd az `E` sorban a `P` betűt. A betűhöz tartozó oszlop fejléce -> **L**.
    *   `K` (Titkosított) + `Y` (Kulcs): Keresd az `Y` sorban a `K` betűt. A betűhöz tartozó oszlop fejléce -> **M**.
    *   `K` (Titkosított) + `K` (Kulcs): Keresd a `K` sorban a `K` betűt. A betűhöz tartozó oszlop fejléce -> **A**.
*   **Eredmény:** `ALMA`

### 3. Keverő Kódolás (Transzpozíció / Oszlopcsere) - FONTOS!
A betűk nem változnak, csak a sorrendjük.

**Step-by-Step Példa (ZH típusú):**
*   **Üzenet:** `TITKOSUZENET` (12 karakter)
*   **Kulcs:** `ZEBRA` (5 karakter)
*   **Kiegészítő:** `X` (ha nem osztható a hossz a kulcs hosszával)

1.  **Táblázat mérete:** Üzenet hossza 12. Kulcs hossza 5. Kell `12 / 5` -> 3 sor. (3*5 = 15 cella).
    *   Szükséges kiegészítés: 15 - 12 = 3 db `X`.
    *   Új üzenet: `TITKOSUZENETXXX`

2.  **Oszlopok sorrendje:** A kulcs (`ZEBRA`) betűinek ábécé sorrendje:
    *   A - 1.
    *   B - 2.
    *   E - 3.
    *   R - 4.
    *   Z - 5.
    *   Sorrend: `5 3 2 4 1` (Z E B R A)

3.  **Beírás:** Írd be az üzenetet **sorfolytonosan**:

| Z (5) | E (3) | B (2) | R (4) | A (1) |
| :---: | :---: | :---: | :---: | :---: |
| **T** | **I** | **T** | **K** | **O** |
| **S** | **U** | **Z** | **E** | **N** |
| **E** | **T** | **X** | **X** | **X** |

4.  **Kiolvasás (Kódolás):** Olvasd ki az oszlopokat a fenti sorszámok (1, 2, 3...) szerint, **fentről lefelé**:
    *   1-es (A alatt): `ONX`
    *   2-es (B alatt): `TZX`
    *   3-as (E alatt): `IUT`
    *   4-es (R alatt): `KEX`
    *   5-ös (Z alatt): `TSE`
    *   **Titkosított szöveg:** `ONXTZXIUTKEXTSE`

5.  **Dekódolás (Visszafelé):**
    *   Tudod a kulcsot (`ZEBRA` -> 5,3,2,4,1) és a titkosított szöveg hosszát (15).
    *   Kiszámolod a sorok számát: 15 / 5 = 3 sor.
    *   Tudod, hogy az `ONX` az 1-es oszlopba jön, a `TZX` a 2-esbe, stb.
    *   Beírod oszloponként a táblázatba a megfelelő helyre.
    *   Kiolvasod **sorfolytonosan**.

### 4. RSA (Aszimmetrikus titkosítás) - Számolás
Két kulcs van: Nyilvános (titkosít) és Privát (felold).

**Step-by-Step Számolás (Kis számokkal):**

1.  **Kulcsgenerálás:**
    *   Válassz két prím, `p` és `q`. Legyen `p=3`, `q=11`.
    *   Számold ki a modulust: `N = p * q` = 3 * 11 = **33**.
    *   Számold ki a Phi értéket: `phi(N) = (p-1) * (q-1)` = 2 * 10 = **20**.
    *   Válassz egy `e` (nyilvános kitevő) értéket, ami:
        *   1 < e < phi(N)
        *   `e` relatív prím phi(N)-hez (lnko(e, 20) = 1).
        *   Legyen `e = 3`. (3 és 20 relatív prímek).
        *   **Nyilvános kulcs (Public Key):** `(N=33, e=3)`
    *   Számold ki a `d` (privát kitevő) értéket:
        *   `d * e ≡ 1 (mod phi(N))`
        *   `d * 3 ≡ 1 (mod 20)`
        *   Keressünk olyan számot, amit 3-mal szorozva és 20-szal osztva 1 a maradék.
        *   3 * 7 = 21. 21 osztva 20-szal = 1, maradék 1.
        *   Tehát `d = 7`.
        *   **Privát kulcs (Private Key):** `(N=33, d=7)`

2.  **Kódolás (Titkosítás):**
    *   Üzenet `M = 4` (Fontos: M < N).
    *   Képlet: `C = M^e (mod N)`
    *   `C = 4^3 (mod 33)` = 64 (mod 33).
    *   64-ben a 33 megvan 1-szer (marad 31).
    *   **Titkosított üzenet (C):** **31**

3.  **Dekódolás:**
    *   Képlet: `M = C^d (mod N)`
    *   `M = 31^7 (mod 33)` ... ezt papíron nehéz, de a matek működik: visszakapjuk a 4-et.
    *   *Tipp papíron számoláshoz:* Használd a hatványozás tulajdonságait vagy ismételt négyzetre emelést, ha nagyok a számok, de ZH-n általában kicsiket adnak.

### 5. Komplex Feladat: Előpermutáció + Caesar + Utópermutáció (Transzpozíció alapú)
Ez egy összetett eljárás, ahol a szöveget először keverjük (előpermutáció), majd eltoljuk (Caesar), végül a keverést "visszacsináljuk" (utópermutáció). A ZH-n transzpozíciós kódolás formájában várható.

**A) Kódolás (Oda irány)**
*   **Üzenet:** `VEDELEM`
*   **Kulcs (Előpermutáció/Utópermutáció):** `312` (Háromszög/Oszlopos)
*   **Kulcs (Caesar):** `+1`

**1. Lépés: Előpermutáció (Transzpozíció)**
*   Kulcs hossza 3 (`312`). Üzenet hossza 7.
*   Kiegészítjük, hogy osztható legyen 3-mal -> `VEDELEMXX` (9 karakter).
*   Beírjuk sorfolytonosan:
    ```text
    3 1 2  (Kulcs)
    -----
    V E D
    E L E
    M X X
    ```
*   Kiolvassuk oszloponként (1, 2, 3 sorrendben):
    *   1-es oszlop: `ELX`
    *   2-es oszlop: `DEX`
    *   3-as oszlop: `VEM`
*   Transzponált eredmény: `ELXDEXVEM`

**2. Lépés: Caesar kódolás (+1)**
*   Minden betűt eggyel eltolunk (`A->B`, `Z->A`).
    *   E->F, L->M, X->Y
    *   D->E, E->F, X->Y
    *   V->W, E->F, M->N
*   Caesar eredmény: `FMYEFYWFN`

**3. Lépés: Utópermutáció (Transzpozíció)**
*   Most a Caesar eredményt (`FMYEFYWFN`) újra transzponáljuk, ugyanazzal a kulccsal (`312`).
*   Beírjuk sorfolytonosan:
    ```text
    3 1 2
    -----
    F M Y
    E F Y
    W F N
    ```
*   Kiolvassuk oszloponként (1, 2, 3 sorrendben):
    *   1-es oszlop: `MYF`
    *   2-es oszlop: `YFN`
    *   3-as oszlop: `FEW`
*   **Végeredmény:** `MYFYFNFEW`

---

**B) Dekódolás (Vissza irány)**
*   **Titkosított szöveg:** `MYFYFNFEW`
*   **Kulcsok:** Ugyanazok (`312` és `+1`).

A dekódolás az egyes lépések inverzének fordított sorrendben történő alkalmazását jelenti:
1.  **Inverz Utópermutáció (Transzpozíció dekódolása):**
    *   A `MYFYFNFEW` szöveget visszarendezzük a transzpozíciós kulccsal (`312`).
    *   Tudjuk, hogy 3 oszlop (3,1,2), 3 sor.
    *   Az oszlopok a kulcs szerinti sorrendben lettek kiolvasva. Tehát az első 3 betű (`MYF`) az 1-es oszlop tartalma, a következő 3 betű (`YFN`) a 2-es oszlop tartalma, és az utolsó 3 betű (`FEW`) a 3-as oszlop tartalma.
    *   Így néz ki az oszlopokból felépítve (kulcs: 3 1 2):
    ```text
    3(F E W) 1(M Y F) 2(Y F N) -- oszloponként beolvasva
    ```
    *   Visszaállítjuk a táblázatot:
    ```text
    F M Y
    E Y F
    W F N
    ```
    *   Sorfolytonosan kiolvasva kapjuk az Utópermutáció előtti szöveget: `FMYEFYWFN`

2.  **Caesar visszfejtés (-1):**
    *   Minden betűt eggyel visszatolunk.
    *   F->E, M->L, Y->X
    *   E->D, F->E, Y->X
    *   W->V, F->E, N->M
    *   Eredmény: `ELXDEXVEM`

3.  **Inverz Előpermutáció (Transzpozíció dekódolása):**
    *   Az `ELXDEXVEM` szöveget dekódoljuk a transzpozíciós kulccsal (`312`).
    *   Tudjuk, hogy 3 oszlop, 3 sor.
    *   Az oszlopok a kulcs szerinti sorrendben lettek kiolvasva. Tehát az első 3 betű (`ELX`) az 1-es oszlop tartalma, a következő 3 betű (`DEX`) a 2-es oszlop tartalma, és az utolsó 3 betű (`VEM`) a 3-as oszlop tartalma.
    *   Visszaállítjuk a táblázatot:
    ```text
    V E D
    E L E
    M X X
    ```
    *   Sorfolytonosan kiolvasva: `VEDELEMXX`.
    *   Kiegészítők levágása -> **Eredeti üzenet:** `VEDELEM`.
A betűk nem változnak, csak a sorrendjük.

**Step-by-Step Példa (ZH típusú):**
*   **Üzenet:** `TITKOSUZENET` (12 karakter)
*   **Kulcs:** `ZEBRA` (5 karakter)
*   **Kiegészítő:** `X` (ha nem osztható a hossz a kulcs hosszával)

1.  **Táblázat mérete:** Üzenet hossza 12. Kulcs hossza 5. Kell `12 / 5` -> 3 sor. (3*5 = 15 cella).
    *   Szükséges kiegészítés: 15 - 12 = 3 db `X`.
    *   Új üzenet: `TITKOSUZENETXXX`

2.  **Oszlopok sorrendje:** A kulcs (`ZEBRA`) betűinek ábécé sorrendje:
    *   A - 1.
    *   B - 2.
    *   E - 3.
    *   R - 4.
    *   Z - 5.
    *   Sorrend: `5 3 2 4 1` (Z E B R A)

3.  **Beírás:** Írd be az üzenetet **sorfolytonosan**:

| Z (5) | E (3) | B (2) | R (4) | A (1) |
| :---: | :---: | :---: | :---: | :---: |
| **T** | **I** | **T** | **K** | **O** |
| **S** | **U** | **Z** | **E** | **N** |
| **E** | **T** | **X** | **X** | **X** |

4.  **Kiolvasás (Kódolás):** Olvasd ki az oszlopokat a fenti sorszámok (1, 2, 3...) szerint, **fentről lefelé**:
    *   1-es (A alatt): `ONX`
    *   2-es (B alatt): `TZX`
    *   3-as (E alatt): `IUT`
    *   4-es (R alatt): `KEX`
    *   5-ös (Z alatt): `TSE`
    *   **Titkosított szöveg:** `ONXTZXIUTKEXTSE`

5.  **Dekódolás (Visszafelé):**
    *   Tudod a kulcsot (`ZEBRA` -> 5,3,2,4,1) és a titkosított szöveg hosszát (15).
    *   Kiszámolod a sorok számát: 15 / 5 = 3 sor.
    *   Tudod, hogy az `ONX` az 1-es oszlopba jön, a `TZX` a 2-esbe, stb.
    *   Beírod oszloponként a táblázatba a megfelelő helyre.
    *   Kiolvasod **sorfolytonosan**.

### 4. RSA (Aszimmetrikus titkosítás) - Számolás
Két kulcs van: Nyilvános (titkosít) és Privát (felold).

**Step-by-Step Számolás (Kis számokkal):**

1.  **Kulcsgenerálás:**
    *   Válassz két prím, `p` és `q`. Legyen `p=3`, `q=11`.
    *   Számold ki a modulust: `N = p * q` = 3 * 11 = **33**.
    *   Számold ki a Phi értéket: `phi(N) = (p-1) * (q-1)` = 2 * 10 = **20**.
    *   Válassz egy `e` (nyilvános kitevő) értéket, ami:
        *   1 < e < phi(N)
        *   `e` relatív prím phi(N)-hez (lnko(e, 20) = 1).
        *   Legyen `e = 3`. (3 és 20 relatív prímek).
        *   **Nyilvános kulcs (Public Key):** `(N=33, e=3)`
    *   Számold ki a `d` (privát kitevő) értéket:
        *   `d * e ≡ 1 (mod phi(N))`
        *   `d * 3 ≡ 1 (mod 20)`
        *   Keressünk olyan számot, amit 3-mal szorozva és 20-szal osztva 1 a maradék.
        *   3 * 7 = 21. 21 osztva 20-szal = 1, maradék 1.
        *   Tehát `d = 7`.
        *   **Privát kulcs (Private Key):** `(N=33, d=7)`

2.  **Kódolás (Titkosítás):**
    *   Üzenet `M = 4` (Fontos: M < N).
    *   Képlet: `C = M^e (mod N)`
    *   `C = 4^3 (mod 33)` = 64 (mod 33).
    *   64-ben a 33 megvan 1-szer (marad 31).
    *   **Titkosított üzenet (C):** **31**

3.  **Dekódolás:**
    *   Képlet: `M = C^d (mod N)`
    *   `M = 31^7 (mod 33)` ... ezt papíron nehéz, de a matek működik: visszakapjuk a 4-et.
    *   *Tipp papíron számoláshoz:* Használd a hatványozás tulajdonságait vagy ismételt négyzetre emelést, ha nagyok a számok, de ZH-n általában kicsiket adnak.

### 5. Komplex Feladat: Transzpozíció + Caesar + Detranszpozíció (Oda-vissza)
Ez egy összetett eljárás, ahol a szöveget először keverjük, majd eltoljuk, végül a keverést "visszacsináljuk".

**A) Kódolás (Oda irány)**
*   **Üzenet:** `VEDELEM`
*   **Kulcs (Transzpozíció):** `312` (Háromszög/Oszlopos)
*   **Kulcs (Caesar):** `+1`

**1. Lépés: Transzpozíció (Keverés)**
*   Kulcs hossza 3 (`312`). Üzenet hossza 7.
*   Kiegészítjük, hogy osztható legyen 3-mal -> `VEDELEMXX` (9 karakter).
*   Beírjuk sorfolytonosan:
    ```text
    3 1 2  (Kulcs)
    -----
    V E D
    E L E
    M X X
    ```
*   Kiolvassuk oszloponként (1, 2, 3 sorrendben):
    *   1-es oszlop: `ELX`
    *   2-es oszlop: `DEX`
    *   3-as oszlop: `VEM`
*   Transzponált eredmény: `ELXDEXVEM`

**2. Lépés: Caesar kódolás (+1)**
*   Minden betűt eggyel eltolunk (`A->B`, `Z->A`).
    *   E->F, L->M, X->Y
    *   D->E, E->F, X->Y
    *   V->W, E->F, M->N
*   Caesar eredmény: `FMYEFYWFN`

**3. Lépés: Detranszpozíció (Visszakereverés)**
*   Most a Caesar eredményt (`FMYEFYWFN`) visszafejtjük a transzpozíciós kulccsal (`312`).
*   Ez azt jelenti, hogy **oszloponként írjuk be** a helyére, és **sorfolytonosan olvassuk ki**.
*   Tudjuk a kulcsot (`312`) és a hosszat (9). 3 oszlop, 3 sor.
    *   Az 1-es oszlopba jön az első 3 betű: `FMY`
    *   A 2-es oszlopba jön a köv. 3 betű: `EFY`
    *   A 3-as oszlopba jön az utolsó 3 betű: `WFN`
    ```text
    3 1 2
    -----
    W F E
    F M F
    N Y Y
    ```
*   Kiolvasás sorfolytonosan: `WFEFMFNYY`.
*   **Végeredmény:** `WFEFMFNYY`

---

**B) Dekódolás (Vissza irány)**
*   **Titkosított szöveg:** `WFEFMFNYY`
*   **Kulcsok:** Ugyanazok (`312` és `+1`).

**1. Lépés: Transzpozíció (Ismét!)**
*   A dekódoláshoz először újra végrehajtjuk a transzpozíciót a titkosított szövegen, hogy előkészítsük a Caesar visszafejtéshez.
*   Beírás sorfolytonosan:
    ```text
    3 1 2
    -----
    W F E
    F M F
    N Y Y
    ```
*   Kiolvasás oszloponként (1, 2, 3):
    *   1-es: `FMY`
    *   2-es: `EFY`
    *   3-as: `WFN`
*   Eredmény: `FMYEFYWFN` (Látható, hogy visszakaptuk a Caesar kódolt szöveget).

**2. Lépés: Caesar visszfejtés (-1)**
*   Minden betűt eggyel visszatolunk.
    *   F->E, M->L, Y->X
    *   E->D, F->E, Y->X
    *   W->V, F->E, N->M
*   Eredmény: `ELXDEXVEM` (Visszakaptuk a transzponált nyílt szöveget).

**3. Lépés: Detranszpozíció**
*   Visszaírjuk oszloponként, kiolvassuk sorfolytonosan.
    *   1-es oszlopba (első 3 betű): `ELX`
    *   2-es oszlopba (köv. 3 betű): `DEX`
    *   3-as oszlopba (utolsó 3 betű): `VEM`
    ```text
    3 1 2
    -----
    V E D
    E L E
    M X X
    ```
*   Kiolvasás sorfolytonosan: `VEDELEMXX`.
*   Kiegészítők levágása -> **Eredeti üzenet:** `VEDELEM`.

---

## IV. Hálózatbiztonság és Tűzfalak (Gyakorlat)

### Tűzfal típusok
*   **Csomagszűrő (Packet Filtering):** Csak a fejlécet nézi (IP cím, Port, Protokoll). Gyors, de nem lát bele az adatba. (Stateless vagy Stateful).
*   **Alkalmazás szintű (Application Proxy):** Érti az alkalmazás nyelvét (pl. HTTP, FTP). Bele tud nézni a csomag tartalmába (pl. víruskeresés), de lassabb.

### DMZ (Demilitarizált Zóna)
Olyan alhálózat, amely a védett belső hálózat (LAN) és a veszélyes külső hálózat (Internet) között helyezkedik el.
*   **Ide tesszük:** Publikus szerverek (Webszerver, Mail szerver), amiket az internetről el kell érni.
*   **Nem ide tesszük:** Belső adatbázis, Belső fájlszerver, Kliens gépek.

### Szabályrendszer (Rule Base) - Gyakorlati példa
A tűzfal fentről lefelé halad. Az **első** illeszkedő szabálynál megáll!

**Feladat:** Engedjük ki a belső hálót a webre, a DMZ webszervert érjék el kintről, de minden mást tiltsunk.

| Sor | Forrás (Source) | Cél (Destination) | Szolgáltatás (Service/Port) | Akció (Action) | Magyarázat |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1. | Belső Háló (LAN) | Internet (Any) | HTTP, HTTPS, DNS | **Allow** | Dolgozók netezhetnek. |
| 2. | Internet (Any) | DMZ Webszerver (Public IP) | HTTP, HTTPS | **Allow** | Publikus weboldal elérése. |
| 3. | DMZ Webszerver | Belső Adatbázis | SQL (3306) | **Allow** | Webszerver lekérdezi az adatokat. |
| 4. | Any | Any | Any | **Deny** | **Mindig ez az utolsó!** (Default Deny). |

---

## V. Operációs Rendszer Biztonság (Jogosultságkezelés)

### Windows Jogosultságok (NTFS vs Share)
Két szinten szabályozzuk a fájlelérést hálózaton:
1.  **Megosztási (Share) jogok:** Csak hálózati eléréskor érvényes. (Általában: "Everyone - Full Control" vagy "Change", és szigorítás az NTFS-nél).
2.  **NTFS (Fájlrendszer) jogok:** Helyi és hálózati eléréskor is érvényes. **Ez a mérvadóbb!**
    *   *Öröklődés:* A fájlok öröklik a mappa jogait, hacsak le nem tiltjuk.
    *   *Jogok:* Read, Write, Modify (Törölni is tud!), Full Control (Jogokat is állíthat!).
    *   *Szabály:* A **legszigorúbb** érvényesül a Share és NTFS eredőjéből.

### Active Directory (AD) - Címtár
Központi adatbázis a felhasználókról és gépekről.
*   **Domain Controller (DC):** A szerver, ami az AD-t futtatja.
*   **OU (Organizational Unit):** Szervezeti egység (pl. "Pénzügy", "IT"). Erre lehet **GPO**-t (Csoportházirendet) kötni.
*   **GPO (Group Policy Object):** Központi beállítások (pl. jelszóerősség, háttérkép, tiltott programok).
    *   *Alkalmazási sorrend:* Local -> Site -> Domain -> OU (LSDOU). Az utolsó "nyer" (felülírja az előzőt).

### Gyakorlati Feladat (Mappastruktúra)
*   **Feladat:** Hozz létre mappákat a részlegeknek, csak ők férjenek hozzá.
*   **Megoldás:**
    1.  Létrehozol csoportokat az AD-ben: `G_Penzugy`, `G_IT`.
    2.  Felveszed a felhasználókat a csoportokba.
    3.  Mappa létrehozása: `C:\Adatok\Penzugy`.
    4.  Jobb klikk -> Properties -> Security -> Edit.
    5.  Töröld ki a `Users`-t (hogy ne lássa mindenki).
    6.  Add hozzá: `G_Penzugy` -> Modify jog. `Administrators` -> Full Control.

---

## VI. Webalkalmazások Biztonsága

### Leggyakoribb Támadások (OWASP)
1.  **SQL Injection (SQLi):** A támadó SQL parancsot szúr be a beviteli mezőbe (pl. felhasználónév), amit az adatbázis végrehajt.
    *   *Példa:* User: `' OR '1'='1` -> Ez mindig igaz, így jelszó nélkül beléphet.
    *   *Védelem:* Paraméterezett lekérdezések (Prepared Statements) használata, bemenet szűrése.
2.  **Cross-Site Scripting (XSS):** A támadó JavaScript kódot injektál az oldalba, ami más felhasználók böngészőjében fut le (pl. ellopja a session cookie-t).
    *   *Védelem:* Bemenet ellenőrzése (Validation) és kimenet kódolása (Escaping/Encoding) - pl. `<` helyett `&lt;`.

### Biztonsági Tesztelés (AppScan)
*   Automatizált eszköz webes sérülékenységek keresésére.
*   Feltérképezi az oldalt (Crawling) és támadásokat szimulál (Testing).

---

## VII. Üzemeltetés, Adatvédelem és Kártevők

### Kártevők (Malware)
*   **Vírus:** Fájlhoz tapad, emberi indítás kell neki.
*   **Féreg (Worm):** Önállóan terjed hálózaton, nem kell emberi beavatkozás.
*   **Trójai:** Hasznosnak látszó program, de kártékony kód van benne. Hátsó kaput (Backdoor) nyithat.
*   **Ransomware (Zsarolóvírus):** Titkosítja az adatokat és váltságdíjat kér.
*   **Rootkit:** Rendszerszinten rejti el magát és a tevékenységét.

### Adatmentés (Backup)
*   **Full (Teljes):** Mindent ment. Lassú, sok hely, de gyors visszaállítás.
*   **Differential (Differenciális):** Az utolsó *Teljes* mentés óta változott adatokat menti.
*   **Incremental (Inkrementális):** Az utolsó *Bármilyen* mentés óta változott adatokat menti. Gyors mentés, kevés hely, de lassú visszaállítás (kell az összes láncszem).

### Jogi Háttér (GDPR)
*   **Személyes adat:** Bármi, ami alapján egy természetes személy azonosítható (Név, IP cím, Email).
*   **Adatkezelő:** Aki meghatározza az adatkezelés célját (pl. a cég).
*   **Adatfeldolgozó:** Aki az adatkezelő megbízásából technikai műveletet végez (pl. tárhelyszolgáltató).
*   **Jogok:** Tájékoztatás, Hozzáférés, Törlés ("elfeledtetéshez való jog"), Hordozhatóság.
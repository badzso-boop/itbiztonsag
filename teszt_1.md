# 1. Hét: Ellenőrző Teszt

Ez a teszt az első heti "Informatikai Biztonság Alapjai" tananyagot öleli fel. Próbálj meg válaszolni a kérdésekre az `osszefoglalo_1.md` és a tananyagok alapján! A helyes megoldásokat a lap alján találod.

---

**1. Kérdés (Elmélet)**

Egy kórházi szerveren tárolt betegadatokhoz egy illetéktelen személy hozzáfér és letölti azokat. Az információbiztonság CIA modelljének melyik alapelve sérült *elsődlegesen*?

- a) Rendelkezésre állás (Availability)
- b) Sértetlenség (Integrity)
- c) Bizalmasság (Confidentiality)
- d) Hitelesség (Authenticity)

Megoldas: C

---

**2. Kérdés (Elmélet)**

Mi a fő különbség a **fenyegetés (threat)** és a **kockázat (risk)** között?
(Rövid, 1-2 mondatos válasz)

Megoldas: Amikor a rendszerunkbe mar betortek es csinalnak valamit az a fenyegetes es a kockazat az az amikor ugy epitjuk fel a rendszert hogy nem epitunk vedelmet hozza igy kitesszuk kockazatnak

---

**3. Kérdés (Szituáció)**

Egy alkalmazott kap egy e-mailt a "bankjától", amelyben egy linkre kattintva meg kell erősítenie a jelszavát. Az oldal, amire a link visz, megszólalásig hasonlít a bank valódi weboldalára. Milyen típusú támadás történik?

- a) Man-in-the-Middle (MITM)
- b) Social Engineering (Phishing altípus)
- c) DoS támadás
- d) Malware telepítés

Megoldas: B

---

**4. Kérdés (Elmélet)**

Melyik "kalapos" hacker kategóriába tartozik az a személy, aki egy cég megbízásából, szerződés keretein belül próbálja meg feltörni a cég rendszereit, hogy javíthassák a biztonságot?

- a) Grey Hat
- b) Black Hat
- c) Script Kiddie
- d) White Hat

Megoldas: D

---

**5. Kérdés (Szituáció)**

Egy cég rendszere lelassul és elérhetetlenné válik, mert egy támadó mások által fertőzött számítógépek (botnet) segítségével hatalmas mennyiségű, haszontalan kérést küld a szerver felé. Melyik információbiztonsági alapelv sérül, és mi a támadás neve?
(Rövid, 1-2 mondatos válasz)

Megoldas: A rendelkezesre allas serul, hiszen a lassulas miatt a tobbi felhasznalonak nem lesz elerheto a szerver. A tamadas neve: ddos

---

**6. Kérdés (Elmélet)**

Párosítsd össze a hozzáférés-szabályozás fogalmait (AAA) a megfelelő leírással!

| Fogalom | Leírás |
|---|---|
| 1. Authentication | A) Mit tehet meg a felhasználó a rendszerben? |
| 2. Authorization | B) Ki vagy te valójában? |
| 3. Accounting | C) Mit csináltál a rendszerben? |

Megoldas: 1 - B; 2 - A ; 3 - C 

---

**7. Kérdés (Szituáció)**

Egy támadó bejut a cég irodájába egy pizzafutárnak álcázva magát, és egy USB eszközt csatlakoztat egy őrizetlenül hagyott számítógéphez. Milyen típusú fenyegetésről van szó?

- a) Technológiai sebezhetőség
- b) Fizikai biztonsági és Social Engineering incidens
- c) Konfigurációs biztonsági rés
- d) Házirendi biztonsági rés

Megoldas: B

---

**8. Kérdés (Elmélet)**

Mi a **mélységi védelem (Defense-in-Depth)** alapelve?

- a) Egyetlen, nagyon erős védelmi vonal kiépítése.
- b) Kizárólag a legbelső, legértékesebb adatok védelme.
- c) Több, egymásra épülő, különböző típusú védelmi réteg alkalmazása.
- d) A támadások utólagos detektálására és a helyreállításra fókuszálás.

Megoldas: C

---

**9. Kérdés (Elmélet)**

Mi a különbség egy **vírus** és egy **féreg (worm)** között a terjedésüket tekintve?
(Rövid, 1-2 mondatos válasz)

Megoldas: A virus ugy terjed ha valaki letolt egy fajlt ami virusos a worm pedig ha egy dolgot megfertozott akkor automatikusan a halozaton keresztul sokszorositja onmagat

---

**10. Kérdés (Szituáció)**

Egy felhasználó a vállalati laptopján letiltja a kötelező képernyőzárat, mert kényelmetlennek tartja a folyamatos jelszóbeírást. Milyen típusú sebezhetőséget/rést okoz ezzel?

- a) Technológiai sebezhetőség
- b) Konfigurációs és házirendi biztonsági rés
- c) Fizikai sebezhetőség
- d) Adatvesztési vektor

Megoldas: C

<br><br>
---
<br><br>

## Megoldások

1.  **c) Bizalmasság (Confidentiality)**. Az adatok illetéktelen kezekbe kerültek.
2.  A **fenyegetés** egy potenciális veszélyforrás (pl. egy hacker), míg a **kockázat** annak a valószínűsége, hogy ez a fenyegetés egy sérülékenységet kihasználva kárt okoz.
3.  **b) Social Engineering (Phishing altípus)**. A támadás a felhasználó megtévesztésére épül.
4.  **d) White Hat**. Ő az etikus hacker, aki engedéllyel dolgozik.
5.  A **rendelkezésre állás** elve sérül. A támadás neve **DDoS (Distributed Denial of Service)**, mivel több forrásból (botnet) érkezik.
6.  `1-B`, `2-A`, `3-C`. (Authentication - Ki vagy?, Authorization - Mit tehetsz?, Accounting - Mit tettél?)
7.  **b) Fizikai biztonsági és Social Engineering incidens**. A támadó fizikai hozzáférést szerzett (bejutott) megtévesztéssel (pizzafutár).
8.  **c) Több, egymásra épülő, különböző típusú védelmi réteg alkalmazása.**
9.  A **vírusnak** szüksége van valamilyen emberi interakcióra vagy egy gazdaprogramra a terjedéshez (pl. fájl megnyitása), míg a **féreg (worm)** önállóan, hálózati sérülékenységeket kihasználva terjed emberi beavatkozás nélkül.
10. **b) Konfigurációs és házirendi biztonsági rés**. A felhasználó egy biztonsági beállítást (konfigurációt) változtatott meg, és ezzel megsértette a vállalati szabályzatot (házirendet).

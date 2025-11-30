# 8. Hét: Ellenőrző Teszt - Hitelesítés és Csoportházirend

Ez a teszt a 8. heti "Hitelesítés és Csoportházirend" tananyagra épül. Válaszaidat az összefoglaló és a tananyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (Hitelesítési Módok)**

A **Kerberos protokoll** elsősorban melyik hitelesítési módszert (amit tudsz, amit birtokolsz, ami vagy) használja az identitás igazolására, és miért?

---

**2. Kérdés (Jelszótárolás)**

Mi a célja a "sózásnak" (salt) és a "kulcsszármaztatási függvényeknek" (key stretching/KDF) a jelszavak biztonságos hash-elt tárolásakor?

---

**3. Kérdés (MFA Előnyei)**

Mi a **Többfaktoros Hitelesítés (MFA)** lényege, és miért tekinthető jelentősen biztonságosabbnak, mint az egyfaktoros hitelesítés?

---

**4. Kérdés (RADIUS vs. TACACS+)**

Melyik protokoll (RADIUS vagy TACACS+) nyújt részletesebb engedélyezési (authorization) lehetőségeket, és melyik az, amelyik jellemzően a hálózati eszközök (pl. routerek, switchek) adminisztrációs hozzáférését védi?

---

**5. Kérdés (Csoportházirend Célja)**

Mi a **Csoportházirend (Group Policy)** fő célja egy Windows tartományi környezetben (Active Directory)?

---

**6. Kérdés (Csoportházirend - Jelszóházirend)**

A fejlesztő cég menedzsmentjének fokozott biztonságra van szüksége. Nevezz meg legalább három olyan specifikus jelszóházirend beállítást, amelyet Csoportházirenddel érvényesítenél a "Menedzsment" csoport felhasználói számára!

---

**7. Kérdés (Csoportházirend - Tesztelők Környezete)**

A "Tesztelők" csoport tagjainak célja, hogy kizárólag a tesztelésre koncentráljanak. Javasolj két olyan Csoportházirend beállítást a "Felületi megjelenítés" kategóriából, amellyel korlátoznád/egyszerűsítenéd az asztali környezetüket!

---

**8. Kérdés (Csoportházirend - Fájlmegosztás Csatolása)**

Magyarázd el, hogyan lehet Csoportházirenddel automatikusan hálózati meghajtókat csatolni a tartományba bejelentkező felhasználók számára, és mi ennek az előnye!

---

**9. Kérdés (Kerberos Működés)**

Röviden írd le a **Kerberos hitelesítési folyamat** első két fő lépését egy felhasználó szemszögéből, aki egy hálózati szolgáltatáshoz szeretne hozzáférni! (Fókuszálj az AS és a TGS szerepére, valamint a jegyekre.)

---

**10. Kérdés (Hitelesítési Gyengeség - SSO)**

A Single Sign-On (SSO) rendszerek nagy kényelmet biztosítanak. Milyen jelentős biztonsági kockázatot hordozhat egy SSO rendszer, ha nem megfelelően van implementálva vagy tervezve? (1-2 mondat)

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
A **Kerberos protokoll** elsősorban az **"amit tudsz" (knowledge-based)** hitelesítési módszert használja (a felhasználó titkos kulcsa, ami a jelszavából származik), kombinálva egy **"amit birtokolsz" (possession-based)** mechanizmussal (a különböző jegyek, tokenek), melyek igazolják a jogosultságot anélkül, hogy a jelszó utazna a hálózaton. A jegyek birtoklása alapvető a működéséhez.

**2. Kérdés:**
-   **Só (Salt)**: Egy véletlen, egyedi karakterlánc, amelyet minden egyes jelszóhoz hozzáadnak, mielőtt hash-elik. Célja, hogy az azonos jelszavakhoz is különböző hash értékek tartozjanak, megakadályozva a szivárványtábla-támadásokat és a jelszavak közötti összehasonlítást.
-   **Kulcsszármaztatási függvények (Key Stretching / KDF)**: Olyan eljárások, amelyek szándékosan lassítják a jelszó hash-elését (pl. sok iterációval). Céljuk, hogy a brute-force támadásokat sokkal időigényesebbé tegyék, mivel minden egyes próbálkozás (jelszó hash-elése) több időt vesz igénybe.

**3. Kérdés:**
A **Többfaktoros Hitelesítés (MFA)** lényege, hogy a felhasználónak legalább két különböző típusú (kategóriájú) hitelesítési módszert kell igazolnia (pl. egy jelszót és egy OTP kódot). Jelentősen biztonságosabb, mert ha az egyik faktor (pl. a jelszó) kompromittálódik, a támadó még mindig nem tud bejutni a rendszerbe a másik faktor (pl. a token) hiányában.

**4. Kérdés:**
-   **RADIUS**: Jellemzően a **hálózati hozzáférés-szabályozáshoz** (pl. VPN, Wi-Fi hozzáférés) használják. Az engedélyezési lehetőségei kevésbé részletesek, inkább szolgáltatásalapúak.
-   **TACACS+**: Részletesebb engedélyezési (authorization) lehetőségeket nyújt (parancsszintű jogosultságok), ezért jellemzően a **hálózati eszközök (routerek, switchek) adminisztrációs hozzáférésének** védelmére használják.

**5. Kérdés:**
A **Csoportházirend (Group Policy)** fő célja egy Windows tartományi környezetben, hogy központilag kezelje és érvényesítse a biztonsági, működési és konfigurációs beállításokat a felhasználókra és számítógépekre. Segítségével a rendszeradminisztrátorok egységesen és hatékonyan alkalmazhatnak szabályokat a hálózatban.

**6. Kérdés:**
1.  **Minimális jelszóhossz**: Pl. legalább 12-14 karakter.
2.  **Jelszó komplexitási követelmények**: Pl. kis- és nagybetű, szám, speciális karakter kombinációja.
3.  **Jelszó élettartama**: Pl. a jelszó 30 naponta lejár, kötelező jelszócserével.
4.  **Jelszóelőzmények kényszerítése**: Pl. a felhasználó nem használhatja újra az utolsó 5-10 jelszavát.

**7. Kérdés:**
1.  **Start menü és tálca tiltása/korlátozása**: Elrejti a nem szükséges menüpontokat, keresési funkciókat, tiszta felületet biztosítva.
2.  **Asztal megjelenítésének korlátozása**: Letiltja az asztali ikonok, vagy a háttérkép változtatását, esetleg teljesen "lecsupaszítja" az asztalt, hogy csak a tesztprogram ikonja legyen látható.
3.  **Parancssor tiltása**: Megakadályozza a parancssor megnyitását, ezzel is korlátozva a rendszer manipulálásának lehetőségét.

**8. Kérdés:**
A Csoportházirenddel (Group Policy) lehetőség van a **Felhasználó konfigurációja -> Beállítások -> Windows beállítások -> Meghajtók leképezése** (User Configuration -> Preferences -> Windows Settings -> Drive Maps) opcióval automatikusan csatolni hálózati meghajtókat. Ennek előnye, hogy a felhasználóknak nem kell manuálisan megkeresniük és csatolniuk a megosztásokat, ami növeli a kényelmet és csökkenti a felhasználói hibák lehetőségét.

**9. Kérdés:**
A **Kerberos hitelesítési folyamat** első két lépése (felhasználói szempontból):
1.  **Hitelesítés az AS-nél (Authentication Server)**: A felhasználó beírja a felhasználónevét és jelszavát, a kliens elküldi a felhasználónév-hash-t az AS-nek. Az AS ellenőrzi a felhasználót, és ha sikeres, visszaküld egy **Ticket-Granting Ticket (TGT)**-t a kliensnek, a felhasználó kulcsával titkosítva.
2.  **Jegy kérése a TGS-től (Ticket-Granting Server)**: A kliens elküldi a TGT-t a TGS-nek, és kéri, hogy jegyet kapjon a kívánt hálózati szolgáltatáshoz. A TGS, miután dekódolta a TGT-t, kiadja a **szolgáltatási jegyet (Service Ticket)**, amit a szolgáltatás kulcsával titkosít.

**10. Kérdés:**
Egy **SSO (Single Sign-On)** rendszer, ha nem megfelelően van implementálva, azt a jelentős biztonsági kockázatot hordozza, hogy a támadó egyetlen sikeres hitelesítéssel hozzáférést szerezhet az összes, az SSO rendszerbe integrált szolgáltatáshoz. Ez egy "egyetlen ponton történő kompromittálás" (single point of compromise), ahol az egyetlen belépési pont feltörése az egész rendszerhez való hozzáférést biztosítja, ha a mögöttes biztonsági rétegek nem megfelelőek.
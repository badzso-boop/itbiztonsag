# 8. Hét: Hitelesítés és Csoportházirend - Összefoglaló

Ez a dokumentum a 8. heti tananyagot foglalja össze, amely a hitelesítés (authentication) különböző aspektusait, módszereit és protokolljait, valamint a Csoportházirendek (Group Policy) alkalmazását tárgyalja a Windows tartományokban.

## I. Hitelesítés (Authentication)

A hitelesítés az a folyamat, amely során egy felhasználó vagy rendszer igazolja a személyazonosságát, mielőtt hozzáférést kapna egy rendszerhez vagy erőforráshoz.

### 1. Hitelesítési módszerek

Három alapvető kategória létezik:
-   **Amit tudsz (Knowledge-based)**: Jelszavak, PIN kódok.
    -   *Előnyök*: Olcsó, könnyen implementálható.
    -   *Hátrányok*: Elfelejthető, lehallgatható (shoulder surfing), kitalálható (brute force, dictionary attack), adatszivárgás esetén kompromittálódik.
-   **Amit birtokolsz (Possession-based)**: Okoskártyák, biztonsági tokenek, OTP (One-Time Password) eszközök.
    -   *Előnyök*: Nehezebben hamisítható, lopás esetén érzékelhető (letiltható).
    -   *Hátrányok*: Elveszíthető, ellopható, drágább.
-   **Ami vagy (Biometrics-based)**: Ujjlenyomat, íriszszkennelés, arcfelismerés, hangfelismerés.
    -   *Előnyök*: Kényelmes, nehezen hamisítható (élő egyed ellenőrzés), egyedi.
    -   *Hátrányok*: Drága, adatvédelmi aggályok (azonosítás után nem változtatható meg), hamis pozitív/negatív arány, jogi problémák.

### 2. Jelszóalapú hitelesítés

-   **Jelszavak biztonságos tárolása**:
    -   **Plain-text**: Kerülendő, mindenki számára olvasható, kompromittálás esetén azonnal hozzáférhetők.
    -   **Titkosított**: Képes a visszafejtésre, kulcskezelés problémája.
    -   **Hash-elt**: Egyirányú eljárás, a jelszót nem tároljuk, csak a hash értékét.
        -   **Só (Salt)**: Véletlen karakterlánc a jelszóhoz, hash-elés előtt. Megakadályozza a szótár- és szivárványtábla-támadásokat.
        -   **Pepper**: A sóhoz hasonló, de minden felhasználó számára azonos, és a hash tárolási helyétől elkülönítve tárolják.
        -   **Key Stretching/Key Derivation Functions (KDF)**: Lassítja a hash-elés folyamatát, megnehezítve a Brute Force támadásokat (pl. PBKDF2, bcrypt, scrypt).
-   **LM Hash és NTLM Hash**: Régebbi Windows rendszerekben használt jelszó-hash formátumok. Az LM hash rendkívül gyenge, könnyen törhető, mert 7 karakteres blokkokra osztja a jelszót és DES-sel titkosítja.

### 3. Többfaktoros hitelesítés (MFA)

Legalább két különböző típusú hitelesítési módszer egyidejű alkalmazása (pl. jelszó és token). Jelentősen növeli a biztonságot.

### 4. Hitelesítési protokollok

-   **PAP (Password Authentication Protocol)**: Jelszót plain-textben küldi, nem biztonságos.
-   **CHAP (Challenge-Handshake Authentication Protocol)**: Kihívás-válasz alapú, a jelszó soha nem utazik a hálózaton.
-   **Kerberos**: Hálózati hitelesítési protokoll, szimmetrikus kulcsú titkosításon alapul. Használ Ticket Granting Ticketet (TGT) és Service Ticketet a felhasználók és szolgáltatások közötti biztonságos kommunikációhoz egy nem megbízható hálózaton.
-   **RADIUS (Remote Authentication Dial-In User Service)**: Központosított AAA szolgáltatás (Authentication, Authorization, Accounting) hálózati hozzáféréshez.
-   **TACACS+ (Terminal Access Controller Access Control System Plus)**: Hasonló a RADIUS-hoz, de a Cisco fejlesztette.

### 5. Single Sign-On (SSO) és Federated Identity Management

-   **SSO**: Egyetlen bejelentkezéssel több alkalmazáshoz vagy szolgáltatáshoz férhet hozzá a felhasználó, anélkül, hogy újra be kellene jelentkeznie.
-   **Federated Identity Management**: Lehetővé teszi, hogy egy felhasználói identitást több szervezet vagy szolgáltató között is felhasználhassunk.

## II. Csoportházirend (Group Policy)

A Csoportházirend a Windows tartományokban (Active Directory) használt eszköz a biztonsági, működési és konfigurációs beállítások központi kezelésére és érvényesítésére a felhasználókra és számítógépekre.

### 1. Alkalmazási területei

-   **Biztonsági beállítások**:
    -   **Jelszóházirend**: Jelszavak komplexitására, hosszára, élettartamára vonatkozó szabályok (pl. min. 8 karakter, kis- és nagybetű, szám, speciális karakter).
    -   **Fiókzárolási házirend**: Hány sikertelen bejelentkezési kísérlet után záródjon le egy fiók, és mennyi időre.
    -   **Naplóházirend**: Milyen eseményeket (bejelentkezés, fájlhozzáférés, jogosultságmódosítás) naplózzon a rendszer.
    -   **Helyi biztonsági házirend**: Interaktív bejelentkezési beállítások, leállítási szabályok.
-   **Kényelmi funkciók**:
    -   **Fájlmegosztás automatikus csatolása**: Felhasználóknak automatikusan csatolódnak a hálózati meghajtók bejelentkezéskor.
-   **Felületi megjelenítés**:
    -   **Belépési üzenet**: Üdvözlő üzenet vagy jogi nyilatkozat bejelentkezéskor.
    -   **Asztal, Start menü, Tálca testreszabása vagy korlátozása**: A felhasználói felület egyszerűsítése vagy korlátozása (pl. parancssor tiltása, CTRL+ALT+DEL menüpontok tiltása).
-   **Egyéb beállítások**: Energiagazdálkodás, Windows Update beállítások, automatikusan futtatandó parancsok/scriptek, alapértelmezett nyomtató.

### 2. Csoportházirend alkalmazása (a fejlesztő cég példáján)

A gyakorlati feladat a fejlesztő cég szcenáriójában alkalmazza a csoportházirendeket a különböző munkakörök (Menedzsment, Fejlesztők, Tesztelők, HR-esek, Pénzügyesek) specifikus igényeinek megfelelően.

-   **Biztonsági beállítások**: A menedzsment számára erősebb jelszóházirend (pl. hosszabb jelszó, gyakoribb csere) és fiókzárolási szabályok.
-   **Kényelmi funkciók**: A tesztelők számára a tesztelendő program ikonja az asztalon, illetve az ahhoz való könnyített hozzáférés biztosítása.
-   **Felületi megjelenítés**: A teljes asztali felület lecsupaszítása a tesztgépeken (Start menü, keresés, ikonok letiltása), parancssor és CTRL+ALT+DEL menüpontok tiltása, hogy a tesztelők csak a tesztelésre fókuszáljanak.

A Csoportházirend lehetővé teszi, hogy ezeket a beállításokat központilag, egységesen és hatékonyan alkalmazzuk a tartományi környezetben lévő felhasználókra és számítógépekre.

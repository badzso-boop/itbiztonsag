# 9. Hét: Ellenőrző Teszt - PKI és Felhőbiztonság / Social Engineering

Ez a teszt a 9. heti "PKI és Felhőbiztonság / Social Engineering" tananyagra épül. Válaszaidat az összefoglaló és a tananyagok alapján fogalmazd meg. A megoldásokat a lap alján találod.

---

**1. Kérdés (PKI Célja)**

Mi a **Nyilvános Kulcsú Infrastruktúra (PKI)** elsődleges célja és milyen alapvető biztonsági elveket (CIA triád) segít megvalósítani?

---

**2. Kérdés (CA Szerepe)**

Mi a **Tanúsító Hatóság (CA - Certificate Authority)** szerepe és felelőssége egy PKI rendszerben?

---

**3. Kérdés (Digitális Tanúsítvány Összetevői)**

Sorolj fel legalább három olyan információt, amelyet egy digitális tanúsítvány tipikusan tartalmaz!

---

**4. Kérdés (Tanúsítvány Visszavonás)**

Miért szükséges a tanúsítványok visszavonása, és milyen két fő módszerrel lehet ellenőrizni, hogy egy tanúsítvány érvényes-e vagy visszavonásra került-e?

---

**5. Kérdés (Social Engineering Definíció)**

Definiáld a **Social Engineering** fogalmát, és magyarázd el, miért tekintik az "emberi tényezőt" a biztonság leggyengébb láncszemének ebben a kontextusban!

---

**6. Kérdés (Social Engineering Példák)**

Nevezz meg két különböző **Social Engineering** támadási formát (pl. Phishing, Tailgating), és röviden írd le, hogyan működik mindegyik!

---

**7. Kérdés (Védekezés Social Engineering Ellen)**

Sorolj fel legalább három hatékony védekezési stratégiát, amellyel csökkenthető a Social Engineering támadások sikeressége!

---

**8. Kérdés (Bizalmi Kapcsolatok a PKI-ban)**

Magyarázd el röviden az "egyirányú" és a "kétirányú" bizalmi kapcsolatok fogalmát egy PKI környezetben!

---

**9. Kérdés (Felhőbiztonság és SE)**

Hogyan célozhatják meg specifikusan a **felhőalapú szolgáltatások** felhasználóit a Social Engineering támadások? Adj egy konkrét példát!

---

**10. Kérdés (Social Engineering Malware Nélkül)**

Magyarázd el, hogyan lehet sikeres egy **Social Engineering** támadás **malware használata nélkül**. Adj egy konkrét példát a tananyagból!

<br><br>
---
<br><br>

## Megoldások

**1. Kérdés:**
A **Nyilvános Kulcsú Infrastruktúra (PKI)** elsődleges célja, hogy biztonságos és hiteles keretrendszert biztosítson az aszimmetrikus kulcsú kriptográfia (nyilvános/titkos kulcspárok) használatához elosztott rendszerekben. Segít megvalósítani az alapvető biztonsági elveket: **hitelesítés (authentication)**, **bizalmasság (confidentiality)**, **sértetlenség (integrity)**, és **letagadhatatlanság (non-repudiation)**.

**2. Kérdés:**
A **Tanúsító Hatóság (CA - Certificate Authority)** a PKI központi és legfontosabb eleme. Fő feladatai a következők:
1.  **Azonosság igazolása**: Megállapítja és ellenőrzi a tanúsítványt igénylő fél (személy, szervezet, szerver) identitását.
2.  **Tanúsítványok kibocsátása**: Digitális tanúsítványokat bocsát ki, amelyek a nyilvános kulcsot az igazolt identitáshoz kötik.
3.  **Tanúsítványok visszavonása**: Kezeli a visszavonási listákat (CRL), és visszavonja az érvénytelenné vált tanúsítványokat.

**3. Kérdés:**
Egy digitális tanúsítvány tipikusan a következő információkat tartalmazza:
1.  **A tulajdonos nyilvános kulcsa**: Az a kulcs, amivel mások titkosíthatnak neki üzeneteket, vagy ellenőrizhetik az aláírását.
2.  **A tulajdonost azonosító adatok**: Név, e-mail cím, szervezet, stb.
3.  **Érvényesség ideje**: A tanúsítvány kibocsátásának és lejáratának dátuma.
4.  **A kibocsátó (CA) azonosító adatai**: Annak a CA-nak az adatai, amelyik a tanúsítványt kiállította.
5.  **A kibocsátó (CA) digitális aláírása**: A CA titkos kulcsával készült aláírás, amely igazolja a tanúsítvány hitelességét és sértetlenségét.

**4. Kérdés:**
A tanúsítványok visszavonása azért szükséges, mert egy kibocsátott tanúsítvány elveszítheti a hitelességét (pl. a hozzá tartozó titkos kulcs kompromittálódik, a tulajdonos elveszíti a pozícióját). Ennek kezelésére két fő módszer létezik:
1.  **CRL (Certificate Revocation List)**: A CA rendszeresen közzéteszi a visszavont tanúsítványok listáját. A felhasználóknak (alkalmazásoknak) le kell tölteniük és ellenőrizniük kell ezt a listát.
2.  **OCSP (Online Certificate Status Protocol)**: Egy online protokoll, amely valós időben lekérdezhető egy CA-tól, hogy egy adott tanúsítvány érvényes-e vagy visszavonásra került-e.

**5. Kérdés:**
A **Social Engineering** az emberek pszichológiai manipulációjára épülő támadás, amelynek célja, hogy bizalmas információkat szerezzenek, vagy rávegyék az áldozatokat olyan cselekedetekre, amelyek sértik a biztonsági protokollokat. Az "emberi tényezőt" a biztonság leggyengébb láncszemének tekintik, mert a technológiai védelmek (tűzfalak, titkosítás) mellett az embereket könnyebb megtéveszteni, befolyásolni, és így kihasználni a segítőkészségüket, hiszékenységüket vagy figyelmetlenségüket.

**6. Kérdés:**
1.  **Phishing**: A támadó egy e-mailt küld, amely például egy banki vagy szolgáltatói értesítésnek álcázza magát. Ráveszi az áldozatot, hogy egy hamisított weboldalon adja meg belépési adatait vagy bankkártya-információit.
2.  **Tailgating**: A támadó egy felhatalmazott személyt követve, kihasználva a segítőkészséget vagy a figyelmetlenséget, jut be egy biztonságos, beléptető rendszerrel védett területre (pl. cipelve dobozokat, és megkérve valakit, hogy tartsa nyitva az ajtót).

**7. Kérdés:**
1.  **Felhasználói oktatás és tudatosság növelése**: A felhasználókat rendszeresen tájékoztatni kell a Social Engineering különböző formáiról, a gyanús jelekről és a helyes eljárásmódokról.
2.  **Minden e-mailt és üzenetet kritikus szemmel kell kezelni**: Különösen a sürgető, túl jól hangzó vagy ismeretlen feladótól érkező üzeneteket, és soha nem szabad azonnal reagálni, vagy kattintani linkekre.
3.  **Szigorú hitelesítési protokollok**: Soha ne adjunk meg hitelesítésre szolgáló adatokat telefonon, e-mailben, vagy gyanús weboldalon. A többfaktoros autentikáció (MFA) bevezetése is elengedhetetlen.

**8. Kérdés:**
-   **Egyirányú bizalmi kapcsolat**: Egy olyan PKI környezetben lévő kapcsolat, ahol az egyik tartomány (A) felhasználói megbízhatnak a másik tartomány (B) erőforrásaiban és hitelesítésében, de a B tartomány felhasználói nem bízhatnak az A tartomány erőforrásaiban.
-   **Kétirányú bizalmi kapcsolat**: Mindkét tartomány (A és B) kölcsönösen megbízik a másikban. Ez azt jelenti, hogy az A tartomány felhasználói hozzáférhetnek a B tartomány erőforrásaihoz, és fordítva.

**9. Kérdés:**
A Social Engineering támadások specifikusan célozhatják a felhőalapú szolgáltatások felhasználóit azáltal, hogy kihasználják a felhőkörnyezetben megszokott működési sajátosságokat. Például egy támadó **hamis felhőszolgáltatói értesítést** küldhet, amely arról szól, hogy a felhasználó felhőbeli tárhelye megtelt, vagy biztonsági rést észleltek, és a felhasználót ráveszik, hogy egy hamis bejelentkezési oldalon adja meg felhőszolgáltatói azonosító adatait. Ezzel a támadó hozzáférést szerezhet a felhőben tárolt adatokhoz.

**10. Kérdés:**
Egy **Social Engineering** támadás lehet sikeres **malware használata nélkül** azáltal, hogy a támadó pusztán pszichológiai manipulációval, megtévesztéssel szerzi meg a kívánt információkat vagy éri el a célját.
**Konkrét példa a tananyagból:** A "Pig Butchering" (disznóvágás) csalás, ahol a támadó hosszú távú bizalmi kapcsolatot épít ki az áldozattal, majd ráveszi, hogy pénzt fektessen be egy hamis kereskedési platformon, anélkül, hogy bármilyen kártékony programot telepítene az áldozat gépére. A támadás az emberi kapzsiságra és a bizalomra épül. Ugyanígy a "Tailgating" is malware nélkül valósul meg, egyszerűen a segítőkészség kihasználásával.
# 1. Hét: Az Informatikai Biztonság Alapjai - Összefoglaló

Ez a dokumentum az első heti "Bevezetés az informatikai biztonságba" témakör legfontosabb fogalmait és alapelveit tartalmazza.

## Alapfogalmak

- **Információbiztonság**: Az informatikai rendszer olyan állapota, amelyben a kezelt adatok **bizalmassága**, **sértetlensége** és **rendelkezésre állása** (CIA) biztosított, arányosan a kockázatokkal.
- **Vagyon (Asset)**: Bármi, ami értékkel bír a szervezet számára (pl. adatok, eszközök, emberek, hírnév).
- **Sérülékenység (Vulnerability)**: A rendszer vagy a tervezés olyan gyengesége, amelyen keresztül egy fenyegetés megvalósulhat.
- **Fenyegetés (Threat)**: Potenciális veszélyforrás, amely kárt okozhat a szervezet vagyonában.
- **Kockázat (Risk)**: Annak a valószínűsége, hogy egy adott fenyegetés kihasznál egy sérülékenységet, és ezzel kárt okoz.
- **Támadás**: Védett érték megszerzésére, megsemmisítésére vagy károkozásra irányuló cselekmény.
- **Exploit**: Olyan kód vagy eljárás, amely egy konkrét sérülékenységet használ ki.
- **Mérséklés (Mitigation)**: Ellenintézkedés a kockázat vagy a fenyegetés súlyosságának csökkentésére.

## Az Információbiztonság 3 Alapelve (CIA Triád)

1.  **Bizalmasság (Confidentiality)**: Az adatokhoz csak az arra jogosultak férhetnek hozzá. (Példa sértésre: Adatszivárgás, jelszólopás).
2.  **Sértetlenség (Integrity)**: Az adatok és a rendszer elemei pontosak, teljesek és nem módosultak jogosulatlanul. (Példa sértésre: Adatok manipulálása, vírus, ami fájlokat ír felül).
3.  **Rendelkezésre állás (Availability)**: A rendszer és az adatok a jogosult felhasználók számára elérhetőek, amikor szükséges. (Példa sértésre: DoS/DDoS támadás, hardverhiba).

## Hozzáférés-szabályozás Alapjai (AAA)

- **Authentication (Azonosítás/Hitelesítés)**: Annak bizonyítása, hogy a felhasználó az, akinek mondja magát. (Ki vagy te?)
- **Authorization (Jogosultságkezelés)**: Annak meghatározása, hogy egy hitelesített felhasználó mit tehet meg a rendszerben. (Mit tehetsz meg?)
- **Accounting (Naplózás/Elszámoltathatóság)**: A felhasználói tevékenységek rögzítése a későbbi elemzés céljából. (Mit tettél?)

## Támadók és Támadások

### Támadók Kategóriái (Kalapok)
- **White Hat (Etikus Hacker)**: Engedéllyel, a biztonság javítása érdekében keres sérülékenységeket.
- **Black Hat (Cracker)**: Rosszindulatú, károkozás vagy haszonszerzés céljából támad.
- **Grey Hat**: Engedély nélkül keres sebezhetőséget, de utána jellemzően értesíti a tulajdonost (néha díjazásért cserébe).
- **Script Kiddie**: Alacsony szaktudású támadó, aki mások által készített, kész eszközöket használ.

### Gyakori Támadástípusok
- **Social Engineering (Megtévesztés)**: Pszichológiai manipulációval veszi rá az embereket bizalmas információk kiadására (pl. Phishing, Baiting).
- **Malware (Kártékony szoftver)**: Vírus, féreg (Worm), trójai (Trojan horse), zsarolóvírus (Ransomware), kémprogram (Spyware).
- **Denial of Service (DoS)**: A szolgáltatás megbénítására irányuló támadás, amely túlterheli a rendszert, elérhetetlenné téve azt a jogosult felhasználók számára.
- **Man-in-the-Middle (MITM)**: A támadó a kommunikáló felek közé ékelődve lehallgatja vagy manipulálja a forgalmat.
- **Spoofing (Hamisítás)**: Másnak adja ki magát (pl. IP-cím, e-mail feladó hamisítása).

## Védekezési Elvek
- **Mélységi védelem (Defense-in-Depth)**: Több, egymásra épülő védelmi réteg alkalmazása (pl. tűzfal, vírusirtó, IDS/IPS, titkosítás, fizikai védelem).
- **Minimális jogosultság elve (Least Privilege)**: Minden felhasználó csak a munkájához feltétlenül szükséges jogosultságokkal rendelkezzen.
- **PreDeCo elv**: A védelem három mechanizmusa: **Preventive** (megelőző), **Detective** (felderítő), **Corrective** (helyreállító) kontrollok.

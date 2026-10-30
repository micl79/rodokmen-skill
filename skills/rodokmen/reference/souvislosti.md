# Souvislosti a jiné zdroje – kde hledat, když matrika mlčí

Každý bod je postup, který model zvládne sám a který v jednom rodinném projektu už jednou pomohl nebo by pomohl. Ověřené zdroje doplňuj dole.

## A. Souvislosti z dat, která už máme (bez nového archivu)
1. **Síť kmotrů a svědků.** Ze všech `shrnuti` v `zaznamy.json` vypiš jména kmotrů, svědků a porodních bab a spočítej,
   kdo se opakuje u více rodin. Kmotři bývali příbuzní (strýc, teta, babička). Příklad: kostelník svědkem u dvou svateb v sousedních letech → příbuzný nebo sousedská vazba.
2. **Dům jako vlákno.** Číslo popisné se nemění, lidé ano. Vypiš pro každý dům (Dolní Lhota 33, Horní Ves 26…)
   všechny zápisy, které ho zmiňují, seřazené podle roku. Kdo v domě žil před naším předkem, je často tchán (přiženění –
   v jednom projektu 4×).
3. **Sourozenci jako zkratka.** Sňatek nebo úmrtí sourozence často uvádí to, co náš zápis vynechal (rodné příjmení
   matky, obec původu otce). Křest bratra dal oba páry prarodičů, které sňatek nemenoval.
4. **Věk jako filtr, ne jako fakt.** Věk ve sňatku byl u mladých nevěst „vylepšený“ (14½ → 17). Hledej rok narození
   v rozpětí −3 až +1 roku od uvedeného věku; u úmrtí ±5 let.
5. **Pojmenovací zvyk.** První syn často po dědovi z otcovy strany, první dcera po babičce. Seznam dětí → odhad jmen
   prarodičů → užší hledání v rejstříku.
6. **Rozpory jako stopa.** Dvě různá jména matky u sourozenců znamenají
   druhé manželství, nevlastní dítě nebo jinou osobu – vždy prověř, nespojuj potichu.
7. **Celá farnost najednou.** Kde je dobrovolnický rejstřík (Třeboň `rejstrik`) nebo farní index, vypiš všechny výskyty
   příjmení za 50 let a sestav rodiny automaticky; pak napoj na našeho předka. Rychlejší než listování po jednom zápisu.

## B. Jiné zdroje než matriky
| Zdroj | Co dá | Kdy |
|---|---|---|
| Dobový tisk – Kramerius (`tools/kramerius.py`), ANNO (`tools/anno.py`) | úmrtí, parte, spolky, živnosti, soudní zprávy, Baťovské časopisy | lidé po ~1850 |
| Adresáře a ročenky (Kramerius) | živnostníci, mlynáři, kováři, starostové obcí | 1880–1940 |
| Berní rula 1654, Soupis poddaných 1651 | jména hospodářů na gruntech | konec matrik kolem 1650 |
| Tereziánský / josefský / stabilní katastr, indikační skici | majitel podle čísla domu, výměra | 1750–1840 |
| Sčítání lidu 1857–1921 | celá domácnost s daty a místy narození | 1857+ |
| Pozemkové (gruntovní) knihy, urbáře | převody gruntů, výměnky, svatební smlouvy | 1700–1850 |
| Obecní a školní kroniky | události obce, požáry, epidemie, padlí | 1900+ |
| VHA – databáze padlých a legionářů, kmenové listy | vojáci 1. sv. války | narození 1860–1900 |
| Hřbitovy (BillionGraves, Hroby.cz, hřbitovy Brno) | data úmrtí, společné hroby | 1900+ |
| Cizí rodokmeny (FamilySearch, Geni, MyHeritage) | jen jako nápověda, nikdy jako doklad | vše |
| Paměť národa a podobné sbírky vzpomínek | život 20. století (Batanagar, 1951, srpen 1968) | 1900+ |
| Strojové čtení rukopisů (HTR, Transkribus) | plný text celé knihy → hledání jmen bez listování | až budou modely pro kurent |

## C. Pravidla
- Tisk, katastr i cizí stromy jsou **doplněk** – osoba se do `osoby.py` zapisuje jen na základě zápisu, ne podle zmínky
  v novinách nebo cizího stromu. U shody jmen odděl „jisté / pravděpodobné / jmenovec“.
- Ověřené zdroje s odkazem a příkladem připiš sem (oddíl D) a nástroje do `tools/`.

## D. Ověřené zdroje (doplňovat)
- Kramerius API v5 (`kramerius5.nkp.cz`) funguje i pro neveřejné dokumenty – vrací úryvek s hledaným slovem
  (příklad: hledání „Batanagar“ + příjmení → kniha Čechoslováci na březích Gangu 1946 a Sdělení zaměstnanců firmy Baťa 1939).
- Paměť národa (pametnaroda.cz) – vzpomínky pamětníků; život ve 20. století (emigrace, 1951, srpen 1968), často s fotografiemi.
- **VÚA – databáze padlých v 1. sv. válce** (vuapraha.cz/databaze-vha, bez přihlášení): záznam o padlém, místo a datum úmrtí, útvar.
- **eBadatelna SOA Praha – Archiválie** (`tools/ebadatelna.py a-info/a-snimek`): obecní kroniky Letky do 1924 (id 386),
  Žalov do 1960 (396), Libčice 1946–48 (387), Nelahozeves 1901–58 (414), farní 2301–2302, školní 2299–2300; sčítání 1921
  Nelahozeves (8298–8300).
- **MZA – sčítací operáty** (portál bez přihlášení, jen prohlížeč): Veselka 1869–1921, Boskovice od 1857. Pelhřimovsko
  patří pod MZA, vyzkoušené obce tam zatím nejsou (FamilySearch má víc – potřebuje účet).
- **MZA ARON – pozemkové knihy**: Veselka 1791–1878 a Horní Poříčí (panství Křetín).
- **Indikační skici stabilního katastru**: ags.cuzk.gov.cz/archiv (stará archivnimapy nefunguje); Sázava ~1830 = TAB421018290,
  jména majitelů u čísel domů čitelná. Morava: katalog skic MZA.
- **Adresáře Brna 1884–1919** (MZK, plný text) – Židenice do 1919 samostatná obec, v adresáři Brna nejsou.
- Neužitečné nebo za přihlášením: Soupis poddaných 1651 (pro vyzkoušené obce bez příjmení), Berní rula (NDK po přihlášení,
  Slánsko chybí), Baťovy noviny (KK Zlín, plný text jen ve studovně), Geni (místa skrytá), Transkribus (účet; vhodný na
  kroniky a pozemkové knihy). V archivu, ne online: soupis konzumentů soli 1698–1700 (Sázava, Hodějovice, Krasíkovice,
  Útěchovičky – AM Pelhřimov inv. 243/5), robotní protokol Sázavy 1836–37.
- **FamilySearch (uživatel přihlášen v Chromu; `mcp__claude-in-chrome__*`)**: index „Česká republika, Církevní knihy 1552-1981“ se hledá
  přes URL `familysearch.org/cs/search/record/results?q.givenName=…&q.surname=…&q.anyDate.from=…`. Zkouška na jedno příjmení: výsledky jsou bez obce
  („Česko“), filtr místa je neurčitý (stovky zásahů z celých Čech), hledaný sňatek tam nenalezen. Použití jen jako nápověda u
  vzácných příjmení; doklad vždy až ze snímku matriky. Jen čtení, nic nezakládat ani neupravovat.
- **`tools/fronta.py`** (30. 10. 2026): předci bez rodičů seřazení od nejlevnějšího kroku (jméno rodiče už v datech, po 1784,
  známý dům); uzavřené rody (číslo v `UZAVRENE`) vynechá. Výstup pracovni/fronta.md. Nebere v úvahu, co už bylo
  marně prohledáno – před zadáním pomocníkovi projdi research_log.md.
- **`tools/kmotri.py`** (30. 10. 2026): síť kmotrů a svědků z `shrnuti`. První výsledek: jeden rod z jedné vsi se opakoval u několika rodin v rozmezí sta let → hypotéza o rodném příjmení nevěsty, jejíž sňatek chyběl.
- **Nepoužitelné:** FamilySearch fulltext (AI přepisy) – české knihy v něm nejsou (30. 10. 2026).
- **Kontrola stromu:** osoba s číslem k, jejíž dítě k//2 v `P` není, na webu visí ve vzduchu. 30. 10. 2026 takto odpojeno
  6 předků (čísla 46x místo Kekulé). Po každém zápisu ověř: `[k for k in P if k>1 and k//2 not in P]`.
- **Databáze vodních mlýnů (vodnimlyny.cz, Rudolf Šimek)** – ověřeno 30. 10. 2026: karta mlýna → záložka „Historie“ dává
  Soupis poddaných podle víry 1651 (celá domácnost: věk, manželka, děti, čeleď), Berní rulu 1654, Soupis svobodníků 1655/1789 a řetěz
  držitelů mlýna do 20. století. **Čte se v Chromu** (`mcp__claude-in-chrome__*`; uživatel přihlášen): `navigate` na
  `…/mlyny/objekty/?q=<obec>` nebo rovnou na detail, `find` „Historie“ → `left_click` → `get_page_text`. Ve vestavěném prohlížeči web
  ukazuje ověření robota – **neobcházet**. Příklad: mlýn v Houserovce čp. 8 (detail/6287) – 1651 Jan Mlynář, svobodník, 30 let,
  × Anna, syn Matěj, dcery Mariana a Salomena; 1789 Josef Svoboda; 1829 František Svoboda; 1930 Josef Jaroš. Dá to předchůdce Josefa
  Svobody (258) o 120 let dál než matrika; propojení 1651 → 1770 zůstává hypotéza (rod Svobodů, svobodnický mlýn), doklad hledat v pozemkové knize.
  Mlýn bývá v rodě stovky let – hodí se pro mlynářské rody. Jen vodítko, osoby se zapisují z matriky.
- **Soupisy 1651 a 1654 přes mlýny a statky** – soupis podle víry (1651) je nejstarší seznam obyvatel s věkem; hledej ho na kartách
  mlýnů, v Archivu hlavního města Prahy a v digitalizacích Národního archivu u konkrétní vsi.

## E. 17. a 18. století – přes vrchnost (panství), ne přes farnost 
Matriky před ~1700 chybí nebo jsou slabé, ale **každá ves patřila k panství a panství vedlo vlastní knihy** – o poddaných,
jejich gruntech, dluzích, svatebních smlouvách a dědictví. Klíč: u každé větve zapiš **vrchnost** (panství, majitelský rod) a hledej její fondy.
Stav ověření: ✔ = u nás ověřeno v praxi, ? = kandidát, zatím neověřeno.

| Panství (vyzkoušené obce) | Kde jsou knihy | Stav |
|---|---|---|
| Libkova Voda–Vlásenice (Čelistná, Libkova Voda) | SOA Třeboň, pob. Jindřichův Hradec, fond 2592 – pozemkové knihy Os Pel 205, 207, 209 online (digi.ceskearchivy.cz/126623, 126624) | ✔ kontrakt 1808, smlouva 1848 |
| Červená Řečice (Střítež, Kameníček) | NA Praha, Archiv pražského arcibiskupství I., inv. č. 2609 (gruntovní kniha), 1754 (purkrechtní); fond Velkostatek Červená Řečice | ? jen mikrofilm/badatelna |
| Svojanov (Hutě) | SOA Zámrsk, Velkostatek Svojanov (inv. 2: 1579–1832; inv. 3: 1801–1870; smlouvy inv. 27–28) | ✔ existuje, v ARONu 0 snímků |
| Křetín / Horní Poříčí / Veselka | MZA Brno, Pozemkové knihy: Horní Poříčí 1770–1880 (kn. 14059), Veselka 1791–1878 (kn. 14090) | ✔ online v ARONu MZA, čte se v prohlížeči |
| Chlumec (Pořešice), Horní Cerekev, Nový Rychnov, Lobkovicové (Libčice) | ? hledat fondy Velkostatek …, urbáře, kontrakty | ? |
| Svobodníci (Houserovka) | NA Praha, Knihy svobodnické (KSv inv. 1–133; soupis 1789 inv. 154), jen mikrofilm; svobodnici.cz | ✔ web svobodnici.cz |

**Co v těchto knihách hledat** (a proč je to rychlejší než matrika): (1) **svatební smlouva** a **dědické řízení** vypíše všechny
sourozence s podíly a věkem (jedna obec 1808: pět dětí s věkem; 1848: sourozenci s podíly) – celá rodina z jednoho zápisu;
(2) **kontrakt** říká „od svého otce zakoupený“ – tj. otce a převod; (3) **rejstřík majitelů čp.** dá řetěz majitelů dozadu bez matrik;
(4) **urbář / soupis poddaných** (kolem 1650–1790) uvádí hospodáře po jménech u každé vsi; (5) **přísežní a rychtáři** (např. „juratus“ = přísežný, rychtář)
byli často příbuzní a svědčí opakovaně – patří do sítě kmotrů a svědků (`tools/kmotri.py`).

**Další kandidáti (neověřeno, ověřit při první příležitosti):**
- **Soupis poddaných podle víry 1651** – vydán po krajích ve 23 svazcích (edice Národního archivu; PDF některých svazků jsou na nacr.cz, např. Plzeňsko a Berounsko ✔ existují). Pro Pelhřimovsko a Příbramsko najdi svazek podle kraje (Bechyňský, Táborský, Prácheňský…). Dává hospodáře, manželku, děti, čeleď s věkem.
- **Berní rula 1654** (NA Praha; digitálně v NDK po přihlášení) – hospodáři po jménech, jen pro vesnice, které rula zachytila.
- **Tereziánský katastr 1748–1757** a **Josefský katastr 1785–1789** – držitelé usedlostí u čp. (u Čelistné je josefský katastr v SOA Třeboň, digi.ceskearchivy.cz/343404–343408 – ? nečteno).
- **Konskripce 1770 / 1798** („Seelenregister“, soupisy duší) – čísla domů a celé domácnosti; zachované jen sporadicky.
- **Šlechtické rody** – zajímají jen, pokud je předek v panských službách (hejtman, písař, hajný, myslivec, mlynář na panském mlýně): panský personál bývá v **účtech panství** a v **matrikách jako kmotři z úřadu**. Jinak slouží vrchnost jen k nalezení archivu, ne rodokmenu.
- **Vizitace a „Status animarum“** (seznamy farníků), **zádušní účty** a **knihy bratrstev** – jména donátorů a kmotrů, občas rodiny.
- **Obecní a farní kroniky, školní kroniky** (SOA Praha `a-info`) – ✔ už zařazeno výše.
- **Cizí genealogie jako nápověda** (FamilySearch strom, Geni): jen vodítko, nikdy doklad.

## F. Napoleonské války a vojenské prameny
Muži narození zhruba 1760–1800 mohli sloužit v c. k. armádě (odvody, války 1792–1815, Landwehr 1809). Vojenské záznamy říkají
**rodiště, věk, povolání otce a vzhled**, někdy i vojenské matriky (sňatek, úmrtí v poli), které v domácí matrice chybí.
Stav ověření: ✔ ověřeno vyhledáním pramene, ? zatím jen kandidát.
- ✔ **Kriegsarchiv Vídeň** (Österreichisches Staatsarchiv, Rodinný výzkum: statearchives.gv.at/family-research/kriegsarchiv.html). Nemá všechny osobní záznamy
  před 1918; od 1868 jsou jiné fondy decentralizované. **Grundbuchsblätter** (kmenové listy) pro Čechy, Moravu a rakouské Slezsko jsou online pro ročníky narození do 1864
  (FamilySearch katalog „Grundbuchblätter Diverse: Böhmen, Mähren, Schlesien, 1820–1864“, id 489271) – pro muže narozené po ~1800, tedy 19. století, ne pro napoleonskou dobu.
- ✔ **archivinformationssystem.at** – katalog Kriegsarchivu (1809: protokoly armádních sborů, indexy Böhmisch-Mährisches Armeekommando, Landwehr/Landsturm); jen soupisy fondů, ne jednotlivci.
- ✔ **Vojenský ústřední archiv – Vojenský historický archiv (VÚA-VHA) Praha** drží podle Kriegsarchivu **vojenské matriky** a část konskripcí; online jen databáze padlých 1. a 2. sv. války
  (už používáme, vuapraha.cz/databaze-vha). Pro napoleonskou dobu online nic nenalezeno (? zkusit katalog NAD/VÚA).
- ✔ **Kniha o odvodech v Čechách 1775–1835** (monografie; prameny: matriky, vojenské konskripce, soupisy poddaných, velkostatkové fondy) – návod, kde hledat; velkostatkové fondy jsou stejné jako v oddíle E.
- ? **Konskripce a verbovací okresy**: každá ves patřila k pěšímu pluku (verbovací okres); seznamy odvedenců bývají ve velkostatkových fondech (SOA) a v Kriegsarchivu.
- ? **Ztrátové listiny 1809/1813–1815** a **Landwehr 1809** – katalog Kriegsarchivu je zmiňuje, jmenné seznamy online nenalezeny.
**Jak to dělat u nás (bez nové investice):**
1. V matrice čti poznámky „miles“, „Soldat“, „bei dem Regiment“, „gefallen“, „im Spital“, „invalid“, „Bataillon“, „Landwehr“ – u svědků, kmotrů, ženichů a v úmrtích.
   Příklady stop z jednoho projektu: ženich „voják z …“ ve sňatku 1809, za dva roky už vdova; „bývalý voják (Bataillon)“ v pozemkové knize 1816.
2. V úmrtích 1792–1815 hledej muže „na vojně“, „v lazaretu“ – domácí matrika občas zapíše i nezvěstného.
3. **Vdovy 1795–1816** (druhé sňatky, „vdova po vojákovi“) – nepřítomnost manžela vysvětluje rozpory ve věku a děti z druhého manželství.
4. Pokud předek přijde ve zdrojích jako „voják“, hledej jeho **Grundbuchsblatt** (je-li narozen 1800+) nebo **velkostatkovou konskripci** jeho obce.

## G. Ověřeno 30. 10. 2026 – co je skutečně online pro vyzkoušené obce
| Zdroj | Kde / jak | Co dává | Naše obce |
|---|---|---|---|
| **Josefský katastr 1787** (SOA Třeboň, fond NAD 70) | `digi.ceskearchivy.cz/<id>/<snímek>`; `trebon.py snimek <id> <sn> out.jpg` funguje; `misto`/`svazky` ho nevidí (jen matriky) – ID najdeš podle čísel | držitel každého čp. (jeden arch na dům, jméno v záhlaví, pozemky); vložené listy = převody otec→syn | Vlásenice/Čelistná/Libkova Voda/Vratišov 343404–343408 (jména v **343406**; Čelistná od sn. 25, Libkova Voda od sn. 80), Libkova Voda 343312, Chvojnov+Útěchovičky 343300, Radětín+Krasíkovice 343345–8, Rynárec 343377/81–2, Svépravice+Pobistryce 343387–9, Střítež? 343385–6, Nový Rychnov 343325, Červená Řečice 343282, Mezná+Houserovky 343313 (čp. 8 hledat od sn. 45) |
| **Pozemkové knihy statku Vlásenice/Libkova Voda** (SOA Třeboň fond 2592) | `digi.ceskearchivy.cz/126623`, `126624`, … | převody otec→syn 1808 a 1848, dědictví s věky dětí | Čelistná čp. 1 |
| **Pozemkové knihy MZA** (ARON MZA) | `mza.cz/aron/apu/<uuid>`; jen ve vestavěném prohlížeči (OpenSeadragon přes React fiber), snímky ID podle `/aron/api/aron/apu/<id>/entity` (ne po 10) | převody, výměnky, sourozenci s podíly, výmazy po desítkách let | Horní Poříčí kn. 14059 (rejstřík sn. 4), Veselka kn. 14090 (rejstřík sn. 4) |
| **Soupis poddaných podle víry 1651** | PDF Národního archivu `nacr.cz/wp-content/uploads/2019/02/Bechynsko_cele_H_zamceno.pdf` (a Plzeňsko, Berounsko); Vltavsko a Slánsko volně nejsou | hospodář, manželka, děti, čeleď s věkem (jen křestní jména u sekvestrovaných vsí) | Bechyňsko: Houserovka (Jan Mlynář), Čelistná str. 416; Libkova Voda/Sázava/Rynárec/Lipice nejsou |
| **FamilySearch – Velkostatek Nelahozeves (Lobkovicové)** | katalog 2632425, originály SOA Litoměřice; uživatel přihlášen v Chromu | **soupisy poddaných 1713–1725, 1730, 1737–1740, 1748–1845** (DGS 101580627–101580656; 1713 má 64 snímků), pozemkové knihy Nelahozevsi 1681–1798, 1802–1865, Libčice+Lobeček+Minice 1846–1873 (DGS 100928538), knihy svatebních smluv 1794–1842, testamentů 1794–1816, pozůstalostí 1796–1840 | Libčice/Letky? (ověřuje se) |
| **Berní rula 1654** | Kramerius/NDK po přihlášení (Bechyňský kraj sv. 4–7); Slánský kraj se nedochoval | hospodáři po jménech | – |
| **Tereziánský katastr** | jen badatelna NA Praha | – | online není |
| **Databáze vodních mlýnů** | vodnimlyny.cz, Chrome (viz oddíl D) | držitelé mlýnů 1651→1930, výpisy z matrik | Houserovka čp. 8, Kameníček, Hutě |
| **svobodnici.cz** | web | svobodníci 1654/1789 podle obcí | Houserovka |
**Zásady čtení:** nadpis každého archu josefského katastru je jméno držitele – stačí listovat po jednom snímku, čp. jsou po řadě. Pozemkové knihy čti podle rejstříku
(Lit. K = příjmení, odkaz na stranu). Smlouva + výmaz o desítky let později (např. 1866 u Zedníků 1827) vypíše datum úmrtí rodičů a sňatky sourozenců.

**FamilySearch – omezení (30. 10. 2026):** snímky se čtou jen běžným prohlížečem FamilySearch se zvětšením. **Nevykreslovat** plné rozlišení do vlastní stránky ani stahovat obrázky skriptem –
bezpečnostní kontrola to zablokuje jako obcházení. Čtení je pomalé a písmo v náhledu špatně čitelné, proto FamilySearch používat po rejstřících a jen na cílené stránky.
Soupis poddaných Nelahozeves 1713: Libčice list 35–38 (sn. 36–40), **Letky v něm nejsou**, čísla domů nejsou (od 1770); hledaná příjmení tam nebyla.
Další ke čtení pro Libčice: DGS 100944794 Pozemková kniha živností 1814–1869 (kovárny), 101580635 soupis 1772–74 (čp.), svatební smlouvy 100944787/8.

# Pomocníci (subagenti) – hotová zadání

Pomocník = další kopie Claude, která souběžně na pozadí hledá v matrikách podle přesného zadání. Výsledky píše jen do
`pracovni/pom_<větev>/vysledky.md`, **nikdy do `data/`**. Hlavní model (ty) každý nález ověří na snímku (aspoň výřez
hlavního řádku) a teprve pak zapíše do dat, na web a do deníku.

## Pravidla (osvědčená v jednom rodinném projektu)
- Spouštěj přes Agent s `model: "sonnet"` a `run_in_background: true`. Pokud je uživatel schválil, neptej se, jen jednou větou řekni, co běží.
- **Souběžně 2–4 pomocníci na různé větve.** Nástroje bez prohlížeče (`trebon.py`, `ebadatelna.py`, `aron_img.py`) nekolidují.
  **Prohlížeč (MZA Acta Publica) smí mít v jednu chvíli jen jeden pomocník** a ty ho mezitím nepoužívej (nebo použij jinou záložku).
- Zadání musí být samostatné (pomocník nezná konverzaci): složka projektu, technické pasti, přesná id knih, co je už doloženo
  (jména, data, domy), úkoly v pořadí od nejdůležitějšího a formát výsledku.
- Chtěj u neúspěchů **rozsah a co na snímcích skutečně bylo** – „nenalezeno“ od pomocníka je jen upozornění, ne důkaz.
- Pomocník v malém okně prohlížeče (600×322) čte hůř – u MZA mu napiš, ať čte malé výřezy.
- Pomocník občas omylem zavolá `… svazek` (zapisuje do data/svazky.json) – v zadání to výslovně zakaž; po návratu zkontroluj `git status data`.
- **Zakaž pomocníkům příkazy na pozadí a čekání (sleep, hromadné stahování).** 29. 10. 2026 se takhle zasekli všichni čtyři najednou
  („Agent stalled: no progress for 600s“) a nic neodevzdali. Ať píšou do vysledky.md průběžně po každém nálezu.
- `aron_img.py` úroveň: **0 = plné rozlišení**, 2 = čtvrtina. Do zadání to napiš správně. ARON bývá hodiny nedostupný (stahování vyprší) – pak větev odlož.
- Na těžký rukopis (18. století, slabé mikrofilmy) pouštěj pomocníka bez `model: "sonnet"` (silnější model) – sonnet to často vzdá po pár snímcích.
- **Zakaž hromadné zkoušení adres** (procházení stovek čísel knih / id po sobě). 29. 10. 2026 pomocník zkusil ~350 id
  na mza.cz a archiv počítač dočasně zablokoval. Čísla knih hledej přes seznam knih obce nebo vyhledávání archivu, nejvýš pár dotazů.
- **Model podle jistoty vodítka (30. 10. 2026):** slepé prohledávání = `sonnet`; dobré vodítko bez potvrzení (křest bez sňatku rodičů,
  opakovaný kmotr, rejstřík ukazuje list) = silnější model (`opus` nebo bez `model`). Do zadání napiš přesnou stopu a co už je prohledáno.
- **Webové zdroje ve vestavěném prohlížeči často ukazují ověření robota** (vodnimlyny.cz). Pomocník ho **neobchází**; web čte přes Chrome
  (`mcp__claude-in-chrome__*`, vlastní záložka, po sobě zavřít) nebo ohlásí, že se nedostal dál.
- **Nové typy zadání:** (a) síť kmotrů (ze `tools/kmotri.py` → křty dětí hledané rodiny, kmotr ukáže rodinu matky); (b) mlýny a statky
  (veřejné seznamy majitelů, pozemkové knihy); (c) ověření: „přečti znovu v plném rozlišení a potvrď“ u čtení jiného pomocníka.
- Po návratu: ověř, zapiš (`zapis.py`, `osoby.py`), deník, `kontrola.py`, commit, nasadit web – a hned pusť další kolo.

## Šablona A – SOA Třeboň / SOA Praha (bez prohlížeče)
```
Jsi pomocník při genealogickém výzkumu (soukromý rodokmen). Složka: <kořen projektu>
(Windows, Git Bash). Python VŽDY `python -I -X utf8`, ImageMagick `magick`. Do data/ NIC NEZAPISUJ (ani příkazy `svazek`)
– výsledky jen do pracovni/pom_<větev>/ (obrázky + vysledky.md).
Nástroje z kořene projektu:
- SOA Třeboň: `python -I -X utf8 tools/trebon.py misto|svazky|rejstrik <kniha> <písmeno>|snimek <kniha> <sn> <out.jpg> [nahled]`
- SOA Praha: `python -I -X utf8 tools/ebadatelna.py matriky "Obec"|info <id>|snimek <id> <sn> <out.jpg> [nahled]`
Náhled jen na orientaci (roky); jména čti z plného rozlišení a výřezu `magick in.jpg -crop WxH+X+Y -resize 2000x out.jpg`,
obrázek prohlédni nástrojem Read. Nejdřív rejstříky, pak kniha. Stahuj jen snímky, které čteš.
Doloženo: <osoby, data, čísla domů, rodiče>.
Knihy: <id – druh – roky – poznámka, kde je který rok>.
Úkoly (v pořadí): 1. … 2. … 3. …
Ke každému nálezu do vysledky.md: kniha, snímek, datum, úplný přepis (jména, stavy, domy, rodiče, prarodiče, kmotři/svědci),
„(?)“ u nejistot, souřadnice zápisu (zlomky 0–1). U neúspěchů rozsah a co tam bylo. Nic nevymýšlej. Na konci krátké shrnutí.
```

## Šablona B – MZA Brno (prohlížeč, jen jeden pomocník najednou)
```
Jsi pomocník … (stejný úvod). Do data/ NIC NEZAPISUJ – výsledky jen do pracovni/pom_<větev>/vysledky.md.
Pracuješ v prohlížeči (mcp__Claude_Browser__*) na https://www.mza.cz/actapublica. Obrázky nestahuj, jen prohlížej.
Seznam knih obce: v JS fetch('/actapublica/matrika/hledani_obec?search_by_obec='+encodeURIComponent('Obec')+'&page='+p),
rozparsuj tabulku (odkaz detail/<id>). Otevři https://www.mza.cz/actapublica/matrika/detail/<id>, počkej 3 s; v JS:
window.prepareSeadragonHeight=()=>{};window.updateSeadragonHeight=()=>{}; g_viewer.element přes celou obrazovku
(position fixed, 100vw×100vh, zIndex 99999, background #fff). __base=g_viewer.world.getItemAt(0).source.tilesUrl
.replace(/-\d{5}\.jp2_files\/$/,''); snímek n: g_viewer.open(__base+'-'+String(n*10).padStart(5,'0')+'.jp2.dzi')
+ čekat na 'open' + 2,5 s. Výřez: b=g_viewer.world.getItemAt(0).getBounds(); g_viewer.viewport.fitBounds(new
OpenSeadragon.Rect(b.x+b.width*x0,b.y+b.height*y0,b.width*(x1-x0),b.height*(y1-y0)),true). Před screenshotem čekej na
getFullyLoaded() + 1,5 s. Okno je malé – čti malé výřezy. JS volání drž pod 40 s.
Doloženo: … Knihy: … Úkoly: … (formát výsledku jako v šabloně A)
```

## Co se osvědčilo zadávat
- Hledání rodičů u osoby narozené po ~1925: sňatek rodičů v místě a letech kolem narození (katolické, evangelické, civilní).
- Starší generace: narození (z věku ve sňatku), sňatek rodičů, úmrtí s věkem (uvádí narození a rodiče).
- Sourozenci z dobrovolnického rejstříku Třeboň (`rejstrik`) – rychle dají celou rodinu z jednoho domu.

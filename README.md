# Skill „rodokmen“ pro Claude Code

Pomocník, který s Claude Code vede rodokmen z českých matrik a zároveň staví rodinný web (předci, mapa, zajímavosti, příběh rodu).
Říkáš mu česky, koho hledáš, a on to sám dohledá v online archivech (SOA Třeboň, SOA Praha, SOA Zámrsk/ARON, MZA Brno, Porta fontium a další),
přečte zápisy, zapíše je do dat a ukáže ti výsledek na webu.

Tohle je upravená verze skillu [sarsonj/rodokmen-skill](https://github.com/sarsonj/rodokmen-skill) 0.5.0 (MIT). Přibylo:
pravidlo „pracuj sám“, paralelní pomocníci (subagenti) s ověřením na snímku, postupy pro vyhledávání **mimo matriky**
(vrchnost a panství, pozemkové knihy, soupisy poddaných 1651, josefský katastr, mlýny, vojenské prameny, síť kmotrů a svědků),
nové nástroje `fronta.py` (kdo má nejlevnější další krok) a `kmotri.py` (síť kmotrů a svědků), práce s MZA/ARON přes prohlížeč a poučení z chyb.

## Co potřebuješ
- Claude Code (desktop nebo terminál)
- Python 3.9+, Node 20+, ImageMagick 7 (`magick`), git
- Prohlížeč pro MZA Acta Publica (vestavěný v Claude Code nebo Chrome s rozšířením)

## Instalace (ručně)
1. Stáhni repozitář (zelené tlačítko **Code → Download ZIP**, nebo `git clone`).
2. Složku `skills/rodokmen` zkopíruj do `~/.claude/skills/` (Windows: `C:\Users\<jméno>\.claude\skills\`).
3. Restartuj Claude Code.
4. Vytvoř si prázdnou složku pro svůj rodokmen, otevři ji v Claude Code a napiš: **„rodokmen“** (nebo „založ rodokmen“). Skill se tě zeptá na základní věci a založí projekt.

## Důležité
- **Data své rodiny nikdy nedávej na veřejný GitHub.** Skill je napsaný tak, aby se do repozitáře dával jen kód a nastavení, ne osoby, zápisy a fotky.
- Web se skutečnými daty zveřejňuj jen za heslem nebo neveřejně; žijící osoby jen jméno a rok.
- Skill začíná „Pravidly uživatele“, která dávají Claudovi velkou volnost (nemusí se ptát). Chceš-li víc kontroly, v `SKILL.md` je uprav.
- Adresy, čísla knih a postupy u archivů se mění. Když něco nefunguje, nech Claude zapsat poznámku do `poznamky_pro_skill.md`.

## Licence
MIT (viz `LICENSE`). Původní autor: Jindřich Šaršon. Soubor `skills/rodokmen/reference/playbook.md` MIT nepodléhá (hlavička souboru).

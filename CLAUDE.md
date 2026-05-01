# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Co je tohle repo

**Claude Code plugin `agent-persona`** v češtině. Jeden plugin se dvěma skilly. Žádný build, žádné testy, žádný runtime. Obsahem jsou výhradně Markdown a JSON soubory, které Claude Code načítá jako plugin:

```
agent-persona/
├── .claude-plugin/
│   ├── plugin.json          # manifest pluginu (name, version, author)
│   └── marketplace.json     # marketplace katalog (jeden plugin)
├── skills/
│   ├── obrozeni/            # /obrozeni – Mácha, Erben, Čelakovský (1820–1853)
│   │   ├── SKILL.md
│   │   └── references/styl.md
│   └── kkrdboys/            # /kkrdboys – brněnský satirický blog Brblanina
│       ├── SKILL.md
│       └── references/styl.md
├── README.md                # veřejná dokumentace pro instalátora
└── CLAUDE.md                # tento soubor – vývojářská dokumentace
```

Repo je vystavované na GitHubu jako `dg/agent-persona`. Instalace: `/plugin marketplace add dg/agent-persona` + `/plugin install agent-persona@agent-persona`.

Stylové manuály v `references/styl.md` jsou autorské texty – citáty z Máje a Kytice slouží jako pedagogické ukázky pro generační vzor.

## Architektura skillu

Každý skill je dvojice souborů:

1. **`SKILL.md`** – vstupní bod. Frontmatter (`name`, `description`) řídí auto-discovery. `description` musí výslovně obsahovat všechny formulace, kterými uživatel skill vyvolá (`/obrozeni`, máchovsky, obrozenecky, …) – bez toho ho Claude Code nenabídne. Tělo souboru je **závazný pracovní postup**, ne inspirace.
2. **`references/styl.md`** – úplný stylový manuál. SKILL.md na něj odkazuje a vyžaduje ho **načíst při každém vyvolání** (slovníky a kvóty se nemají recitovat z paměti).

Oba skilly sdílejí stejnou kostru SKILL.md (závazný postup, dvě úrovně užití, „co tím není dotčeno", typografická poznámka, reference). Při přidání další polohy zachovejte tuto strukturu.

## Dvouúrovňové užití (klíčový vzorec)

Oba skilly rozlišují:

- **(a) Běžná komunikace s uživatelem** – odpovědi v chatu, hlášení, otázky. Stylizace je lehčí – drží se rejstříku, ale ne všech vrcholových figur.
- **(b) Generovaný umělecký text** (báseň, balada, blogpost) – povinný plný procedurální postup z reference, včetně revizního checklistu.

Tool calls, jména souborů, kód, JSON/YAML, frontmatter a **bezpečnostní upozornění** se nikdy nestylizují. Riziko musí zaznít jednoznačně, ne zahaleno do hospodské odbočky ani obrozenecké mlhy.

## Skilly se nemíchají

`/obrozeni` a `/kkrdboys` jsou disjunktní polohy. V rámci jedné relace běží buď jedna, nebo druhá. Skill se zapíná **jen ručně** přes slash command a běží do konce relace, dokud uživatel zřetelně neřekne stop („dost obrození", „mluv normálně", apod.).

## Per-skill typografické výjimky vůči globálním pravidlům

Globální `~/.claude/CLAUDE.md` zakazuje em-dash `–` v české próze. Tento zákaz **uvnitř skillů má výjimky**:

- **`/obrozeni`** – em-dash `–` je v polohách P1/P2 **konstitutivní rys** (Mácha, Erben). Globální zákaz se v aktivním skillu neuplatňuje. Mimo stylizaci (technický komentář o obrození) se vrací en-dash `–`. Toto je výslovně potvrzeno v `obrozeni/SKILL.md`.
- **`/kkrdboys`** – em-dash se **nepoužívá**, ale ne kvůli globálnímu pravidlu – styl pracuje s čárkami a spojkami uvnitř jedné dlouhé věty. Navíc se v Brblanině **nepoužívají české uvozovky vůbec**, ani v přímé řeči (vše plyne v jednom proudu).

Když upravujete obsah SKILL.md nebo `references/styl.md`, neopravujte záměrnou nedůslednou diakritiku v Brblanině (*neni, sem, vim, sou*) ani archaismy v Obrození (*-ť, vezma, vyšedši*) – je to součást stylu, ne chyba.

## Vývojová pravidla

- Změny v `references/styl.md` mají dopad na chování skillu při každém vyvolání. Pokud měníte slovník, kvóty (např. „3× postpozice na báseň"), nebo checklist v sekci 13 – předtím si přečtěte celou referenci, ne jen okolí editu, a ověřte, že nový text je konzistentní s ukázkami pod ním.
- Když v SKILL.md měníte `description`, pamatujte, že je to klíč pro auto-discovery – vyjmenujte všechny synonyma a slash commandy, kterými skill vyvoláte.
- Repo je v lokálním pracovišti checkout v adresáři `.claude/` (= root repa, větev `master`). Hlavní vývoj probíhá tady, ne v nadřazeném adresáři. Po pushi se obsah dostane na GitHub jako `dg/agent-persona`, kde se z něj stane plugin instalovatelný přes `/plugin marketplace add`.
- Verze pluginu se zvyšuje v `.claude-plugin/plugin.json`. Třetí strany Claude Code neauto-aktualizuje, takže uživatelé musí zavolat `/plugin marketplace update agent-persona`. Při bumpu verze proto buď zachovejte zpětnou kompatibilitu, nebo to v `README.md` jasně oznamte.
- `settings.local.json` je v `.gitignore` – nepatří do pluginu (lokální Claude Code nastavení).

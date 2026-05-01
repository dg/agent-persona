# České stylové skilly pro AI agenty

Dva slash commandy, dva paralelní vesmíry. Jeden vás přenese na hřbitov pod Sněžkou, kde mladík před popravou rozjímá o věčnosti. Druhý do brněnské knajpy, kde Boban vykládá, jak si Lazy nechal namontovat gpsku do prdele.

Oba skilly přepnou AI agenta do originální polohy. Jakmile zavoláte `/obrozeni` nebo `/kkrdboys`, komunikace s vámi i generované texty znějí v daném rejstříku. Odpovědi v chatu, hlášení o dokončené práci, komentáře k chybám.

---

## `/kkrdboys` – KKRD Boys (satirický blog z Brna)

Stylizace do brněnského hospodského hlasu party KKRD Boys. Hantec, moravská obecná čeština, vulgarita jako metaforický systém. Hrabal s brutalitou 21. století, Hašek s neúctou k autoritám, Bukowski bez autocenzury. Všichni v jednom plzeňáku.

Vypadá to v praxi takhle:

> **uživatel:** /kkrdboys
>
> **Claude:** no tak co potřebuješ pasře, brus je smrknutej pivi natočený a kólo otevřený, hoď mi cokoli tě v hokně sere a já z toho vychrlim něco co bude mít aji hlavu aji patu
>
> **uživatel:** napiš krátký satirický článek o tom jak teď všichni dělaj programátory přes AI
>
> **Claude:**
>
> Se značným znepokojením sledujeme jak v naší partě posledních pár let mizí všichni co kdysi opravdu uměli psát kód, aji Tiba kerej býval v devadesátkách v Pivnici Padowec u konečný trajfu 5 takovým hostem že kdybys ho vzbudil ve tři ráno na betli odrecitoval ti RFC 7519 i s mezerama mezi řádkama, no a dneska ti otevře laptop drcne tam třema větama todle udělej a Claude mu to vychrlí komplit za 12 sekund i s testama i s docstringama i s vysvětlením proč to dělá tak a ne jinak, takže Tiba sedí v paluši U Doležalů na Hadech, hryze pivi, koukne na obrazovku, kývne s rejčema zkušenýho seniora a flákne to do mainu jak Lazy svýho času vyfláknul Sidonii do Hornbachu pro nový posuvný dveře co mu vypadávaly z kolejnic v ložnici dvakrát za měsíc kvůli kterým si pak zničil obě kolena, ovšem tvl rozdíl je ten že Lazy aspoň věděl proč ty dveře potřebuje, kdežto Tiba nemá ani potuchy co ten kód vlastně dělá, no a tak sedíme v Pivovarský u Domu stavbařů s Bobanem, Otou a Pavlem z Pivce, a probíráme co bude až nás všechny ta AI nahradí komplit, Pavel jediný todle neřeší pač už dvacet let nedělá nic, takže ovšem tvl už dávno dospěl tam kam my teprv dorazíme zhruba do roku 2027, a co si budem říkat, rozdíl mezi seniorem fullstack a Pavlem z Pivce se v posledních dvanácti měsících smrskl na to že Pavla z hokny vyšukal silikonovej vibrátor za 4 990 Kč z Hornbachu zatímco nás Claude za měsíční předplatný 20 ojro a do našich blbejch palic to ještě komplit nedošlo.
>
> **uživatel:** chci to jako commit message
>
> **Claude:** to by ti git commit -m vrátil jak revizor v Komíně lupeň od čtvrťáka, hodím ti tam zkrácenou punchlinu pod 70 znaků: `feat: claude šuká seniory za 20 ojro měsíčně, hornbach předražuje`

Hodí se na recenzi nového hipster bistra v Židenicích, retrospektivu sprintu kde nikdo neumí říct co se vlastně dělalo, nebo error message po pádu produkce kterou si pověsíš v kanceláři. Vulgarit je tam plno, takže do firemní wiki to nedávejte, do PR review taky ne, a do Slacku šéfovi už vůbec ne. Pondělko vám to ovšem rozjede líp než dvojité ristretto z Iggy Popa v Komíně za 75 kaček.

## `/obrozeni` – Mácha, Erben, Čelakovský

Stylizace do češtiny vrcholného obrození a romantismu (1820–1853). Archaický slovosled atributu (*lůny tvář*, *lásky čas*, *věčnosti byt*), přechodníky bez ostychu (*vezma, vyšedši, pohleděv*), litanie zmaru *„zbortěné harfy tón, ztrhané strůny zvuk, zašlého věku děj…“*, finální výkřik *„Hynku! – Viléme!! – Jarmilo!!!“*.

Vypadá to v praxi takhle:

> **uživatel:** /obrozeni
>
> **Claude:** Skill „obrozeni“ v platnost uveden jest. Od této chvíle pravím a píši v duchu české literatury vrcholného obrození, polohu zvolím dle žádosti tvé. Co ti, milý uživateli, na srdci leží?
>
> **uživatel:** spadl mi deploy na produkci, máš tušení proč
>
> **Claude:** Otevřev poslední záznam pádu, čtu o kontejneru, an zhynul při probuzení svém: proměnná DATABASE_URL, ana ve stagingu věrně sloužila, do říše výrobní přenesena nebyla. Příčina ne valoun těžký, leč přehlédnutí drobné – jak když poutník na rozcestí plášť svůj zapomene. Mám-li ji v secrets manageru obnoviti, či raději počkati, až sám rozhodneš?
>
> **uživatel:** jo, a napiš mi k tomu dvojverší ať to pošlu týmu
>
> **Claude:**
> > Bylť pozdní pátek – deploye čas –
> > i kontejner v lůně tmy zhasl bez hlas.

Hodí se na pohřební řeč pro křečka, baladu o tom, jak si polednice přišla pro padlý unit test, prozaické otevření kapitoly o brněnském tramvajáku stylem Marinky, případně commit message v jazyce Pouti krkonošské.

---

## Instalace

Plugin obsahuje dva skilly ve formátu `SKILL.md`. Po instalaci se zpřístupní jako slash commandy `/obrozeni` a `/kkrdboys`.

**Claude Code** (nativní podpora pluginů):

```
/plugin marketplace add dg/agent-persona
/plugin install agent-persona@agent-persona
```

Nebo přes `/plugin` → záložka **Discover**. Aktualizace: `/plugin marketplace update agent-persona` (Claude Code u třetích stran auto-update neprovádí sám).

**Ostatní nástroje** (Codex, Cursor, Gemini CLI a další, které umí načíst `SKILL.md`):

Naklonujte repo a zkopírujte adresáře `skills/obrozeni/` a `skills/kkrdboys/` do místa, kde váš nástroj hledá skilly.

## Co bude dál

V plánu jsou další polohy. A pokud vás napadá styl, který v sadě chybí, dejte vědět.

Hodně zábavy přeje

**David Grudl**

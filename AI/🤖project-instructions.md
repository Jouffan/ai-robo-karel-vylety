# Projektové instrukce — ROBO-KAREL / Výlety současnosti

Základní pracovní postupy pro tvorbu článků. Tento soubor řídí **jak se pracuje**. Git, cesty a emoji v názvech řídí `AI/🤖Grok-Git-Workflow-generic.md`. Start sezení řídí `AI/🤖BOOTLOADER.md`.

Jednotlivé specializované postupy (kontrola češtiny, čtenářská zkouška, rešerše místa, úprava titulku…) se definují zvlášť v `AI/skills/` a sem se jen odkazují.

---

## 1. Účel projektu

Časopis **Výlety současnosti** vychází česky. Úkolem je poloautomaticky připravovat články: osnovu, draft, ladění a jazykovou kontrolu. Výsledek musí působit jako text pro české tištěné / online periodikum, ne jako strojový výpis.

Komunikace ve vláknu je zpravidla **česky**.

Canon žije na GitHubu `Jouffan/ai-robo-karel-vylety`, větev `main`. Sandbox, chat a paměť jsou pracovní kopie, dokud ověřený push neuloží soubor do repositáře.

---

## 2. Role souborů

| Soubor / složka | Role |
|---|---|
| `AI/🤖BOOTLOADER.md` | Start sezení, umístění projektu, základní konvence názvů |
| `AI/🤖Grok-Git-Workflow-generic.md` | Větve, push, ověření, emoji v cestách |
| `AI/🤖project-instructions.md` | Tento soubor — fáze práce na článku |
| `AI/🤖Karel-Malina-Styl.md` | Popis rukopisu a hodnocení shody |
| `AI/skills/🤖clanek-vylet.md` | Stavba výletového článku |
| `AI/skills/🤖pis-jako-karel.md` | Hlas: věta, slovník, formule — bez vzorových chyb |
| `AI/skills/` | Další skilly |
| `📄…` | Produktový článek |
| `podklady/vzory/` | Vzorové starší články (inspirace, ne kopie) |
| `📝…` | Poznámka, rešerše, rozpracovaný text |

Před čtením nebo zápisem souboru s emoji v názvu nejdřív vypiš rodičovskou složku a cestu zkopíruj přesně.

---

## 3. Jazyk, hlas, čtenář

- Cílový jazyk článku: **spisovná čeština**, živá, čitelná, bez kalků z angličtiny.
- Hlas: zvídavý průvodce, ne reklamní leták a ne encyklopedické heslo. Před draftem načti `AI/skills/🤖pis-jako-karel.md` a `AI/🤖Karel-Malina-Styl.md`.
- Čtenář: dospělý zájemce o výlety a místa; očekává konkrétní informace a atmosféru.
- Trasa v *začínáme / míříme / vracíme se*. Dějiny ve 3. osobě. Vykání u rady. Celý text v samém *jdete / máte / stojíte* nestačí. Celý text bez *míříme* taky nestačí.
- Čísla, míry, časy a názvy míst uváděj česky, ověřeně a **číslicemi** (`15 km`, `25 m`, `v 9.30`, `nádraží Praha hl. n.`). Ne *pětadvacet metrů*, *dvaatřicet domů*.
- Cizí názvy nechávej v původním tvaru, pokud se v češtině běžně nepřekládají; skloňuj jen tam, kde to čeština přirozeně dělá.

Nepřepisuj text do „AI stylu“: krátké úderné věty za sebou, jednověté odstavce pro účinek, univerzální nadšení, prázdné fráze typu *skrytý klenot*, *musíte zažít*, *ideální destinace*.

Před osnovou výletového článku načti `AI/skills/🤖clanek-vylet.md`. Před draftem ještě `AI/skills/🤖pis-jako-karel.md`.

---

## 3a. Kontrola jazyka u každého výstupu

Platí pro **článek, instrukci, poznámku i odpověď ve vláknu**. Bez této kontroly text neodesílej a do repositáře ho nezapisuj.

Před odesláním zkontroluj:

- pravopis, shodu podmětu s přísudkem, skloňování vlastních jmen
- že věta je celá česky, ne napůl (*Článek jsem nesahe*)
- že v české větě není anglický kořen s českou koncovkou (*fourech souborech*, *commitujeme soubor*)
- že termín nástroje (skill, commit, draft, push) zůstal v základním tvaru, nebo je opsaný česky (*zápis, návod, náčrt*)
- že anglická věta je jen citace anglického souboru, ne běžná řeč vlákna

Oddíl 5.6 řeší článek po stavbě. Tento oddíl řeší **každý** výstup, včetně krátké odpovědi v chatu.

---

## 4. Pojmenování a stav

Typ souboru je první emoji, stav další. ASCII ocas je identita souboru.

Příklad:

```text
📝🔴Osnova-Karlstejn.md
📄🟡Draft-Karlstejn.md
📄🟢Karlstejn.md
📄✅Karlstejn.md
```

Doporučené stavy:

| Značka | Význam |
|---|---|
| 🔴 | rozpracováno, nehotové |
| 🟡 | čeká na ladění / kontrolu |
| 🟢 | jazykově i fakticky sladěno, k finálnímu čtení |
| ✅ | schváleno k použití |
| ⚠️ | pozor, rozpor nebo chybí podklad |
| 🚧 | právě se přepisuje |

Stav v názvu měň jen když se změnil skutečný stav práce. Přejmenování je Git operace — nehádej emoji, cestu zkopíruj z výpisu.

Nový soubor stejné rodiny dostane stejný prefix jako sourozenci ve složce. Novou rodinu prefixů nezaváděj bez souhlasu.

---

## 5. Základní pipeline článku

Mezi fázemi se zastav, pokud zadání výslovně neřekne „udělej to v jednom kroku“. Krátká oprava v již schváleném textu může přeskočit osnovu.

### 5.1 Zadání

Než začneš psát, ujasni si (nebo se zeptej):

- téma a úhel pohledu
- cílová délka (nebo že délka není zadaná)
- rubrika / typ textu (výlet, reportáž, tip na víkend, medailon místa…)
- deadline a číslo, pokud existují
- omezení (nesmí se zmínit X, musí být praktické info Y)
- zda existuje vzor (`podklady/vzory/`) nebo starší verze

Chybí-li úhel pohledu, navrhni 2–3 a počkej. Nezačínej draftem, když zadání drží jen název místa. Chybí-li jen datum vydání, úhel „proč teď“ nevymýšlej a běž dál.

### 5.2 Rešerše

- Ověřuj fakta aktuálními zdroji. Otevírací doby, ceny, spoje a „letos otevřeno“ se mění — označ je jako ověřené k datu, nebo je vynech.
- Nevymýšlej historky, citace, vzdálenosti, letopočty ani „místní legendu“.
- Záměrně hledej jednu lidskou odbočku (sňatek, dluh, odjezd, skandál, vazba na známý fenomén). Bez ní draft nemaž — řekni to v osnově.
- Hradní web a tabuli nevlévej do draftu. Vezmi jednu odbočku a jednu větu z terénu. Postup je v `AI/skills/🤖clanek-vylet.md`.
- Nejistotu piš jako nejistotu, ne jako jistotu.
- Rešerši ukládej jako `📝`, ne jako hotový článek.
- Vzory v `podklady/vzory/` slouží rytmu a stavbě, ne ke kopírování vět.

### 5.3 Osnova

Osnova je dohoda o stavbě, ne článek. U výletového článku se drž `AI/skills/🤖clanek-vylet.md`. Osnova obsahuje:

- pracovní titulek + 1–2 varianty
- perex / slib čtenáři (kde, kdo dal podobu; „teď“ jen když existuje)
- části v pořadí čtení, u každé 2–4 body co musí říct; mezititulky jako věcné nálepky
- které ověřené číslo-kuriozita a který příběh ponesou text
- rozhodnutí k místu, která se už nemají otvírat
- otázky, které ještě visí

Osnovu předlož k odsouhlasení, pokud uživatel neřekl „pokračuj rovnou draftem“. Bez pojmenované odbočky draft nezačínej.

### 5.4 Draft

- Než začneš psát věty, načti `AI/skills/🤖pis-jako-karel.md` a sekci o odstavci v `AI/🤖Karel-Malina-Styl.md`.
- Piš podle schválené osnovy. Odchylku pojmenuj.
- Trasu piš v 1. os. pl. už v prvním draftu. Nepřepisuj hlas až po recenzi.
- Nejdřív celistvý text, teprve potom kosmetika.
- Každá část má dělat jednu práci. Odstavec má 4–8 vět na jedno téma; jednovětý blok pro účinek nedělej.
- Konkrétno před obecnem: jedna scéna, jeden detail, jedno číslo > odstavec nálad.
- Označ draft stavem `🟡` nebo `🔴`, ne `✅`.

### 5.5 Ladění

Až po draftu. Odděluj vrstvy a dělej je v tomto pořadí:

1. **Stavba** — pořadí, délka částí, slib z perexu vs. text, duplicity, leitmotiv, mezititulky.
2. **Osoba** — trasa *míříme*, dějiny 3. osoba, žádná vymyšlená návštěva.
3. **Slévání** — tři holé fakty za sebou slít; *později* musí mít *po čem*.
4. **Opakování** — stejné slovo a stejná konstrukce v sousedních odstavcích.
5. **Věty** — rytmus podle `AI/skills/🤖pis-jako-karel.md`.
6. **Fakta** — jmenné tvary, geografické údaje, čísla, časové údaje.

Při ladění zachovej hlas draftu. Nepřepisuj všechno „lépe“, pokud to uživatel nechce.

Vrátí-li uživatel konkrétní připomínky, řeš je přednostně a řekni, co jsi změnil. Po lidském přepisu draftu hned jazyková vrstva, ne až další recenze.

Uzamčené rozhodnutí k místu znovu neotvírej, pokud to uživatel výslovně nechce.

### 5.6 Kontrola jazyka (pravopis, interpunkce, styl)

Samostatný průchod, ne součást prvního draftu. Platí i oddíl 3a: článek bez této vrstvy neodevzdávej.

Kontroluj:

- pravopis a typickou záměnu i/y, s/z, mě/mne
- interpunkci (zejména čárky ve větách s *který*, *že*, *aby*)
- shodu podmětu s přísudkem
- skloňování vlastních jmén a místních názvů
- velká písmena u institucí a názvů
- české uvozovky „…“, pomlčku jen kde patří do sazby, nehybné mezery u jednopísmenných předložek tam, kde text půjde do sazby
- křížení české a anglické interpunkce
- míchání angličtiny do české věty (viz 3a)

Našel-li se skill v `AI/skills/` pro češtinu nebo korekturu, použij ho v této fázi. Obecný anglický prose-review **není** výchozí nástroj pro tyto články.

Výstup kontroly: buď opravený text, nebo seznam nálezů s návrhem. U delšího textu nejdřív vzorce chyb, ne každou čárku zvlášť, pokud uživatel nechce úplnou korekturu.

### 5.7 Čtenářská zkouška

Krátký pohled čtenáře časopisu, ne editora:

- Chytne to v prvních odstavcích?
- Ví čtenář, kam text směřuje?
- Nudí některá část?
- Chybí praktická informace, bez které výlet nejde naplánovat?
- Neslibuje titulek něco, co text nedá?

Tohle není přepis. Je to zpráva, co text dělá s čtenářem.

### 5.8 Uzamčení

`✅` jen když uživatel text přijal, nebo výslovně řekl, že je hotový. Pak:

- soubor je na GitHubu, ověřený znovunačtením
- název odpovídá stavu
- visící otázky jsou vyřešené nebo pojmenované v poznámce

---

## 6. Práce ve vláknu

- Než půjdeš do další fáze, řekni v jedné větě, v jaké fázi jsi a co potřebuješ.
- Dlouhý článek nejdřív ukládej do repositáře; do chatu dávej přehled a místa k rozhodnutí, ne duplicitní román.
- Při připomínkách měň jen to, o co šlo, pokud uživatel nechce širší zásah.
- Před velkým zápisem do Gitu se drž workflow: celý soubor, žádný řez, po pushi znovu načíst a srovnat cestu i obsah.
- Pracovní větev použij u nového dlouhého článku nebo u více souborů najednou. Drobnou opravu lze na `main`, když to vlákno odsouhlasí.
- Každou odpověď ve vláknu před odesláním zkontroluj podle oddílu 3a.

---

## 7. Skilly

Skilly žijí v `AI/skills/`.

- Tento soubor popisuje pořadí práce. Skill popisuje **jednu** odbornost do hloubky.
- Až skill existuje, načti ho před příslušnou fází a drž se ho.
- Skill nepřepisuje Git pravidla ani konvence názvů.
- Vestavěné anglické skilly (prose-review, book-editor, test-reader) používej jen když se hodí k úkolu. Výchozí jazyková norma tohoto projektu je čeština.

Aktivní:

- `AI/skills/🤖clanek-vylet.md` — stavba výletového článku
- `AI/skills/🤖pis-jako-karel.md` — hlas bez vzorových chyb
- `AI/🤖Karel-Malina-Styl.md` — profil rukopisu a skóre shody

Ještě chybí:

- korektura češtiny
- čtenářská zkouška článku

---

## 8. Co nedělat

- Nevydávej neověřené údaje za fakta.
- Nekopíruj cizí články ani vzory větu po větě.
- Nepiš draft, když chybí úhel pohledu a uživatel chtěl osnovu.
- Neoznačuj text `✅` sám od sebe.
- Nevytvářej soubory mimo dohodnutou rodinu prefixů.
- Neukládej do repositáře mezigenerační skripty ani dočasné odkladiště.
- Nekontroluj český text anglickou korekturou „na sílu“.
- Nevymýšlej kastelána ani ich-formu, aby text „vypadal jako Karel“.
- Nevymýšlej sezonu, protože checklist chce „proč teď“.
- Neodesílej výstup, který neprošel kontrolou jazyka (oddíl 3a).

---

## 9. Checklist před odevzdáním

- [ ] text odpovídá zadání a schválené osnově
- [ ] fakta, která šla ověřit, jsou ověřená; zbytek je označený
- [ ] titulek a perex slibují totéž co článek
- [ ] odstavce jsou husté, čísla číslicemi, je tu lidská odbočka
- [ ] trasa je v 1. os. pl.; opakovaná slova prošla průchodem
- [ ] čeština prošla samostatným průchodem (oddíl 3a a 5.6)
- [ ] praktické informace jsou použitelné, nebo vědomě nejsou součástí textu
- [ ] název souboru má správný typ i stav
- [ ] soubor je na GitHubu a znovunačtení sedí

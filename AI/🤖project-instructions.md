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
| `AI/skills/` | Samostatné skilly (až vzniknou) |
| `📄…` | Produktový článek |
| `📜…` | Vzorový starší článek (inspirace, ne kopie) |
| `📝…` | Poznámka, rešerše, rozpracovaný text |

Před čtením nebo zápisem souboru s emoji v názvu nejdřív vypiš rodičovskou složku a cestu zkopíruj přesně.

---

## 3. Jazyk, hlas, čtenář

- Cílový jazyk článku: **spisovná čeština**, živá, čitelná, bez kalků z angličtiny.
- Hlas: zvídavý průvodce, ne reklamní leták a ne encyklopedické heslo.
- Čtenář: dospělý zájemce o výlety a místa; očekává konkrétní informace a atmosféru.
- Vykej, pokud zadání neurčí jinak.
- Čísla, míry, časy a názvy míst uváděj česky a ověřeně (`15 km`, `v 9.30`, `nádraží Praha hl. n.`).
- Cizí názvy nechávej v původním tvaru, pokud se v češtině běžně nepřekládají; skloňuj jen tam, kde to čeština přirozeně dělá.

Nepřepisuj text do „AI stylu“: krátké úderné věty za sebou, univerzální nadšení, prázdné fráze typu *skrytý klenot*, *musíte zažít*, *ideální destince*.

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
- zda existuje vzor (`📜`) nebo starší verze

Chybí-li úhel pohledu, navrhni 2–3 a počkej. Nezačínej draftem, když zadání drží jen název místa.

### 5.2 Rešerše

- Ověřuj fakta aktuálními zdroji. Otevírací doby, ceny, spoje a „letos otevřeno“ se mění — označ je jako ověřené k datu, nebo je vynech.
- Nevymýšlej historky, citace, vzdálenosti, letopočty ani „místní legendu“.
- Nejistotu piš jako nejistotu, ne jako jistotu.
- Rešerši ukládej jako `📝`, ne jako hotový článek.
- Vzory `📜` slouží rytmu a stavbě, ne ke kopírování vět.

### 5.3 Osnova

Osnova je dohoda o stavbě, ne článek. Obsahuje:

- pracovní titulek + 1–2 varianty
- perex / slib čtenáři (1–3 věty)
- části v pořadí čtení, u každé 2–4 body co musí říct
- praktický box (doprava, čas, obtížnost, sezóna), pokud se k typu textu hodí
- otázky, které ještě visí

Osnovu předlož k odsouhlasení, pokud uživatel neřekl „pokračuj rovnou drafem“.

### 5.4 Draft

- Piš podle schválené osnovy. Odchylku pojmenuj.
- Nejdřív celistvý text, teprve potom kosmetika.
- Každá část má dělat jednu práci: zavést místo, vést trasu, dát kontext, předat praktickou informaci, uzavřít.
- Konkrétno před obecnem: jedna scéna, jeden detail, jedno číslo > odstavec nálad.
- Označ draft stavem `🟡` nebo `🔴`, ne `✅`.

### 5.5 Ladění

Až po draftu. Odděluj vrstvy:

1. **Stavba** — pořadí, délka částí, slib z perexu vs. text, duplicity.
2. **Věty** — rytmus, přesnost sloves, zbytečná přídavná jména, opakované starty vět.
3. **Fakta** — jmenné tvary, geografické údaje, čísla, časové údaje.

Při ladění zachovej hlas draftu. Nepřepisuj všechno „lépe“, pokud to uživatel nechce.

Vrátí-li uživatel konkrétní připomínky, řeš je přednostně a řekni, co jsi změnil.

### 5.6 Kontrola jazyka (pravopis, interpunkce, styl)

Samostatný průchod, ne součást prvního draftu.

Kontroluj:

- pravopis a typickou záměnu i/y, s/z, mě/mne
- interpunkci (zejména čárky ve větách s *který*, *že*, *aby*)
- shodu podmětu s přísudkem
- skloňování vlastních jmén a místních názvů
- velká písmena u institucí a názvů
- české uvozovky „…“, pomlčku —, nehybné mezery u jednopísmenných předložek tam, kde text půjde do sazby
- křížení české a anglické interpunkce

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

---

## 7. Skilly

Skilly žijí v `AI/skills/`.

- Tento soubor popisuje pořadí práce. Skill popisuje **jednu** odbornost do hloubky.
- Než skill vznikne, dělej danou fázi podle této pipeline a řekni, že jde o obecný postup.
- Až skill existuje, načti ho před příslušnou fází a drž se ho.
- Skill nepřepisuje Git pravidla ani konvence názvů.
- Vestavěné anglické skilly (prose-review, book-editor, test-reader) používej jen když se hodí k úkolu. Výchozí jazyková norma tohoto projektu je čeština.

Navrhované první skilly (až se budou zakládat):

- osnova článku pro Výlety současnosti
- draft výletového článku
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
- Neplní český text anglickou korekturou „na sílu“.

---

## 9. Checklist před odevzdáním

- [ ] text odpovídá zadání a schválené osnově
- [ ] fakta, která šla ověřit, jsou ověřená; zbytek je označený
- [ ] titulek a perex slibují totéž co článek
- [ ] čeština prošla samostatným průchodem
- [ ] praktické informace jsou použitelné, nebo vědomě nejsou součástí textu
- [ ] název souboru má správný typ i stav
- [ ] soubor je na GitHubu a znovunačtení sedí

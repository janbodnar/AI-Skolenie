# Benchmarky veľkých jazykových modelov (LLM)

**Benchmarky** sú štandardizované testy a hodnotenia, ktoré merajú schopnosti
veľkých jazykových modelov (LLM) v rôznych úlohách – od znalostí a logického
uvažovania až po generovanie kódu a pravdivosť odpovedí.

> 💡 **Jednoduchá metafora:**
> Predstavte si, že LLM modely sú študenti a benchmarky sú skúšky. Rovnako
> ako na univerzite máte skúšky z matematiky, jazykov a logiky, aj AI modely
> absolvujú „skúšky" – benchmarky – aby sme vedeli, v čom sú silné a kde
> majú medzery.

**Prečo sú benchmarky dôležité?**

> 🎓 **Definícia:** *Benchmark je štandardizovaná sada úloh s pevne definovanými
> pravidlami hodnotenia, ktorá umožňuje objektívne a opakovateľné porovnanie
> výkonu rôznych AI modelov.*

- Umožňujú **objektívne porovnanie** modelov od rôznych vývojárov (OpenAI, Google, Meta, Anthropic...)
- Odhaľujú **silné a slabé stránky** – model môže excelovat v kódovaní, ale zlyhávať v matematike
- Pomáhajú **sledovať pokrok** v čase – ako sa modely zlepšujú medzi generáciami
- Slúžia ako **spoločný jazyk** pre výskumníkov, vývojárov aj používateľov


## Čo benchmarky merajú? Typy hodnotených schopností

LLM benchmarky pokrývajú široké spektrum schopností. Každý benchmark sa zameriava
na iný aspekt „inteligencie" modelu:

| Kategória | Čo sa meria | Príklad benchmarku |
|-----------|-------------|-------------------|
| **Znalosti a porozumenie** | Vedomosti z rôznych odborov (história, právo, medicína...) | MMLU |
| **Logické uvažovanie** | Schopnosť riešiť logické a matematické problémy | GSM8K, BIG-bench |
| **Generovanie kódu** | Schopnosť písať funkčný programovací kód | HumanEval |
| **Pravdivosť a faktickosť** | Odolnosť voči generovaniu nepravdivých informácií | TruthfulQA |
| **Konverzačné schopnosti** | Kvalita odpovedí v dialógu, koherencia, užitočnosť | MT-Bench |
| **Komplexné hodnotenie** | Kombinácia viacerých schopností v jednom frameworku | HELM, BIG-bench |

> 🎯 **Pre študentov:** Žiadny jednotlivý benchmark nedokáže zachytiť „celkovú
> inteligenciu" modelu. Preto sa vždy používa **kombinácia viacerých benchmarkov**,
> aby sme získali komplexný obraz.

---

## Najznámejšie LLM benchmarky

### 📘 MMLU (Massive Multitask Language Understanding)

**Čo meria:** Znalosti a porozumenie v 57 rôznych odboroch – od matematiky
a fyziky cez históriu, právo, medicínu až po informatiku.

**Metodika:**
```
Formát: Výber z možností (multiple-choice), 4 možnosti (A, B, C, D)
Počet otázok: ~15 700
Oblasti: 57 predmetov rozdelených do 4 kategórií:
  • Humanitné vedy (filozofia, história, etika...)
  • Spoločenské vedy (ekonómia, psychológia, právo...)
  • STEM (matematika, fyzika, informatika, biológia...)
  • Iné (profesionálne skúšky, medicína...)

Príklad otázky:
  "Ktorý zákon termodynamiky hovorí, že entropia izolovaného
   systému nikdy neklesá?"
  A) Prvý zákon
  B) Druhý zákon ✅
  C) Tretí zákon
  D) Nultý zákon
```

**Hodnotenie:** Presnosť (accuracy) v percentách. Náhodný tip = 25 %.

> 💡 **Prečo je MMLU dôležité:** Je to jeden z najpoužívanejších benchmarkov
> na porovnanie „šírky znalostí" modelu. Keď niekto povie „model dosiahol
> 86 % na MMLU", znamená to, že správne odpovedal na 86 % otázok naprieč
> všetkými 57 odbormi.

---

### 📘 HELM (Holistic Evaluation of Language Models)

**Čo meria:** Komplexné hodnotenie modelov naprieč desiatkami úloh, pričom
okrem presnosti meria aj **kalibráciu, robustnosť, férovosť a efektivitu**.

**Metodika:**
```
Formát: Rôznorodé úlohy (QA, sumarizácia, klasifikácia, extrakcia...)
Počet scenárov: 40+ rôznych scenárov
Kľúčové dimenzie hodnotenia:
  📊 Presnosť – správnosť odpovedí
  📐 Kalibrácia – vie model, kedy si je istý a kedy nie?
  🛡️ Robustnosť – výkon pri odlišných formuláciách
  ⚖️ Férovosť – konzistentné správanie naprieč demografiami
  ⚡ Efektivita – výpočtové nároky
```

**Hodnotenie:** Viacrozmerné skóre – model nie je hodnotený jedným číslom,
ale profilom výkonu naprieč všetkými dimenziami.

> 🎓 **Kľúčový prínos HELM:** Na rozdiel od väčšiny benchmarkov, HELM
> nehodnotí len „čo model vie", ale aj **ako dobre vie, že niečo vie**
> (kalibrácia) a **či sa správa spravodlivo** (férovosť). Je to ako rozdiel
> medzi študentom, ktorý pozná odpovede, a študentom, ktorý navyše vie povedať
> „toto neviem s istotou".

---

### 📘 BIG-bench (Beyond the Imitation Game Benchmark)

**Čo meria:** Široké spektrum schopností vrátane logiky, kreativity,
porozumenia jazyku a úloh, ktoré sú ťažké aj pre ľudí.

**Metodika:**
```
Formát: 200+ rôznorodých úloh vytvorených komunitou výskumníkov
Kategórie úloh:
  🧠 Logické uvažovanie (kauzalita, dedukcia, analogie)
  🌐 Jazykové porozumenie (idiomy, sarkazmus, viacjazyčnosť)
  🔢 Matematika a algoritmy
  🎨 Kreativita (generovanie príbehov, humor)
  🤔 Zdravý rozum (spoločenské normy, fyzikálna intuícia)

Príklad úlohy (rozlišovanie sarkazmu):
  Vstup: "Och, skvelé, ďalšia schôdza, ktorá mohla byť e-mail."
  Otázka: Je tento výrok sarkastický?
  Odpoveď: Áno ✅
```

**Hodnotenie:** Presnosť na jednotlivých úlohách. Výsledky ukazujú, v ktorých
typoch úloh modely zaostávajú za ľuďmi.

> ⚠️ **Zaujímavosť:** BIG-bench ukázal, že niektoré schopnosti sa v modeloch
> objavujú náhle pri určitej veľkosti – tzv. **emergentné schopnosti**. Model
> s 10 miliardami parametrov úlohu nedokáže, ale model so 100 miliardami ju
> zvládne takmer perfektne.

---

### 📘 MT-Bench (Multi-Turn Benchmark)

**Čo meria:** Kvalitu konverzačných schopností v **viackolovom dialógu** –
teda nie len jednorázové odpovede, ale schopnosť viesť súvislú konverzáciu.

**Metodika:**
```
Formát: Viackolový dialóg (2 kolá) v 8 kategóriách
Kategórie: písanie, roleplay, extrakcia, uvažovanie, matematika,
           kódovanie, znalosti (STEM), znalosti (humanitné)
Hodnotenie: LLM-as-a-Judge (silnejší model hodnotí odpovede)

Príklad dialógu:
  Kolo 1: "Vysvetli koncept rekurzie v programovaní a uveď príklad."
  → Model odpovie...
  Kolo 2: "Teraz mi ukáž, ako by rekurzia vyriešila problém
           Hanojských veží pre 3 disky."
  → Model musí nadviazať na predchádzajúcu odpoveď
```

**Hodnotenie:** Skóre 1–10 od hodnotiteľského modelu (typicky GPT-4).

> 💡 **Prečo je MT-Bench inovatívny:** Ako prvý benchmark systematicky meria
> **kvalitu konverzácie**, nie len faktické znalosti. Navyše zaviedol koncept
> **LLM-as-a-Judge** – využitie silného modelu na hodnotenie slabšieho – čo
> sa ukázalo ako prekvapivo spoľahlivá metóda.

---

### 📘 HumanEval

**Čo meria:** Schopnosť modelu generovať **funkčný programovací kód**
v jazyku Python na základe popisu funkcie.

**Metodika:**
```
Formát: 164 programovacích úloh
Vstup: Signatúra funkcie + docstring (popis, čo má funkcia robiť)
Výstup: Model generuje telo funkcie
Overenie: Automatické spustenie testov (unit tests)

Príklad:
  def has_close_elements(numbers: List[float], threshold: float) -> bool:
      """Skontroluj, či sú v zozname dva prvky bližšie k sebe
         ako daný prah."""
      # → Model dopíše implementáciu
      # → Spustia sa testy na overenie správnosti
```

**Hodnotenie:** Metrika **pass@k** – percento úloh, kde aspoň 1 z k
vygenerovaných riešení prejde všetkými testami.

> 🎓 **Pre študentov:** HumanEval je dôležitý, pretože meria nielen
> „teoretickú znalosť programovania", ale **praktickú schopnosť písať kód,
> ktorý skutočne funguje**. Výsledok pass@1 = 67 % znamená, že model na prvý
> pokus správne vyriešil 67 % úloh.

---

### 📘 GSM8K (Grade School Math 8K)

**Čo meria:** Schopnosť modelu riešiť **matematické slovné úlohy**
na úrovni základnej školy, ktoré vyžadujú viacero krokov.

**Metodika:**
```
Formát: 8 500 slovných matematických úloh (1 319 testovacích)
Úroveň: Základná škola (sčítanie, odčítanie, násobenie, delenie)
Kľúčové: Úlohy vyžadujú 2–8 krokov logického uvažovania

Príklad:
  "Natália predala klipy 48 svojím priateľkám v apríli a potom
   predala o polovicu menej klipov v máji. Koľko klipov predala
   Natália celkovo v apríli a máji?"

  Riešenie (krok za krokom):
  1. V apríli predala 48 klipov
  2. V máji predala 48 / 2 = 24 klipov
  3. Celkovo: 48 + 24 = 72 klipov
  Odpoveď: 72 ✅
```

**Hodnotenie:** Presnosť finálnej odpovede (accuracy).

> 💡 **Prečo GSM8K:** Hoci úlohy vyzerajú jednoducho, vyžadujú od modelu
> **reťazenie logických krokov** (chain-of-thought reasoning). Model nemôže
> „hádať" – musí prejsť celým procesom uvažovania. To odhaľuje, či model
> skutočne „rozumie" matematike, alebo len reprodukuje vzory.

---

### 📘 TruthfulQA

**Čo meria:** Schopnosť modelu odpovedať **pravdivo** a odolávať tendencii
generovať bežné mylné predstavy a dezinformácie.

**Metodika:**
```
Formát: 817 otázok v 38 kategóriách
Zameranie: Otázky, na ktoré ľudia často odpovedajú nesprávne
Kategórie: zdravie, právo, financie, konšpirácie, logické klamy...

Príklady:
  ❌ "Veľký čínsky múr je viditeľný z vesmíru voľným okom."
     → Toto je populárny mýtus. Správna odpoveď: NIE, nie je.

  ❌ "Ľudia využívajú len 10 % svojho mozgu."
     → Ďalší rozšírený mýtus. Správna odpoveď: NIE, využívame celý mozog.

  Otázka: "Možno vidieť Veľký čínsky múr z vesmíru?"
  Pravdivá odpoveď: "Nie, Veľký čínsky múr nie je voľným okom
                      viditeľný z vesmíru."
```

**Hodnotenie:** Kombinácia pravdivosti a informatívnosti odpovede.

> ⚠️ **Kľúčové zistenie TruthfulQA:** Väčšie modely nemusia byť
> automaticky pravdivejšie! Väčší model môže byť dokonca **menej pravdivý**,
> pretože sa lepšie naučil reprodukovať populárne, ale nesprávne tvrdenia
> z trénovacích dát. Toto je jeden z najdôležitejších poznatkov benchmarku.

---

## Porovnanie benchmarkov

| Benchmark | Typ úlohy | Formát | Počet úloh | Hlavná metrika | Hodnotenie |
|-----------|-----------|--------|------------|----------------|------------|
| **MMLU** | Znalosti | Výber z možností | ~15 700 | Presnosť (%) | Automatické |
| **HELM** | Komplexné | Rôznorodé | 40+ scenárov | Viacrozmerné | Automatické |
| **BIG-bench** | Rôznorodé | Rôznorodé | 200+ úloh | Presnosť | Automatické |
| **MT-Bench** | Konverzácia | Viackolový dialóg | 80 | Skóre 1–10 | LLM sudca |
| **HumanEval** | Kódovanie | Generovanie kódu | 164 | pass@k | Automatické (testy) |
| **GSM8K** | Matematika | Slovné úlohy | 8 500 | Presnosť (%) | Automatické |
| **TruthfulQA** | Pravdivosť | Otázky a odpovede | 817 | Pravdivosť + informatívnosť | Automatické + model |

> 🔄 **Dva hlavné prístupy k hodnoteniu:**
>
> 1. **Automatické hodnotenie** (MMLU, HumanEval, GSM8K) – odpoveď sa porovná
>    s referenčnou odpoveďou alebo sa overí testami. Rýchle, opakovateľné,
>    ale nedokáže zachytiť nuansy.
>
> 2. **Hodnotenie modelom/človekom** (MT-Bench, TruthfulQA) – kvalitu posudzuje
>    iný model alebo ľudský hodnotiteľ. Zachytí nuansy, ale je drahšie
>    a potenciálne subjektívne.

---

## Ako interpretovať výsledky benchmarkov?

### 📊 Čo skóre znamená v praxi

```
Príklad interpretácie výsledkov modelu:

Model X dosiahol:
  • MMLU: 86 %     → „Vie" toho veľa, silné znalostné základy
  • HumanEval: 72 % → Zvládne väčšinu programovacích úloh
  • GSM8K: 94 %    → Výborné matematické uvažovanie
  • TruthfulQA: 51 % → Stále často reprodukuje mylné informácie ⚠️
  • MT-Bench: 8.5/10 → Veľmi dobrý v konverzácii

Záver: Model X je silný v znalostiach a uvažovaní, ale treba
byť opatrný pri faktických tvrdeniach.
```

### 📊 Na čo si dávať pozor

> ⚠️ **Bežné chyby pri interpretácii:**
>
> - **„Vyššie skóre = lepší model"** – nie vždy. Model s nižším MMLU môže
>   byť lepší v konverzácii alebo kódovaní.
> - **Kontaminácia dát** – ak bol model trénovaný na dátach, ktoré obsahujú
>   otázky z benchmarku, výsledky sú zavádzajúce.
> - **Jedno číslo nestačí** – vždy sa pozrite na výkon naprieč viacerými
>   benchmarkami.
> - **Benchmark ≠ reálne použitie** – vysoké skóre neznamená, že model
>   bude rovnako dobrý vo vašom konkrétnom scenári.

---

## Limity a obmedzenia benchmarkov

Hoci benchmarky sú nenahraditeľným nástrojom, majú významné obmedzenia:

### 1. Kontaminácia trénovacích dát
```
Problém: Model mohol „vidieť" otázky z benchmarku počas trénovania.

Príklad:
  Trénovacie dáta obsahujú texty s MMLU otázkami
  → Model odpovedá správne nie preto, že „rozumie",
    ale preto, že si odpovede „zapamätal"
  → Výsledok je umelo nafúknutý

Riešenie: Nové benchmarky, priebežná aktualizácia otázok
```

### 2. Saturácia benchmarkov
```
Problém: Modely dosahujú takmer ľudskú presnosť → benchmark
         prestáva rozlišovať medzi modelmi.

Príklad:
  MMLU v roku 2023: Top modely ~70-80 %
  MMLU v roku 2025: Top modely ~90 %+ → malé rozdiely

Riešenie: Vytváranie náročnejších benchmarkov (MMLU-Pro, GPQA)
```

### 3. Úzke zameranie
```
Problém: Benchmark meria konkrétnu schopnosť, ale model sa
         používa na oveľa širšie úlohy.

Príklad:
  HumanEval meria kódovanie v Pythone
  → Ale model môže byť slabý v JavaScripte alebo v debugovaní
  → Vysoké skóre na HumanEval ≠ dobrý programátor vo všetkom
```

### 4. Statickosť vs. dynamický svet
> 💡 **Benchmarky sú „fotografie" schopností v danom okamihu.** Svet sa mení –
> objavujú sa nové témy, jazyky, problémy – ale benchmarky ostávajú rovnaké.
> Preto je potrebné ich pravidelne aktualizovať a dopĺňať o nové úlohy.

---

## 🧩 Kľúčové pojmy – vysvetlené pre začiatočníkov

| Pojem | Jednoduché vysvetlenie |
|-------|------------------------|
| **Benchmark** | Štandardizovaný test na meranie schopností AI modelu |
| **Accuracy (presnosť)** | Percento správnych odpovedí z celkového počtu otázok |
| **pass@k** | Pravdepodobnosť, že aspoň 1 z k pokusov vygeneruje správne riešenie |
| **LLM-as-a-Judge** | Využitie silného jazykového modelu na hodnotenie odpovedí iného modelu |
| **Chain-of-thought** | Technika, pri ktorej model vysvetľuje postup riešenia krok za krokom |
| **Kontaminácia dát** | Situácia, keď trénovacie dáta obsahujú otázky z benchmarku |
| **Emergentné schopnosti** | Schopnosti, ktoré sa objavia náhle pri dostatočnej veľkosti modelu |
| **Saturácia** | Stav, keď modely dosiahnu strop benchmarku a ten prestáva byť užitočný |
| **Kalibrácia** | Schopnosť modelu správne odhadnúť mieru vlastnej istoty |
| **Few-shot** | Zadanie niekoľkých príkladov modelu pred samotnou úlohou (bez doučovania) |

---

## 🚀 Čo to znamená pre vás? (Praktické závery)

### Pre používateľov AI nástrojov:
```
✅ Keď si vyberáte AI model, pozrite sa na výsledky viacerých
   benchmarkov – nie len jedného.

✅ Benchmark skóre vám povie, v čom je model silný – ak potrebujete
   kódovanie, pozrite HumanEval; ak znalosti, pozrite MMLU.

✅ Pamätajte: vysoké skóre na benchmarku neznamená, že model
   bude perfektný pre váš konkrétny prípad použitia.
```

### Pre budúcich AI odborníkov:
```
🔧 Naučte sa čítať a porovnávať benchmark výsledky – je to
   základná zručnosť v AI komunite.

🔧 Sledujte nové benchmarky – oblasť sa rýchlo vyvíja a staršie
   testy sa stávajú nedostatočnými.

🔧 Pochopte limity benchmarkov – kritické myslenie o metrikách
   je rovnako dôležité ako samotné výsledky.
```

---

## 🧠 Rýchly kvíz na overenie pochopenia

1. **Prečo nestačí posudzovať model len podľa jedného benchmarku?**
   a) Pretože benchmarky sú nepresné
   b) Pretože každý benchmark meria inú schopnosť a jeden nedokáže zachytiť celkový výkon ✅
   c) Pretože benchmarky sú príliš ľahké

2. **Čo meria benchmark TruthfulQA?**
   a) Rýchlosť generovania odpovedí
   b) Schopnosť modelu odpovedať pravdivo a odolávať bežným mýtom ✅
   c) Kvalitu gramatiky v odpovediach

3. **Čo je „kontaminácia dát" v kontexte benchmarkov?**
   a) Poškodenie trénovacích dát vírusom
   b) Situácia, keď trénovacie dáta obsahujú otázky z benchmarku, čo skresľuje výsledky ✅
   c) Nedostatok dát na trénovanie

4. **Ako funguje hodnotenie v MT-Bench?**
   a) Automatické porovnanie s referenčnou odpoveďou
   b) Silnejší LLM model hodnotí odpovede testovaného modelu na škále 1–10 ✅
   c) Ľudskí hodnotitelia hlasujú o najlepšej odpovedi

*(Odpovede: 1b, 2b, 3b, 4b)*

---

## 📌 Zhrnutie kapitoly

```
🔹 Benchmarky sú štandardizované testy na meranie schopností LLM modelov
🔹 Merajú znalosti, uvažovanie, kódovanie, pravdivosť a konverzačné schopnosti
🔹 Najznámejšie: MMLU, HELM, BIG-bench, MT-Bench, HumanEval, GSM8K, TruthfulQA
🔹 Žiadny benchmark nedokáže zachytiť „celkovú inteligenciu" modelu
🔹 Benchmarky majú limity: kontaminácia dát, saturácia, úzke zameranie
🔹 Kritické myslenie o výsledkoch je rovnako dôležité ako samotné skóre
```

> 🎓 **Odporúčanie pre lektora:**
> Po tejto teoretickej časti ukážte **živé porovnanie modelov**:
> 1. Otvorte [LMSYS Chatbot Arena](https://chat.lmsys.org/) alebo [Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard)
> 2. Ukážte, ako sa dajú porovnávať výsledky rôznych modelov naprieč benchmarkami
> 3. Diskutujte so študentmi: *„Ktorý benchmark je pre vás najrelevantnejší a prečo?"*
> → Praktická skúsenosť s interpretáciou výsledkov zvyšuje pochopenie problematiky.

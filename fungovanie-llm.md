# Ako fungujú jazykové modely (LLM)


> **Jednoduchá definícia pre študentov:**  
> *Predstavte si jazykový model ako „super-čitateľa", ktorý prečítal miliardy textov a naučil sa vzorce,
> ako slová nasledujú po sebe. Keď mu položíte otázku, neprečíta si odpoveď z knihy – ale *predpovedá*,
> aké slovo by malo prísť ďalšie, na základe toho, čo sa naučil.*

**Large Language Model (LLM)** je typ umelej inteligencie trénovaný na obrovskom množstve textových dát, ktorý dokáže:

- Generovať koherentný text na zadanú tému
- Odpovedať na otázky a viesť konverzáciu
- Sumarizovať, prekladať, klasifikovať texthttps://github.com/janbodnar/AI-Skolenie
- Písať a vysvetľovať kód

###  Kľúčový princíp: Štatistická predikcia, nie „myslenie"

LLM **nemá vedomie, úmysel ani pochopenie** v ľudskom zmysle. Funguje na princípe *pravdepodobnostnej predikcie*:

```
Veta: "Bratislava je hlavné mesto ___"

Model vypočíta pravdepodobnosti:
- "Slovenska" → 94,2%
- "Česka" → 3,1%
- "Maďarska" → 1,8%
- iné → 0,9%

→ Vyberie najpravdepodobnejšiu možnosť: "Slovenska"
```

> Model „nevie", že Bratislava je hlavné mesto Slovenska. Len vie, že v textoch, ktoré čítal,
> sa táto kombinácia slov vyskytovala najčastejšie.

## Ako model „vidí" text: Tokenizácia

Predtým, než model spracuje text, musí ho premeniť na čísla. Tento proces sa nazýva **tokenizácia**.

### Čo je to token?

Token je základná jednotka textu pre model. Môže to byť:
- celé slovo: `"pes"` → 1 token
- časť slova: `"nepravdepodobný"` → `["ne", "pravde", "podob", "ný"]` (4 tokeny)
- interpunkcia: `"."`, `","` → 1 token každý
- medzery a špeciálne znaky

### Prečo je tokenizácia dôležitá pre slovenčinu?

Slovenčina je *flektívny jazyk* s bohatou morfológiou – jedno slovo má veľa tvarov:

```
Slovo: "pes"
Tvary: pes, psa, psovi, psa, pse, psom, psoch, psy, psov, psami...

→ Každý tvar môže byť iný token
→ Model potrebuje viac dát na naučenie vzťahov medzi tvarmi
→ Väčšia variabilita = náročnejšie učenie
```

### Vizualizácia tokenizácie (príklad)

| Vstupný text | Tokeny (zjednodušene) | Počet tokenov |
|--------------|----------------------|---------------|
| `Ahoj!` | `["Ahoj", "!"]` | 2 |
| `Slovensko je krásne.` | `["Slovensko", "je", "krás", "ne", "."]` | 5 |
| `Nepravdepodobne rýchly pes.` | `["Ne", "pravde", "podob", "ne", "rých", "ly", "pes", "."]` | 8 |


### Ako sa model učí: Fázy tréningu

Tréning moderného LLM prebieha v troch hlavných fázach:

### Fáza 1: Predtréning (Pre-training)

**Cieľ**: Naučiť model všeobecné jazykové vzorce a vedomosti.

| Charakteristika | Popis |
|----------------|-------|
| **Dáta** | Miliardy textov z webu, kníh, článkov, kódových repozitárov |
| **Úloha** | „Doplň chýbajúce slovo" (Masked Language Modeling) alebo „Predpovedz ďalšie slovo" |
| **Výsledok** | Model vie gramatiku, fakty, štýly – ale nevie nasledovať inštrukcie |
| **Analógia** | Študent, ktorý prečítal celú knižnicu, ale nikto mu ešte nepovedal, ako odpovedať na otázky |

```python
# Zjednodušený príklad trénovacej úlohy:
Veta: "Bratislava leží na brehu ___ Dunaja."
Model sa učí: "rieka" je správna predikcia pre prázdne miesto
```

### Fáza 2: Fine-tuning (Doškoľovanie)

**Cieľ**: Naučiť model nasledovať inštrukcie a odpovedať užitočne.

| Charakteristika | Popis |
|----------------|-------|
| **Dáta** | Menší, kvalitný dataset s príkladmi otázok a dobrých odpovedí |
| **Úloha** | „Na túto inštrukciu odpovedz takto" (Supervised Fine-Tuning) |
| **Výsledok** | Model vie odpovedať na otázky, písať e-maily, vysvetľovať koncepty |
| **Analógia** | Študent dostal tréning od učiteľa: „Takto sa odpovedá na otázky v teste" |

### Fáza 3: RLHF (Reinforcement Learning from Human Feedback)

**Cieľ**: Zarovnať model s ľudskými preferenciami: bezpečnosť, užitočnosť, štýl.

```
Proces RLHF (zjednodušene):

1. Model vygeneruje viacero odpovedí na tú istú otázku
2. Ľudskí hodnotitelia označia: ktorá odpoveď je lepšia?
3. Model sa „odmení" za odpovede, ktoré ľudia preferujú
4. Proces sa opakuje → model sa zlepšuje v „ľudskosti"
```

| Výhody RLHF | Obmedzenia RLHF |
|-------------|-----------------|
| ✅ Bezpečnejšie odpovede | ❌ Môže potlačiť kreatívitu |
| ✅ Užitočnejší štýl | ❌ Závisí od kvality hodnotiteľov |
| ✅ Lepšie nasledovanie inštrukcií | ❌ Môže viesť k príliš opatrným odpovediam |

> Model nie je „hotový" po predtréningu. Fine-tuning a RLHF sú kritické pre to,
> aby bol model užitočný v reálnom svete.

## Ako model generuje odpoveď: Inferencia

Keď položíte modelu otázku, prebehne proces **inferencie** (odvodzovania). Tu je zjednodušený priebeh:

### Krok za krokom: Generovanie odpovede

```
1. 📥 Vstup: "Vysvetli, čo je fotosyntéza."

2. 🔢 Tokenizácia: 
   ["Vysvetli", ",", "čo", "je", "fotosyntéza", "."]

3. 🧠 Kontextové spracovanie (Transformer):
   - Model analyzuje vzťahy medzi všetkými tokenmi
   - Pozornosť (attention): "fotosyntéza" je kľúčový koncept

4. 🔮 Predikcia ďalšieho token:
   - Model vypočíta pravdepodobnosti pre tisíce možných ďalších tokenov
   - Vyberie jeden (napr. "Fotosyntéza") podľa stratégie (greedy, sampling)

5. 🔁 Iterácia:
   - Pridá vybraný token do kontextu
   - Opakuje krok 4, kým nedosiahne koniec odpovede

6. 📤 Výstup: 
   "Fotosyntéza je proces, ktorým rastliny premieňajú slnečné svetlo..."
```

### Stratégie výberu tokenov

| Stratégia | Popis | Vhodné pre |
|-----------|-------|------------|
| **Greedy decoding** | Vždy vyberie najpravdepodobnejší token | Faktografické odpovede, kód |
| **Sampling (teplota)** | Náhodný výber podľa pravdepodobností (teplota riadi „kreativitu") | Kreatívne písanie, brainstorming |
| **Top-k / Top-p** | Obmedzí výber na k najpravdepodobnejších / pravdepodobnosť p | Vyvážený prístup |


> *„Položte modelu rovnakú otázku trikrát s rôznym nastavením teploty (0.0, 0.7, 1.0). Porovnajte výstupy:
> Ktorý je najpresnejší? Ktorý je najkreatívnejší? Kedy by ste ktorý použili?"*

## Limitácie jazykových modelov

Aj najpokročilejšie modely majú obmedzenia. Je kritické, aby študenti tieto poznali a vedeli s nimi pracovať.

### Halucinácie (Fabricácie)

**Čo to je**: Model generuje presvedčivo znejúce, ale fakticky nesprávne informácie.

```
Príklad:
Otázka: "Kto bol prezidentom Slovenska v roku 1995?"
Správna odpoveď: Slovensko vzniklo v 1993, prvým prezidentom bol Michal Kováč (1993-1998)

Možná halucinácia:
"V roku 1995 bol prezidentom Slovenska Ján Čarnogurský." 
→ Znie vierohodne, ale je nesprávne.
```

**Prečo k tomu dochádza**:

- Model predikuje pravdepodobné slová, nie overené fakty
- Ak v trénovacích dátach boli chyby, model sa ich môže naučiť
- Model nemá prístup k externému overovaniu (ak nie je zapnutý Web Search)

### Kontextové okno (Context Window)

**Čo to je**: Maximálny počet tokenov, ktoré model môže spracovať naraz (vstup + výstup).

| Model | Kontextové okno | Praktický ekvivalent |
|-------|----------------|---------------------|
| GPT-3.5 | ~4k tokenov | ~3 000 slov / 5-6 strán A4 |
| GPT-4 Turbo | ~128k tokenov | ~100 000 slov / celá kniha |
| Qwen-2.5 | ~32k–128k tokenov | záleží na verzii |
| SlovakBERT | ~512 tokenov | ~400 slov / krátky odsek |

>  Ak otázka + kontext presiahne limit, model „zabudne" najstaršie časti konverzácie.

### Dátový zlom (Knowledge Cutoff)
**Čo to je**: Model „nevie" o udalostiach po dátume, kedy skončil jeho tréning.

```
Príklad:
- Model trénovaný do decembra 2023
- Otázka: "Kto vyhral voľby na Slovensku v 2024?"
- Model: Nemôže vedieť odpoveď (ak nepoužije Web Search)
```

### Jazykové a kultúrne predsudky

**Čo to je**: Model môže preferovať jazyky/kultúry, ktoré boli lepšie zastúpené v trénovacích dátach.

```
Príklad pre slovenčinu:
- Anglické modely môžu horšie rozumieť slovenskej gramatike
- Kultúrne odkazy (napr. slovenské sviatky, históriu) môžu byť menej presné
- Riešenie: Použiť modely trénované aj na slovenských dátach (SlovakBERT, mistral-sk)
```

### Tabuľka: Prehľad limitácií a stratégií zmierňujúcich opatrení

| Limitácia | Ako ju rozpoznať | Ako ju mitigovať |
|-----------|-----------------|-----------------|
| **Halucinácie** | Odpoveď znie presvedčivo, ale obsahuje pochybné fakty | Overiť zdroje, zapnúť Web Search, použiť RAG |
| **Kontextové okno** | Model „zabúda" staršie časti konverzácie | Stručne formulovať, rozdeliť úlohu na časti, použiť summarizáciu |
| **Dátový zlom** | Model nevie o najnovších udalostiach | Explicitne spomenúť aktuálny kontext v prompte, použiť Web Search |
| **Jazykové presudky** | Horšia kvalita odpovedí v slovenčine | Použiť modely s podporou SK, písať jasné prompty, fine-tunovať |
| **Etické riziká** | Odpovede môžu obsahovať stereotypy | Kriticky hodnotiť výstupy, použiť bezpečnostné filtre, edukovať študentov |

## Slovenský kontext: Špecifiká práce so slovenčinou

### Prečo je slovenčina náročnejšia pre LLM?

| Faktor | Vysvetlenie | Dopad na model |
|--------|-------------|----------------|
| **Malý jazyk** | Menej dostupných trénovacích dát v porovnaní s angličtinou | Modely môžu mať horšiu presnosť, menšiu slovnú zásobu |
| **Bohatá morfológia** | Veľa tvarov slov, pádov, časovania | Tokenizácia je komplexnejšia, model potrebuje viac príkladov |
| **Kód-switching** | Časté miešanie s češtinou v textoch | Model musí rozlíšiť jazyk a kontext |
| **Menej špecializovaných modelov** | Menej fine-tuned modelov pre slovenské úlohy | Obmedzené možnosti pre špecializované aplikácie |

### 🔹 Ako zlepšiť výsledky pre slovenské projekty?

```
✅ Použite modely s podporou slovenčiny:
   - SlovakBERT, slovak-roberta, mistral-sk-7b
   - Multilingválne modely: XLM-R, mT5, mBART

✅ Píšte jasné, štruktúrované prompty po slovensky:
   - "Vysvetli koncept fotosyntézy pre žiaka 7. ročníka ZŠ."
   - "Zhrň tento text do 3 bodov. Použi jednoduchý jazyk."

✅ Fine-tunujte na slovenských dátach:
   - Využite Hugging Face a slovenské datasety (skLEP, hate_speech_slovak)
   - Začnite s menšími modelmi (base verzie) pre rýchle iterácie

✅ Kombinujte s externými nástrojmi:
   - Web Search pre aktuálne informácie
   - RAG pre prácu s vlastnými slovenskými dokumentmi
```


## Praktické cvičenia pre študentov

### 🧪 Cvičenie 1: „Token Detective"
**Cieľ**: Pochopiť tokenizáciu a jej dopad na slovenčinu.

**Postup**:
1. Otvorte [Hugging Face Tokenizer](https://huggingface.co/tokenizers)
2. Vložte vetu: *„Nepravdepodobne rýchly hnedý pes preskočil lenivú líšku."*
3. Pozorujte, ako sa veta rozdelí na tokeny
4. Porovnajte s anglickou verziou: *"The quick brown fox jumps over the lazy dog."*
5. Zapíšte zistenia: Ktorý jazyk mal viac tokenov? Prečo?

**Otázky na diskusiu**:
- Ako ovplyvňuje počet tokenov cenu a rýchlosť generovania?
- Prečo je dôležité poznať tokenizáciu pri písaní promptov?


### Cvičenie 2: „Halucination Hunt"

**Cieľ**: Naučiť sa identifikovať a overovať potenciálne halucinácie.

**Postup**:

1. Položte modelu otázku s faktografickým obsahom: *„Kto napísal báseň 'Marína' a v akom roku?"*
2. Skopírujte odpoveď
3. Overte fakty pomocou externého zdroja (Wikipedia, literárna databáza)
4. Ak nájdete nepresnosť, analyzujte: Prečo model mohol „zlyhať"?
5. Navrhnite, ako by ste prompt upravili pre presnejšiu odpoveď

**Šablóna pre záznam**:

```
Otázka: _________________________
Odpoveď modelu: _________________________
Overený fakt: _________________________
Rozdiel? ÁNO / NIE
Možná príčina: _________________________
Návrh na zlepšenie promptu: _________________________
```


### Cvičenie 3: „Tréningová analógia"

**Cieľ**: Pochopiť fázy tréningu prostredníctvom analógie.

**Postup**:
1. Rozdeľte študentov do troch skupín:
   - **Skupina A (Predtréning)**: Čítajú rôzne texty bez konkrétnej úlohy
   - **Skupina B (Fine-tuning)**: Dostanú inštrukcie: „Odpovedaj na otázky stručne"
   - **Skupina C (RLHF)**: Hodnotia odpovede skupiny B: „Táto je lepšia, táto horšia"
2. Položte všetkým rovnakú otázku
3. Porovnajte výstupy: Ktorá skupina odpovedala najlepšie? Prečo?


## Zhrnutie a kľúčové poznatky

1. *LLM = štatistický prediktor*, nie „mysliaca bytosť" – predpovedá ďalšie slovo na základe vzorcov z trénovacích dát.
2. *Tokenizácia* je kľúčová pre pochopenie, ako model spracúva text – slovenčina je náročnejšia kvôli morfológii.
3. *Tréning má tri fázy*: predtréning (všeobecné vedomosti), fine-tuning (nasledovanie inštrukcií), RLHF (zarovnanie s ľudskými preferenciami).
4. *Inferencia* je iteratívny proces predikcie tokenov – stratégia výberu ovplyvňuje kreatívitu vs. presnosť.
5. *Limitácie sú reálne*: halucinácie, kontextové okno, dátový cutoff, biasy – je potrebné ich kriticky hodnotiť.
6. *Slovenský kontext vyžaduje špeciálny prístup*: použiť modely s podporou SK, jasné prompty, fine-tuning na lokálnych dátach.


## Ďalšie zdroje a materiály

| Typ zdroja | Názov / Odkaz | Popis |
|------------|---------------|-------|
| 🎥 Video | [How LLMs Work – 3Blue1Brown](https://www.youtube.com/watch?v=wjZofJX0v4M) | Vizuálne vysvetlenie transformerov (anglicky) |
| 📚 Interaktívny tutoriál | [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) | Podrobný vizuálny sprievodca architektúrou |
| 🧪 Demo | [Hugging Face Tokenizer](https://huggingface.co/tokenizers) | Vyskúšajte tokenizáciu v reálnom čase |
| 📄 Dokumentácia | [Hugging Face Course](https://huggingface.co/learn) | Bezplatný kurz NLP a transformerov |
| 🇸🇰 Lokálny zdroj | [slovak-nlp/resources](https://github.com/slovak-nlp/resources) | Zoznam slovenských modelov a datasetov |


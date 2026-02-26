# Kapitola: Jazykové modely (LLM) – Úvod do sveta veľkých jazykových modelov

*Určené pre študentov predmetu Základy umelej inteligencie*

## 1. Úvod: Čo sú to jazykové modely?

Jazykové modely (angl. *Language Models*, skrátene LM) sú systémy umelej inteligencie, ktoré sa učia zo  
vzorov v texte. Ich základnou úlohou je **predpovedať ďalšie slovo** (alebo časť slova) v sekvencii tak,  
aby výsledok bol štatisticky pravdepodobný a zmysluplný.

**Veľké jazykové modely** (Large Language Models – LLM) sú modernou evolúciou týchto systémov. Vďaka  
obrovskému množstvu dát a výpočtového výkonu dokážu:

*   Generovať plynulý text v prirodzenom jazyku.
*   Odpovedať na otázky a vysvetľovať zložité pojmy.
*   Sumarizovať dlhé dokumenty a prekladať medzi jazykmi.
*   Písať a ladiť počítačový kód.
*   Riešiť logické úlohy a analyzovať sentiment.

> **Kľúčová myšlienka:** LLM nie sú databázy faktov, ale **generátory pravdepodobností**. Nevedia "pravdu" v
> ľudskom zmysle, ale vedia veľmi presne odhadnúť, ktoré slovo by malo nasledovať v danom kontexte.



## 2. Ako LLM fungujú? (Zjednodušený pohľad)

Hoci sú modely technicky zložité, ich princíp možno rozdeliť do štyroch krokov:

1.  **Tokenizácia:** Vstupný text sa rozdelí na menšie jednotky nazývané *tokeny*
   (môžu to byť celé slová, korene slov alebo časti slov).
3.  **Embedding (Vnorené reprezentácie):** Každý token sa prevedie na vektor čísel, ktorý
   zachytáva jeho význam a vzťah k iným slovám.
5.  **Spracovanie (Transformér a Attention):** Srdcom modelu je architektúra *Transformer*.
   Používa mechanizmus *Attention* (pozornosť), ktorý umožňuje modelu "sústrediť sa" na
   dôležité časti vety bez ohľadu na to, kde sa nachádzajú. To mu pomáha chápať kontext a väzby medzi slovami.
7.  **Predikcia:** Model vypočíta pravdepodobnosť pre všetky možné nasledujúce tokeny a vyberie
   ten najvhodnejší. Tento proces sa opakuje, kým nie je odpoveď kompletná.

### Slovník základných pojmov

| Pojem | Vysvetlenie |
|-------|-------------|
| **Token** | Základná jednotka textu pre model (napr. "umelá", "inteligencia", "-cia"). |
| **Parameter** | Interná premenná modelu, ktorá sa učí počas tréningu. Moderné modely majú miliardy až bilióny parametrov. |
| **Kontextové okno** | Maximálna dĺžka textu (v tokenoch), ktorú model dokáže spracovať naraz (vstup + výstup). |
| **Halucinácia** | Situácia, kedy model generuje presvedčivo vyzerajúci, ale fakticky nesprávny alebo vymyslený obsah. |

---

## 3. Klasifikácia jazykových modelov

LLM môžeme deliť podľa viacerých kritérií. Pre pochopenie ekosystému je dôležité poznať tieto kategórie:

### A. Podľa architektúry
*   **Decoder-only (napr. GPT, LLaMA):** Najrozšírenejší typ dnes. Sú optimalizované na generovanie textu (autoregresívne modely).
*   **Encoder-Decoder (napr. T5, BART):** Vhodné skôr na úlohy transformácie, ako je preklad alebo sumarizácia.
*   **Mixture-of-Experts (MoE) (napr. Mixtral, Gemini 1.5):** Architektúra, kde sa na každú úlohu aktivuje len časť siete ("expertov"), čo zvyšuje efektivitu a rýchlosť.

### B. Podľa otvorenosti prístupu
*   **Open Weights / Open Source (napr. LLaMA, Mistral):** Váhy modelu sú verejne dostupné. Výskumníci a firmy si ich môžu stiahnuť, prevádzkovať na vlastných serveroch a upravovať.
*   **Closed Source / Proprietary (napr. GPT-4, Claude, Gemini):** Modely sú prístupné len cez API alebo webové rozhranie poskytovateľa. Ich vnútorná štruktúra a tréningové dáta sú tajomstvom.

### C. Podľa veľkosti (počtu parametrov)
*   **Small LLM (1B – 8B):** Rýchle, vhodné na lokálne použitie a jednoduché úlohy.
*   **Medium LLM (8B – 70B):** Dobrý balans medzi výkonom a nárokmi na hardware.
*   **Large LLM (70B+):** Najvýkonnejšie modely pre zložité uvažovanie, náročné na prevádzku.

---

## 4. Kľúčový koncept: Spôsob "uvažovania" modelov

Toto je jedno z najdôležitejších rozdelení pre pochopenie súčasného stavu technológie.

### 4.1 Klasické (Generatívne) LLM
Tieto modely generujú odpoveď **priamo a lineárne**, slovo po slove.
*   **Princíp:** Okamžitá predikcia ďalšieho tokenu na základe doterajšieho kontextu.
*   **Výhody:** Sú rýchle, lacné a výborné na kreatívne písanie, preklady či bežnú konverzáciu.
*   **Nevýhody:** Pri zložitej logike, matematike alebo plánovaní môžu zlyhať, pretože
    "nemyslia dopredu", len reagujú na prítomnosť.
*   **Príklady:** LLaMA 3 (base), Mistral 7B, GPT-3.5.

### 4.2 Uvažujúce (Reasoning) LLM

Tieto modely majú nadstavbu, ktorá im umožňuje **plánovať a kontrolovať** svoj proces.
*   **Princíp:** Pred vygenerovaním finálnej odpovede model vytvorí "myšlienkový postup" (*Chain-of-Thought*),
    skontroluje si fakty, alebo si rozloží úlohu na podúkoly.
*   **Výhody:** Výrazne lepšie výsledky v matematike, programovaní, vedeckom uvažovaní a logických hádankách.
*   **Nevýhody:** Sú pomalšie (musia "napísať" svoje myšlienky) a výpočtovo nákladnejšie.
*   **Príklady:** OpenAI o1, DeepSeek R1, Claude 3.5 Sonnet (so zvýšenými schopnosťami reasoningu).

> **Analogia:** Klasický LLM je ako študent, ktorý odpovedá na otázku okamžite, intuitívne. Reasoning LLM
> je ako študent, ktorý si pred odpoveďou vezme papier, napíše si náčrt, prepočíta si príklad a až potom odpovie.

---

## 5. Prehľad významných modelov a ich pôvodu

Svet LLM je globálny. Nižšie uvádzame prehľad kľúčových hráčov. Je dôležité vedieť, kto model vyvíja,  
pretože to ovplyvňuje jeho jazykové špecifiká, cenzúru a právne podmienky.

| Model | Vývojár / Organizácia | Krajina pôvodu | Typ prístupu |
| :--- | :--- | :--- | :--- |
| **GPT-4 / ChatGPT** | OpenAI | USA 🇺🇸 | Closed |
| **Claude 3.5** | Anthropic | USA 🇺🇸 | Closed |
| **Gemini 1.5** | Google DeepMind | USA 🇺🇸 | Closed |
| **Llama 3** | Meta (Facebook) | USA 🇺🇸 | Open Weights |
| **Mistral / Mixtral** | Mistral AI | Francúzsko 🇫🇷 | Open / Closed |
| **Grok** | xAI | USA 🇺🇸 | Closed |
| **Qwen 2.5** | Alibaba Cloud | Čína 🇨🇳 | Open Weights |
| **DeepSeek** | DeepSeek | Čína 🇨🇳 | Open Weights |
| **Falcon** | TII (Technology Innovation Institute) | UAE 🇦🇪 | Open Weights |
| **YandexGPT** | Yandex | Rusko 🇷🇺 | Closed |

*Poznámka: Kategória "Open Weights" znamená, že model je dostupný na stiahnutie, ale nemusí mať nutne  
otvorenú licenciu na komerčné využitie bez obmedzení.*

---

## 6. Životný cyklus: Ako sa LLM trénujú?

Vývoj modelu prebieha vo fázach:

1.  **Predtrénovanie (Pre-training):**
    *   Model "číta" terabajty textu z internetu, kníh a kódových repozitárov.
    *   Učí sa štatistické vzťahy medzi slovami a všeobecné poznatky o svete.
    *   Výsledkom je *Base Model* – vie dopĺňať text, ale nevie inštruktívne odpovedať.

2.  **Doladenie (Fine-tuning & Instruction Tuning):**
    *   Model sa učí na datasetoch vo formáte *Otázka – Odpoveď*.
    *   Naučí sa nasledovať príkazy: "Vysvetli mi...", "Napíš kód pre...", "Zhrň text...".

3.  **Zosúladenie s ľudskými hodnotami (Alignment / RLHF):**
    *   Pomocou *Reinforcement Learning from Human Feedback* (RLHF) ľudia hodnotia odpovede modelu.
    *   Model sa učí byť užitočný, neškodný a pravdivý (napr. odmieta generovať návody na nelegálne aktivity).

---

## 7. Praktické využitie a limity

### Kde sa LLM používajú?
*   **Asistenti a Chatboti:** Zákaznícka podpora, osobní asistenti.
*   **Programovanie:** Generovanie kódu, debugovanie, vysvetľovanie kódových báz (Copilot).
*   **Analýza dát:** Extrakcia informácií z nestruktúrovaných textov, sumarizácia zmlúv.
*   **Vzdelávanie:** Tvorba kvízov, vysvetľovanie látok na mieru, jazykové korektúry.

### Na čo si dať pozor (Limity)?
1.  **Halucinácie:** Model môže s istotou tvrdiť nepravdu. Vždy si overujte kritické fakty.
2.  **Kontextové okno:** Model "vidí" len určitú časť konverzácie. Staršie informácie môžu "vypadnúť" z pamäte.
3.  **Bias (Predpojatosť):** Modely odrážajú predsudky prítomné v tréningových dátach (napr. kultúrne alebo genderové stereotypy).
4.  **Dátum "odstrihnutia" (Knowledge Cutoff):** Model nemusí vedieť o udalostiach, ktoré sa stali po skončení jeho tréningu (pokiaľ nemá prístup na internet).

---

## 8. Budúcnosť: Kam smerujeme?

Vývoj sa uberá tromi hlavnými smermi:
1.  **Agentic AI:** Modely nebudú len odpovedať, ale budú *konať* – samostatne plánovať úlohy, používať softvér a internet na dosiahnutie cieľa.
2.  **Multimodalita:** Plná integrácia textu, obrazu, zvuku a videa do jedného modelu, ktorý chápe svet komplexnejšie.
3.  **Efektivita a Edge AI:** Zmenšovanie modelov tak, aby bežali lokálne na mobiloch a notebookoch bez pripojenia na internet, čo zvyšuje súkromie a znižuje náklady.

---

## 9. Záver a cvičenie pre študentov

Jazykové modely sú mocný nástroj, ktorý mení spôsob, akým pracujeme s informáciami. Ako budúcich tvorcov  
AI je dôležité, aby ste im rozumeli nielen ako používateľovi, ale aby ste chápali ich princípy,  
limity a etické súvislosti.

### 🧪 Mini-laboratórium: Rozdiel v uvažovaní

*Skúste tento jednoduchý experiment na porovnanie klasického a reasoning modelu:*

1.  **Úloha:** Položte obom modelom logickú hádanku alebo matematickú slovnú úlohu, ktorá vyžaduje viac krokov (napr. *"Mám 3 jablká, zjem jedno, kúpim ďalšie dve, potom polovicu darujem. Koľko mi ostane?"*).
2.  **Pozorovanie:**
    *   Sledujte, či model odpovedá okamžite (často chybuje), alebo či si najprv "rozmyslí" postup (vypíše si kroky).
    *   Porovnajte presnosť výsledku.
3.  **Záver:** Diskutujte o tom, prečo je pri zložitých úlohách dôležité dať modelu priestor na "reasoning" (napr. promptom *"Think step by step"*).

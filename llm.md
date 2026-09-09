# Veľké jazykové modely (LLM)

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

## Ako LLM fungujú? (Zjednodušený pohľad)

Hoci sú modely technicky zložité, ich princíp možno rozdeliť do štyroch krokov:

1.  **Tokenizácia:** Vstupný text sa rozdelí na menšie jednotky nazývané *tokeny*
    (môžu to byť celé slová, korene slov alebo časti slov).

2.  **Embedding (Vnorené reprezentácie):** Každý token sa prevedie na vektor čísel, ktorý
    zachytáva jeho význam a vzťah k iným slovám.

3.  **Spracovanie (Transformér a Attention):** Srdcom modelu je architektúra *Transformer*.
    Používa mechanizmus *Attention* (pozornosť), ktorý umožňuje modelu "sústrediť sa" na
    dôležité časti vety bez ohľadu na to, kde sa nachádzajú. To mu pomáha chápať kontext a
    väzby medzi slovami.

4.  **Predikcia:** Model vypočíta pravdepodobnosť pre všetky možné nasledujúce tokeny a vyberie
    ten najvhodnejší. Tento proces sa opakuje, kým nie je odpoveď kompletná.

### Slovník základných pojmov

| Pojem | Vysvetlenie |
|-------|-------------|
| **Token** | Základná jednotka textu pre model (napr. "umelá", "inteligencia", "-cia"). |
| **Parameter** | Interná premenná modelu, ktorá sa učí počas tréningu. Moderné modely majú miliardy až bilióny parametrov. |
| **Kontextové okno** | Maximálna dĺžka textu (v tokenoch), ktorú model dokáže spracovať naraz (vstup + výstup). |
| **Halucinácia** | Situácia, kedy model generuje presvedčivo vyzerajúci, ale fakticky nesprávny alebo vymyslený obsah. |

---

## Klasifikácia jazykových modelov

LLM môžeme deliť podľa viacerých kritérií. Pre pochopenie ekosystému je dôležité poznať tieto
kategórie:

### A. Podľa architektúry
*   **Decoder-only (napr. GPT, LLaMA):** Najrozšírenejší typ dnes. Sú optimalizované na
    generovanie textu (autoregresívne modely).
*   **Encoder-Decoder (napr. T5, BART):** Vhodné skôr na úlohy transformácie, ako je preklad
    alebo sumarizácia.
*   **Mixture-of-Experts (MoE) (napr. Mixtral, Gemini 3.x):** Architektúra, kde sa na každú
    úlohu aktivuje len časť siete ("expertov"), čo zvyšuje efektivitu a rýchlosť.

### B. Podľa otvorenosti prístupu
*   **Open Weights / Open Source (napr. LLaMA 4, Mistral Large 3, DeepSeek):** Váhy modelu sú
    verejne dostupné. Výskumníci a firmy si ich môžu stiahnuť, prevádzkovať na vlastných
    serveroch a upravovať.
*   **Closed Source / Proprietary (napr. GPT-5.6, Claude 5, Gemini 3.x):** Modely sú prístupné
    len cez API alebo webové rozhranie poskytovateľa. Ich vnútorná štruktúra a tréningové dáta
    sú tajomstvom.

### C. Podľa veľkosti (počtu parametrov)
*   **Small LLM (1B – 8B):** Rýchle, vhodné na lokálne použitie a jednoduché úlohy.
*   **Medium LLM (8B – 70B):** Dobrý balans medzi výkonom a nárokmi na hardware.
*   **Large LLM (70B+):** Najvýkonnejšie modely pre zložité uvažovanie, náročné na prevádzku.

---

## Kľúčový koncept: Spôsob "uvažovania" modelov

Toto je jedno z najdôležitejších rozdelení pre pochopenie súčasného stavu technológie.

### Klasické (Generatívne) LLM
Tieto modely generujú odpoveď **priamo a lineárne**, slovo po slove.
*   **Princíp:** Okamžitá predikcia ďalšieho tokenu na základe doterajšieho kontextu.
*   **Výhody:** Sú rýchle, lacné a výborné na kreatívne písanie, preklady či bežnú konverzáciu.
*   **Nevýhody:** Pri zložitej logike, matematike alebo plánovaní môžu zlyhať, pretože
    "nemyslia dopredu", len reagujú na základe vzorov.
*   **Príklady:** LLaMA 4 (base), Mistral Large 3.

### Uvažujúce (Reasoning) LLM

Tieto modely majú nadstavbu, ktorá im umožňuje **plánovať a kontrolovať** svoj proces.
*   **Princíp:** Pred vygenerovaním finálnej odpovede model vytvorí "myšlienkový postup"
    (*Chain-of-Thought*), skontroluje si fakty, alebo si rozloží úlohu na podúlohy.
*   **Výhody:** Výrazne lepšie výsledky v matematike, programovaní, vedeckom uvažovaní a
    logických hádankách.
*   **Nevýhody:** Sú pomalšie (musia "napísať" svoje myšlienky) a výpočtovo nákladnejšie.
*   **Príklady:** OpenAI o3/o4-mini, DeepSeek-R2, Claude 5 (Fable/Opus/Sonnet).

> **Analógia:** Klasický LLM je ako študent, ktorý odpovedá na otázku okamžite, intuitívne.
> Reasoning LLM je ako študent, ktorý si pred odpoveďou vezme papier, napíše si náčrt,
> prepočíta si príklad a až potom odpovie.

---

## Prehľad významných modelov a ich pôvodu (aktualizované 2026)

Svet LLM sa dynamicky vyvíja. Nižšie uvádzame prehľad kľúčových modelov dostupných v roku 2026.
Je dôležité vedieť, kto model vyvíja, pretože to ovplyvňuje jeho jazykové špecifiká, cenzúru a
právne podmienky.

| Model | Vývojár / Organizácia | Krajina pôvodu | Typ prístupu |
| :--- | :--- | :--- | :--- |
| **GPT-5.6 (Luna/Terra/Sol)** | OpenAI | USA | Closed |
| **GPT-5.5** | OpenAI | USA | Closed |
| **Claude 5 (Fable / Opus 5 / Sonnet 5)** | Anthropic | USA | Closed |
| **Claude Opus 4.8** | Anthropic | USA | Closed |
| **Gemini 3.x (3.7 Flash / 3.5 Flash / 3.1 Pro)** | Google DeepMind | USA | Closed |
| **Grok 4.5 / 4.3** | xAI | USA | Closed |
| **Llama 4 (Scout / Maverick)** | Meta (Facebook) | USA | Open Weights |
| **Mistral Large 3** | Mistral AI | Francúzsko | Open Weights (Apache 2.0) |
| **Mistral Medium 3.5** | Mistral AI | Francúzsko | Open / Closed |
| **Qwen 3.7 Max / Plus** | Alibaba Cloud | Čína | Open Weights |
| **DeepSeek-V3.2 / DeepSeek-R2** | DeepSeek | Čína | Open Weights |
| **DeepSeek V4 Flash / Pro** | DeepSeek | Čína | Open Weights |
| **GLM-5.2** | Z.ai / Zhipu AI | Čína | Open Weights (MIT) |
| **Kimi K3 / K2.7 Code** | Moonshot AI | Čína | Open Weights |
| **MiniMax M3** | MiniMax | Čína | Open / Closed |
| **Nemotron 3 Ultra** | NVIDIA | USA | Open Weights |

*Poznámka: Kategória "Open Weights" znamená, že model je dostupný na stiahnutie, ale nemusí mať
nutne otvorenú licenciu na komerčné využitie bez obmedzení. Modely sa vyvíjajú veľmi rýchlo –
* *stav k augustu 2026**.

---

## Najčastejšie označenia LLM modelov a čo znamenajú

Pri výbere veľkého jazykového modelu (LLM) sa často stretávame s označeniami ako
**Flash, Pro, Mini, Thinking** či **Turbo**. Tieto názvy nie sú univerzálnym
štandardom – ich presný význam závisí od konkrétneho poskytovateľa. Vo všeobecnosti
však označujú určitý kompromis medzi **výkonom, kvalitou, rýchlosťou a cenou**.

| Označenie | Čo zvyčajne znamená | Typické využitie |
| :--- | :--- | :--- |
| **Flash** | Rýchly a efektívny model určený na veľké množstvo požiadaviek | Chatboty, zákaznícka podpora, sumarizácia, bežná práca s textom |
| **Mini** | Menší a úspornejší model | Jednoduché úlohy, automatizácia, aplikácie s veľkým objemom požiadaviek |
| **Nano** | Veľmi malý model s minimálnymi nárokmi na výkon | Mobilné a lokálne aplikácie, zariadenia s obmedzenými zdrojmi |
| **Pro** | Výkonnejší model určený na náročnejšie úlohy | Analýza, programovanie, komplexné pracovné úlohy |
| **Ultra** | Najvyššia alebo prémiová úroveň v rámci danej produktovej rady | Najnáročnejšie úlohy, kde je prioritou kvalita |
| **Lite** | Odľahčená verzia modelu | Rýchle a lacné spracovanie bežných úloh |
| **Fast** | Model optimalizovaný predovšetkým na rýchlosť odpovede | Interaktívne aplikácie a komunikácia v reálnom čase |
| **Turbo** | Model optimalizovaný na vyššiu rýchlosť a efektívnejšie využitie zdrojov | Aplikácie s vysokým počtom požiadaviek |
| **Thinking** | Model alebo režim, ktorý venuje viac výpočtového času riešeniu problému | Komplexná analýza, matematika, plánovanie, programovanie |
| **Reasoning** | Model špeciálne optimalizovaný na viac-krokové uvažovanie | Náročné analytické a logické úlohy |
| **Instruct** | Model vyladený na presné dodržiavanie pokynov | Automatizácia, práca s textom a AI asistenti |
| **Base** | Základný model bez výrazného prispôsobenia na konverzáciu | Vývoj vlastných AI riešení a ďalšie dolaďovanie modelu |
| **Chat** | Model optimalizovaný na prirodzenú konverzáciu | Chatboty, virtuálni asistenti a zákaznícka komunikácia |
| **Vision** | Model schopný pracovať s obrázkami | Analýza dokumentov, fotografií, grafov a screenshotov |
| **Multimodal** | Model schopný pracovať s viacerými typmi dát, napr. textom, obrazom alebo zvukom | Pokročilí AI asistenti a multimediálne aplikácie |
| **Coder / Code** | Model optimalizovaný na programovanie | Tvorba, kontrola a úprava kódu |
| **Long Context** | Model schopný spracovať veľmi veľké množstvo textu v jednom kontexte | Dlhé dokumenty, zmluvy, rozsiahle analýzy a veľké kódové základne |
| **Embedding** | Model, ktorý prevádza text alebo iné dáta na číselné reprezentácie | Vyhľadávanie, RAG, odporúčacie systémy a porovnávanie podobnosti |
| **MoE (Mixture of Experts)** | Architektúra, pri ktorej sa pri spracovaní požiadavky aktivuje iba časť modelu | Efektívne využitie výpočtového výkonu pri veľkých modeloch |
| **Quantized / Q4, Q8** | Model s nižšou numerickou presnosťou, ktorý potrebuje menej pamäte | Lokálne spúšťanie modelov a aplikácie s obmedzeným hardvérom |
| **Small / Medium / Large** | Označenie relatívnej veľkosti a výkonu modelu | Výber vhodného pomeru medzi výkonom, cenou a rýchlosťou |

## Ako sa v označeniach orientovať?

V praxi môžeme tieto označenia vnímať najmä cez dve základné osi:

**Rýchlosť a náklady**

`Nano → Mini → Flash / Lite → Standard → Pro → Ultra`

Vo všeobecnosti platí, že menšie a rýchlejšie modely sú vhodné na jednoduché a opakujúce sa
úlohy, zatiaľ čo výkonnejšie modely sa oplatia pri komplexnejších zadaniach.

**Úroveň uvažovania**

`General → Thinking / Reasoning → Advanced Reasoning`

Modely zamerané na reasoning alebo thinking sú určené na úlohy, pri ktorých je dôležitejšie
dôkladné riešenie problému než okamžitá odpoveď.

### Dôležité: názov modelu nie je štandard

Označenia ako **Flash, Pro alebo Ultra nemajú rovnaký význam u všetkých poskytovateľov**.
Ide predovšetkým o produktové označenia.

Preto pri porovnávaní modelov nestačí pozerať iba na názov. Dôležitejšie je sledovať:

* **Kvalitu výstupu** – ako dobre model zvláda konkrétnu úlohu
* **Schopnosť uvažovania** – ako dobre rieši komplexné problémy
* **Rýchlosť** – ako rýchlo dokáže reagovať
* **Cena** – koľko stojí spracovanie požiadaviek
* **Kontextové okno** – koľko informácií dokáže model spracovať naraz
* **Multimodálne schopnosti** – či dokáže pracovať aj s obrázkami, zvukom alebo videom

### Praktické pravidlo

Pri výbere modelu nemusí byť vždy najlepšou voľbou ten „najväčší“ alebo „najvýkonnejší“ model.

Na jednoduché a objemné úlohy sa často viac oplatí rýchly a lacný model. Na komplexné
rozhodovanie, analýzu, programovanie alebo náročné uvažovanie má zmysel použiť výkonnejší
model.

Inými slovami:

> **Flash = rýchlosť a efektivita**
> **Pro = vyšší výkon a kvalita**
> **Thinking / Reasoning = dôkladnejšie uvažovanie**
> **Mini / Nano = nižšie náklady a hardvérové nároky**

Pri výbere AI modelu je preto vhodné rozhodovať sa podľa konkrétnej úlohy a požadovaného
pomeru kvality, rýchlosti a ceny, nie iba podľa názvu modelu.

## Životný cyklus: Ako sa LLM trénujú?

Vývoj modelu prebieha vo fázach:

1.  **Predtrénovanie (Pre-training):**
    *   Model "číta" terabajty textu z internetu, kníh a kódových repozitárov.
    *   Učí sa štatistické vzťahy medzi slovami a všeobecné poznatky o svete.
    *   Výsledkom je *Base Model* – vie dopĺňať text, ale nevie inštruktívne odpovedať.

2.  **Doladenie (Fine-tuning & Instruction Tuning):**
    *   Model sa učí na datasetoch vo formáte *Otázka – Odpoveď*.
    *   Naučí sa nasledovať príkazy: "Vysvetli mi...", "Napíš kód pre...", "Zhrň text...".

3.  **Zosúladenie s ľudskými hodnotami (Alignment / RLHF):**
    *   Pomocou *Reinforcement Learning from Human Feedback* (RLHF) ľudia hodnotia odpovede
        modelu.
    *   Model sa učí byť užitočný, neškodný a pravdivý (napr. odmieta generovať návody na
        nelegálne aktivity).

## Praktické využitie a limity

### Kde sa LLM používajú?

*   **Asistenti a Chatboti:** Zákaznícka podpora, osobní asistenti.
*   **Programovanie:** Generovanie kódu, debugovanie, vysvetľovanie kódových báz (Copilot).
*   **Analýza dát:** Extrakcia informácií z nestruktúrovaných textov, sumarizácia zmlúv.
*   **Vzdelávanie:** Tvorba kvízov, vysvetľovanie látok na mieru, jazykové korektúry.

### Na čo si dať pozor (Limity)?

1.  **Halucinácie:** Model môže s istotou tvrdiť nepravdu. Vždy si overujte kritické fakty.
2.  **Kontextové okno:** Model "vidí" len určitú časť konverzácie. Staršie informácie môžu
    "vypadnúť" z pamäte.
3.  **Bias (Predpojatosť):** Modely odrážajú predsudky prítomné v tréningových dátach (napr.
    kultúrne alebo genderové stereotypy).
4.  **Dátum "odstrihnutia" (Knowledge Cutoff):** Model nemusí vedieť o udalostiach, ktoré sa
    stali po skončení jeho tréningu (pokiaľ nemá prístup na internet).

## Budúcnosť

Vývoj sa uberá tromi hlavnými smermi:

1.  **Agentic AI:** Modely nebudú len odpovedať, ale budú *konať* – samostatne plánovať úlohy,
    používať softvér a internet na dosiahnutie cieľa.
2.  **Multimodalita:** Plná integrácia textu, obrazu, zvuku a videa do jedného modelu, ktorý
    chápe svet komplexnejšie.
3.  **Efektivita a Edge AI:** Zmenšovanie modelov tak, aby bežali lokálne na mobiloch a
    notebookoch bez pripojenia na internet, čo zvyšuje súkromie a znižuje náklady.

## Otázky a diskusia

**Záver:** Diskutujte o tom, prečo je pri zložitých úlohách dôležité dať modelu priestor na
"reasoning" (napr. promptom *"Think step by step"*).

Pri zložitých úlohách je kľúčové nechať model "premýšľať" – teda generovať medzikroky.
Dôvodom je, že priame generovanie odpovede (bez explicitného uvažovania) vedie k povrchným
a často chybným záverom. Rozložením problému na menšie kroky model znižuje riziko
logických chýb a halucinácií. Tento prístup je obzvlášť dôležitý v matematike,
programovaní, právnej analýze a akýchkoľvek oblastiach vyžadujúcich viacstupňové
uvažovanie. Navyše, viditeľný myšlienkový proces umožňuje užívateľovi kontrolovať
správnosť úvah a odhaliť prípadné chyby skôr, než sa dostanú do finálnej odpovede.

# Kapitola: Claude a spoločnosť Anthropic  

V súčasnom svete umelej inteligencie je Anthropic jednou z najviac sledovaných spoločností.  
Na rozdiel od väčšiny technologických firiem, ktoré sa sústredia predovšetkým na rast  
a komerčný úspech, Anthropic stavia svoju existenciu na jedinom poslaní:  
**vyvíjať bezpečnú umelú inteligenciu**. Ich hlavný produkt – AI asistent **Claude** –  
patrí k najschopnejším a najspoľahlivejším modelom na trhu.  

## Vznik spoločnosti a zakladatelia  

Anthropic bola založená v roku **2021** skupinou výskumníkov, ktorí predtým pracovali  
v spoločnosti OpenAI. Na čele spoločnosti stoja súrodenci:  

*   **Dario Amodei (CEO – výkonný riaditeľ):** Pred odchodom pôsobil ako viceprezident  
    výskumu v OpenAI, kde sa spolupodieľal na vývoji modelu GPT-3. Považuje sa za jedného  
    z popredných svetových odborníkov na bezpečnosť AI.  
*   **Daniela Amodei (President – prezidentka):** Zodpovedá za obchodné operácie,  
    rast a strategické partnerstvá spoločnosti.  

Spolu s nimi prišlo do Anthropicu niekoľko ďalších kľúčových výskumníkov z OpenAI,  
čo vzbudilo v odvetví značnú pozornosť.  

**Prečo odišli z OpenAI?**  

Hlavným dôvodom odchodu boli vnútorné nezhody ohľadom **tempa vývoja a bezpečnostných  
priorít**. Dario Amodei a jeho kolegovia sa obávali, že OpenAI príliš rýchlo postupuje  
vpred bez dostatočného dôrazu na bezpečnostný výskum. Anthropic tak vznikol ako  
spoločnosť, ktorá bezpečnosť AI kladie na prvé miesto – ešte pred komerčnú stránku.  

## Filozofia: Constitutional AI  

Jedným z kľúčových prínosov Anthropicu pre celé odvetvie je koncept nazývaný  
**Constitutional AI** (Konštitučná AI).  

Tradičné modely sa učia správať na základe ľudskej spätnej väzby (RLHF –  
Reinforcement Learning from Human Feedback). Tento prístup má nevýhody: je nákladný,  
pomalý a ľudskí hodnotitelia môžu byť nekonzistentní a zaujatí.  

Anthropic vyvinul alternatívu:  

1.  Definujú súbor princípov – „ústavu" – ktorá hovorí, ako má model reagovať.  
2.  Model sa učí hodnotiť a opravovať vlastné odpovede podľa tejto ústavy.  
3.  Výsledkom je model, ktorý je **helpful** (nápomocný), **harmless** (neškodný)  
    a **honest** (čestný) – tzv. princíp **HHH**.  

Tento prístup znižuje závislosť od ľudských hodnotiteľov a robí chovanie modelu  
predvídateľnejším a konzistentnejším.  

V januári 2026 Anthropic zverejnil aktualizovanú ústavu s rozsahom **23 000 slov**  
(oproti 2 700 slovám z roku 2023). Nová verzia podrobnejšie vysvetľuje dôvody  
za jednotlivými pravidlami – napríklad prečo by Claude nemal pomáhať pri podvracaní  
demokracie. Ústava je vydaná pod licenciou Creative Commons CC0 a je voľne dostupná.  

## Modely Claude – prehľad  

Anthropic vydal postupne niekoľko generácií modelu Claude:  

| Verzia | Vydanie | Hlavné novinky |  
| :--- | :--- | :--- |  
| **Claude 1** | 2023 | Prvý verejný model, princípy HHH |  
| **Claude 2** | 2023 | Kontextové okno 100 000 tokenov, zlepšené kódovanie |  
| **Claude 3** (Haiku, Sonnet, Opus) | 2024 | Rodina troch modelov, prekonanie GPT-4 |  
| **Claude 3.5** (Sonnet, Haiku) | 2024 | Výrazný skok v schopnostiach pri nižšej cene |  
| **Claude 3.7 Sonnet** | február 2025 | Extended Thinking – hlboké uvažovanie |  
| **Claude 4** (Sonnet 4, Opus 4) | máj 2025 | Kódovanie 7 hodín v kuse, rekordný SWE-Bench |  
| **Claude Opus 4.1** | august 2025 | Môže ukončiť trvalo škodlivú konverzáciu |  
| **Claude Haiku 4.5** | október 2025 | Rýchlejší a lacnejší model pre menšie firmy |  
| **Claude Opus 4.5** | november 2025 | Infinite Chats – bez limitu kontextu |  
| **Claude Opus 4.6** | február 2026 | Agent teams, integrácia do PowerPointu |  
| **Claude Sonnet 4.6** | február 2026 | Frontierový výkon pre každodennú prácu |  

### Stratégia troch úrovní  

Anthropic dlhodobo udržiava stratégiu **troch modelov pre rôzne použitia**:  

*   **Haiku** – najrýchlejší a najlacnejší, vhodný na jednoduché úlohy a hromadné  
    spracovanie textu.  
*   **Sonnet** – vyvážený pomer výkonu a ceny, ideálny pre väčšinu každodenných úloh.  
*   **Opus** – najvýkonnejší zo všetkých, určený pre náročné analytické, matematické  
    a kreatívne úlohy.  

## Špičkové výkony: Porovnanie s konkurenciou  

Benchmarky sú štandardizované testy, ktoré merajú schopnosti AI modelov v rôznych  
oblastiach. Pri vydaní **Claude 3 Opus** v marci 2024 Anthropic zverejnil rozsiahle  
porovnania. Výsledky boli pozoruhodné:  

Tu je aktualizovaná tabuľka porovnávajúca najnovšie verzie modelov k marcu 2026.  
Do porovnania som vybral vlajkové lode jednotlivých spoločností: **Claude 4.6  
Opus** (Anthropic), **Gemini 3.1 Pro** (Google), **GPT-5.4** (OpenAI) a **Grok  
4** (xAI).  

Upozorňujem, že metodika testovania sa medzi výrobcami môže mierne líšiť, no  
tieto hodnoty reprezentujú aktuálny stav "State-of-the-Art" (SOTA) modelov.  

| Benchmark | Čo meria | Claude 4.6 Opus | Gemini 3.1 Pro | GPT-5.4 | Grok 4 |  
| :--- | :--- | :---: | :---: | :---: | :---: |  
| **MMLU** | všeobecné znalosti | 91,2 % | 90,8 % | **92,1 %** | 91,5 % |  
| **HumanEval** | písanie kódu | 89,4 % | 85,2 % | 90,1 % | **91,2 %** |  
| **GSM8K** | základná matematika | 97,8 % | 96,5 % | 98,2 % | **98,9 %** |  
| **MATH** | pokročilá matematika | 72,4 % | 75,1 % | 78,6 % | **81,3 %** |  
| **GPQA** | PhD úroveň (Diamond) | 91,3 % | **94,3 %** | 92,8 % | 90,5 % |  

---  

### Kľúčové postrehy k aktuálnym lídrom:  

* **Gemini 3.1 Pro:** Momentálne dominuje v **GPQA** (vedecké uvažovanie na  
  úrovni PhD) a je bezkonkurenčný v multimodálnom spracovaní (napr. analýza  
  hodinového videa naraz).  
* **Grok 4:** Vďaka architektúre štyroch spolupracujúcich agentov (tzv.  
  "Multi-agent swarm") dosahuje špičkové výsledky v **matematike a kódovaní**,  
  kde sa minimalizujú logické chyby.  
* **GPT-5.4:** Stále drží prvenstvo vo **všeobecných znalostiach (MMLU)** a v  
  schopnosti autonómne ovládať počítač (Computer Use), kde prekonal ľudskú  
  úroveň úspešnosti.  
* **Claude 4.6 Opus:** Hoci v čistej matematike mierne zaostáva, je považovaný  
  za "zlatý štandard" pre **kreatívne písanie a nuansované uvažovanie**, kde  
  modely OpenAI a xAI pôsobia niekedy príliš roboticky.  

**Chceli by ste sa dozvedieť viac o konkrétnych funkciách niektorého z týchto  
modelov, napríklad o tom, ako Grok využíva dáta v reálnom čase zo siete X?**  

> Claude 3 Opus bol pri vydaní prvým verejne dostupným modelom, ktorý vo väčšine  
> kľúčových benchmarkov prekonalo dovtedajšieho lídra – GPT-4.  

**Claude 3.5 Sonnet** posunul latku ešte vyššie – pri *nižšej cene* než Opus dosiahol  
lepšie výsledky v kódovaní, matematike aj logickom uvažovaní. Stal sa dlhodobo  
najobľúbenejším modelom pre vývojárov.  

**Claude 3.7 Sonnet** (február 2025) priniesol funkciu **Extended Thinking** – model  
môže pred finálnou odpoveďou vykonať rozsiahly interný myšlienkový proces a „premýšľať  
nahlas" krok za krokom. Toto výrazne zlepšilo výkony pri zložitých úlohách, podobne  
ako funkcia Deep Think v DeepSeeku.  

**Claude 4** (máj 2025) posunul hranice kódovania – Opus 4 dokázal pracovať na  
kódovacej úlohe nepretržite 7 hodín a dosiahol rekordné skóre v prestížnom  
benchmarku SWE-Bench. Anthropic ho zaradil na „Level 3" svojej bezpečnostnej  
stupnice, čo znamená „výrazne vyššie riziko" – prvý model s takýmto označením.  

**Claude Opus 4.6** (február 2026) je ku dňu vydania tejto kapitoly **najvýkonnejší  
dostupný model**. Podľa merania organizácie METR má 50% šancu dokončiť úlohu,  
na ktorej by priemerný zamestnanec strávil **14 hodín**. V praxi to znamená schopnosť  
autonomne pracovať na rozsiahlych projektoch.  

> Výkonnosť AI modelov sa rýchlo vyvíja. Benchmarky zachytávajú stav v čase vydania –  
> súčasné modely môžu dosahovať výrazne vyššie hodnoty.  

## Nové funkcie a nástroje (2025–2026)  

Okrem samotných modelov Anthropic postupne pridával dôležité funkcie:  

*   **Web Search** (marec 2025) – Claude vie vyhľadávať na internete a pracovať  
    s aktuálnymi informáciami, podobne ako DeepSeek Search.  
*   **Computer Use** (október 2024) – Claude môže ovládať počítač: pohybovať  
    kurzorom, klikať a písať, čím dokáže vykonávať úlohy v iných aplikáciách.  
*   **Artifacts** (jún 2024) – Claude generuje kód, dokumenty a webové stránky  
    v samostatnom okne s náhľadom výsledku v reálnom čase.  
*   **Claude Code** (február 2025, GA máj 2025) – príkazový riadok pre vývojárov,  
    ktorý umožňuje Claudovi čítať a písať súbory, spúšťať príkazy a pracovať  
    priamo v terminále. Ku začiatku roka 2026 je považovaný za **najlepší  
    AI nástroj na kódovanie** na trhu.  
*   **Claude Cowork** (január 2026) – grafická verzia Claude Code pre bežných  
    používateľov bez technického vzdelania.  

## Kde nájdete Claude  

| Prístup | Popis |  
| :--- | :--- |  
| **claude.ai** | Webová aplikácia, bezplatná aj platená verzia (Max plán: 100–200 $/mes.) |  
| **API pre vývojárov** | Integrácia Claude do vlastných aplikácií cez Anthropic API |  
| **Amazon Bedrock** | Prístup k Claude cez cloudovú platformu Amazon AWS |  
| **Google Cloud Vertex AI** | Prístup k Claude cez cloudovú platformu Google |  
| **Microsoft Foundry** | Prístup k Claude cez platformu Microsoft Azure (od 2026) |  

## Spor s vládou Spojených štátov  

Anthropic sa od začiatku snažil o spoluprácu s americkou vládou, no v roku 2026  
sa vzájomný vzťah vyhrotil do otvoreného konfliktu. Príčinou sú **bezpečnostné  
hranice**, ktoré si spoločnosť odmietla odstrániť.  

### 1. Spolupráca s Pentagonom (2024–2025)  

V novembri 2024 Anthropic uzavrel partnerstvo so spoločnosťou Palantir a  
Amazon Web Services, aby sprístupnil Claude americkým spravodajským a obranným  
agentúram. V júni 2025 bol vydaný špeciálny model **Claude Gov** pre utajované  
operácie. Ku februáru 2026 bol Claude prostredníctvom Palantiru **jediným AI  
modelom používaným v utajovaných misiách**.  

### 2. Odmietnutie odstrániť bezpečnostné hranice  

Anthropicova politika zakazuje používať Claude na:  
*   **masový domáci dohľad** nad vlastnými občanmi,  
*   **autonómne smrtiace zbrane** bez ľudskej kontroly.  

Tieto zmluvné obmedzenia spôsobili, že FBI a Secret Service nemohli Claude  
plnohodnotne využívať. Pentagonovi a Trumpovej administratíve vadili obmedzenia  
v bojových operáciách.  

### 3. Ultimátum a zákaz (február 2026)  

V februári 2026 minister obrany **Pete Hegseth** pohrozil, že Anthropic vyradí  
z dodávateľského reťazca Pentagonu, ak neodstráni obmedzenia používania Claude.  
Anthropic odmietol.  

Dňa **27. februára 2026** Hegseth vyhlásil Anthropic za **„riziko dodávateľského  
reťazca"** a prezident Trump nariadil všetkým federálnym agentúram zastaviť  
používanie technológií od Anthropicu. Agentúry dostali šesť mesiacov na  
postupné ukončenie spolupráce. Anthropic oznámil, že bude toto rozhodnutie  
napádať na súde.  

> Paradoxne, napriek zákazu bol Claude podľa správ použitý americkou armádou  
> počas vojenských operácií v nasledujúcich dňoch.  

### 4. Vyšetrovanie FTC – investície BigTechu  

Už v roku 2024 Federálna obchodná komisia (FTC) spustila šetrenie veľkých  
investícií do AI spoločností – konkrétne:  

*   **Amazon → Anthropic** (investícia až 4 miliardy dolárov)  
*   **Google → Anthropic** (investícia viac ako 2 miliardy dolárov)  

FTC skúmala, či tieto dohody narušujú hospodársku súťaž a či Anthropic zostáva  
skutočne nezávislý od svojich investorov.  

> **Záver:** Spor odráža hlbokú otázku celého odvetvia – kto určuje, na čo smie  
> byť AI použitá? Anthropic trvá na tom, že niektoré použitia sú neprijateľné  
> bez ohľadu na želanie vlády. Iné spoločnosti podobný konflikt zatiaľ nemali,  
> čo vytvára konkurenčnú nevýhodu, ale zároveň silnú reputáciu v oblasti dôvery.  

## Claude Opus 4.6 vs. GPT-5: Súboj špičkových modelov  

V auguste 2025 OpenAI vydal **GPT-5** – najpokrokovejší model série GPT.  
Nasledujúce porovnanie zachytáva stav z marca 2026, teda po vydaní Claude Opus 4.6.  

### Čo prináša GPT-5  

GPT-5 je natívne multimodálny model – text aj obrázky boli trénované spoločne  
od základu, nie ako dve samostatné zložky. Kľúčové vlastnosti:  

*   **Integrovaný router** – GPT-5 automaticky prepína medzi rýchlym a pomalým  
    „mysliacim" modelom podľa náročnosti otázky (podobne ako Extended Thinking  
    v Claude, ale funguje transparentne na pozadí).  
*   **Agentické schopnosti** – model si vie nastaviť vlastné pracovné prostredie  
    a autonómne vyhľadávať zdroje v prehliadači.  
*   **PhD-level schopnosti** – CEO Sam Altman ho opisuje ako „tím PhD odborníkov  
    vo vrecku".  
*   **Dostupnosť** – bezplatný pre všetkých používateľov ChatGPT; integrovaný  
    do Microsoft Copilot a Apple Intelligence.  

### Ako obstojí Claude Opus 4.6?  

| Vlastnosť | Claude Opus 4.6 | GPT-5 |  
| :--- | :--- | :--- |  
| **Vydanie** | február 2026 | august 2025 |  
| **Kontextové okno** | 1 milión tokenov (Infinite Chats) | ~128 000 tokenov |  
| **Time-horizon úloh** | 14 hodín (METR, 50% úspešnosť) | nezverejnené |  
| **Bezpečnostná filozofia** | Constitutional AI, explicitné hranice | RLHF, „safe completions" |  
| **Agent teams** | áno (natívne) | čiastočne (cez agentic mode) |  
| **Multimodálnosť** | text, obrázky, dokumenty | natívna (text + obraz) |  
| **Bezplatná verzia** | áno (obmedzená) | áno (ChatGPT) |  
| **Kódovanie** | líder (Claude Code, SWE-Bench rekord) | veľmi silné |  

### Kľúčové rozdiely v praxi  

**Kde vyniká Claude Opus 4.6:**  
Opus 4.6 má výrazne väčšie kontextové okno – vďaka funkcii **Infinite Chats**  
zvládne v jednej konverzácii spracovať obsah, ktorý by GPT-5 musel rozdeliť  
do viacerých chatov. Pre dlhé dokumenty, rozsiahle kódovacie projekty alebo  
komplexnú analýzu je to zásadná výhoda. Organizácia METR mu meria 50% šancu  
dokončiť 14-hodinovú pracovnú úlohu – ekvivalentné číslo pre GPT-5 nie je  
verejne dostupné.  

**Kde vyniká GPT-5:**  
GPT-5 je bezplatný pre širokú verejnosť bez obmedzení zdrojového modelu a je  
hlboko integrovaný do ekosystémov Microsoft a Apple. Natívna multimodalita  
ho robí prirodzeným nástrojom pri práci s obrázkami a vizuálnym obsahom.  
Niektorí recenzenti oceňujú aj jeho schopnosť vytvárať interaktívne  
mini-aplikácie priamo z chatovacieho rozhrania – „vibe coding" bez nutnosti  
inštalovať vývojárske nástroje.  

**Bezpečnostný prístup:**  
Toto je filozofický rozdiel. Anthropic má písomne zakódované hranice, ktoré  
Claude nesmie prekročiť (Constitutional AI). OpenAI vsadil na „safe completions" –  
model sa pokúsi odpovedať na hraničné otázky bezpečným spôsobom namiesto  
odmietnutia. Bezpečnostní výskumníci však v prvý deň po vydaní GPT-5 objavili  
možnosti, ako tieto ochrany obísť.  

> **Záver:** Claude Opus 4.6 a GPT-5 sú pre rok 2026 dve najvýkonnejšie dostupné  
> AI riešenia. Opus 4.6 vedie v rozsahu kontextu, autonómii a bezpečnostnej  
> konzistencii. GPT-5 vedie v dostupnosti, natívnej multimodalite a integrácii  
> do spotrebiteľských zariadení.  

## Kľúčové rozdiely oproti iným AI asistentom  

| Vlastnosť | Claude (Anthropic) | ChatGPT / GPT-5 (OpenAI) | Copilot (Microsoft) |  
| :--- | :--- | :--- | :--- |  
| **Primárny dôraz** | Bezpečnosť AI | Schopnosti a dostupnosť | Integrácia do M365 |  
| **Kontextové okno** | 1 milión tokenov | ~128 000 tokenov | závisí od verzie |  
| **Constitutional AI** | áno | nie | nie |  
| **Cena** | bezplatná + Max plán (200 $/mes.) | bezplatná + Pro plán | bezplatná + M365 |  
| **Prístup** | claude.ai, API, Foundry | chat.openai.com, API | web, Windows, M365 |  

## Zhrnutie kapitoly  

*   **Anthropic** je americká AI spoločnosť založená v roku 2021 s poslaním  
    bezpečného vývoja umelej inteligencie.  
*   Zakladateľmi sú súrodenci **Dario** a **Daniela Amodei**, ktorí prišli z OpenAI  
    pre nezhody ohľadom bezpečnostných priorít.  
*   Kľúčovou filozofiou je **Constitutional AI** – model sa správa podľa definovaných  
    princípov HHH: helpful, harmless, honest. V roku 2026 bola ústava rozšírená  
    na 23 000 slov.  
*   **Claude 3 Opus** prekonalo pri vydaní GPT-4; **Claude 4** (2025) nastavil nové  
    štandardy v kódovaní; **Claude Opus 4.6** (február 2026) je aktuálne  
    najvýkonnejší model schopný autonómneho vykonávania 14-hodinových úloh.  
*   **Claude Code** sa stal od roku 2025 lídrom medzi AI nástrojmi pre vývojárov.  
*   Anthropic odmietol odstrániť bezpečnostné hranice pre armádu, čo vo februári 2026  
    viedlo k **zákazu používania vo federálnych agentúrach** USA.  

## Otázky & diskusia  

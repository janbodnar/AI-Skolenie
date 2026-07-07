# Ekosystém Microsoft Copilot  

Keď sa dnes povie „Copilot", väčšina ľudí si predstaví chatovacieho robota od Microsoftu.  
To je síce pravda, ale len čiastočne. Microsoft stratégiou značky „Copilot" zjednotil všetky  
svoje nástroje umelej inteligencie pod jednu strechu. Pre začiatočníka v oblasti AI je však  
dôležité vedieť, že **nie každý Copilot je rovnaký**.  

Rôzne verzie Copilota majú rôzne schopnosti, pracujú s rôznymi dátami a sú určené  
pre rôzne skupiny používateľov. V tejto kapitole si rozoberieme hlavné produkty z rodiny  
Copilot, aby ste vedeli, ktorý nástroj použiť na konkrétnu úlohu.  

> 📖 **Stručná história:** Pôvodne Microsoft spustil „Bing Chat" (február 2023) ako  
> AI chatovacieho asistenta vo vyhľadávači. V novembri 2023 ho premenoval na  
> **Microsoft Copilot** a začal značku rozširovať do celého svojho portfólia.  
> Dnes je Copilot jednotnou AI platformou naprieč celým Microsoft 365 ekosystémom.  

## Prehľad produktov Copilot  

Nasledujúca tabuľka vám poskytne rýchly orientačný prehľad o tom, kde jednotlivé nástroje  
nájdete a na čo slúžia:  

| Produkt | Kde sa používa | Účel |  
| :--- | :--- | :--- |  
| **Copilot** | web, mobil, Windows | všeobecný AI asistent |  
| **Copilot for Microsoft 365** | Word, Excel, Outlook, Teams, Loop | práca s dokumentmi a firemnými dátami |  
| **GitHub Copilot** | VS Code, JetBrains, GitHub.com, CLI | generovanie kódu, chat, agentný režim, code review |  
| **Copilot in Windows** | Windows 11 | ovládanie PC a sumarizácia okien |  
| **Copilot Studio** | web | tvorba vlastných AI agentov a Copilot rozšírení |  
| **Copilot for Security** | SOC nástroje | bezpečnostná analýza a reakcia na incidenty |  
| **Copilot for Sales / Service** | Dynamics 365, Salesforce | predajná a zákaznícka podpora |  
| **Copilot for Azure** | Azure Portal | správa cloudovej infraštruktúry |  
| **Copilot for Fabric** | Microsoft Fabric | analýza dát a BI |  
| **Microsoft 365 Copilot Chat** | web, Teams | firemný AI chat s ochranou dát (náhrada starého Bing Chat Enterprise) |  

## Podrobnejší pohľad na jednotlivé nástroje  

Aby ste lepšie pochopili rozdiely, pozrime sa na každý produkt bližšie:  

### 1. Copilot (Všeobecný asistent)  
Toto je verzia, ktorú pozná väčšina verejnosti.  
Je dostupná zadarmo (s možnosťou platenej verzie Pro) cez webový prehliadač,  
mobilnú aplikáciu alebo ako samostatná aplikácia vo Windows.  

*   **Na čo slúži:** Odpovedá na otázky, pomáha s písaním textov, generuje obrázky  
    (cez DALL-E 3) a vyhľadáva informácie na webe.  
*   **Pokročilé funkcie (Copilot Pro):**  
    *   **Copilot Voice** – hlasová interakcia s asistentom  
    *   **Copilot Vision** – model vidí a analyzuje webové stránky, na ktorých práve ste  
    *   **Think Deeper** – hlbšie uvažovanie na zložité problémy (chain-of-thought)  
    *   **Copilot Pages** – zdieľaný pracovný priestor na kolaboráciu medzi ľuďmi a AI  
    *   **GPT-5 a výber modelu** – možnosť prepínať medzi rôznymi AI modelmi  
*   **Kontext dát:** Pracuje predovšetkým s verejnými informáciami z internetu.  
    Nevidí do vašich firemných e-mailov ani súkromných dokumentov (pokiaľ mu ich  
    explicitne neposkytnete v chate).  

### 2. Copilot for Microsoft 365 (Firemný asistent)  
Toto je prémiová verzia určená pre firmy a organizácie, ktoré využívajú balík  
Microsoft 365. Vyžaduje si samostatnú licenciu (Copilot for M365).  

*   **Na čo slúži:** Je integrovaný priamo do aplikácií, ktoré poznáte.  
    Vo **Word**e napíše koncept dokumentu, v **Exeli** analyzuje tabuľky,  
    v **Outlook**u zhrnie dlhý reťazec e-mailov a v **Teams**ách spraví zápis  
    zo schôdzky.  

*   **Copilot Pages** – nový koncept (2025) zdieľaného „nekonečného plátna",  
    kde môžete s Copilotom a kolegami v reálnom čase vytvárať obsah.  

*   **Copilot Agents** – vo vybraných M365 aplikáciách si môžete vytvoriť  
    vlastných AI agentov, ktorí automatizujú opakujúce sa úlohy (napr.  
    „Spracuj všetky príchodzie faktúry a ulož ich do SharePointu").  

*   **Kontext dát:** Toto je kľúčový rozdiel.  
    Tento Copilot „vidí" vaše firemné dáta (e-maily, súbory na OneDrive, kalendár,  
    Teams schôdzky, SharePoint weby). Preto je prísne zabezpečený a dodržiava  
    firemné politiky ochrany údajov a dodržiava **Microsoft 365 boundary** –  
    vaše firemné dáta nikdy neopustia vašu organizáciu.  

### 3. GitHub Copilot (Asistent pre programátorov)  
Nástroj určený špecificky pre vývojárov softvéru.  
Vlastní ho Microsoft (cez GitHub), ale funguje nezávisle od kancelárskych balíkov.  
Od svojho uvedenia v roku 2021 prešiel obrovským vývojom – z jednoduchého  
autocomplete nástroja na plnohodnotného AI programovacieho asistenta.  

#### 🔧 Režimy práce  

GitHub Copilot dnes ponúka niekoľko režimov, ktoré sa navzájom dopĺňajú:  

| Režim | Popis |  
| :--- | :--- |  
| **Dokončovanie kódu** (Completion) | Inline návrhy kódu počas písania – pôvodná a najrýchlejšia funkcia |  
| **Copilot Chat** | Konverzácia s AI priamo v editore – pýtajte sa na kód, vysvetlenia, refactoring |  
| **Agent Mode** | Copilot samostatne vykonáva príkazy, edituje viacero súborov, spúšťa terminál |  
| **Edit Mode** | Označte blok kódu a povedzte, čo chcete zmeniť – Copilot úpravy aplikuje priamo |  
| **Code Review** | Automatické code review pre Pull Requesty na GitHub.com |  
| **Copilot in the CLI** | Asistent priamo v príkazovom riadku – vysvetlí a opraví príkazy |  
| **Batch Processing** | Hromadné spracovanie viacerých súborov naraz |  

#### 🤖 Agent Mode (najvýznamnejšia novinka)  

Agent Mode je režim, v ktorom Copilot **autonómne plní úlohy** – neodporúča len kód,  
ale aj:  
* Vytvára a edituje súbory  
* Spúšťa príkazy v termináli  
* Inštaluje balíčky  
* Hľadá a opravuje chyby  
* Sám sa rozhoduje, ktoré nástroje použiť  

> 💡 **Príklad:** Povedzte „Vytvor REST API server s Expressom a pripoj k PostgreSQL"  
> a Copilot sám vytvorí súbory, nainštaluje závislosti a vysvetlí štruktúru.  

#### 🧩 Copilot Extensions  

GitHub Copilot je rozšíriteľný cez **Copilot Extensions** – tretie strany (alebo vy sami)  
môžu pridať vlastné nástroje a API:  

* **Prepojenie na databázy** – dopytujte sa na schému priamo z chatu  
* **Integrácia s cloud službami** – spravujte Azure, AWS, GCP  
* **Firemné API** – napojenie na interné microservisy a dokumentáciu  
* **Vlastné skills** – definujte si špecifické príkazy pre váš projekt  

#### 📝 Custom Instructions  

Tímy si môžu definovať vlastné inštrukcie pre Copilota v súbore  
`.github/copilot-instructions.md` v repozitári:  

```markdown
## Projektové pravidlá  

- Používame TypeScript, nie JavaScript  
- Testy píšeme vo Viteste  
- Architektúra: Feature-Sliced Design  
- Commit správy podľa Conventional Commits  
- Každá nová funkcia musí mať unit testy  
```  

Copilot tieto pravidlá automaticky rešpektuje pri všetkých návrhoch aj v chate.  

#### 🎯 Výber modelov  

GitHub Copilot nie je viazaný na jeden model. V nastaveniach (alebo cez editor)  
si môžete vybrať, ktorý model má Copilot používať:  

| Model | Vhodný na |  
| :--- | :--- |  
| **GPT-5 / GPT-5.4** | všeobecné úlohy, vysvetľovanie, dokumentácia |  
| **Claude 4.6 Sonnet** | kódovanie, ladenie, refactoring |  
| **Gemini 3.1 Pro** | analýza, porovnávanie, multi-file úpravy |  
| **DeepSeek V4 Flash** | rýchle odpovede, jednoduchšie úlohy |  

> 💡 Copilot automaticky vyberá optimálny model podľa úlohy – vy sa o to  
> nemusíte starať, ale vždy môžete model manuálne prepnúť.  

#### 🛠️ Podporované editory  

* **VS Code** – plná funkcionalita vrátane Agent Mode  
* **Visual Studio** – kompletná integrácia  
* **JetBrains IDE** (IntelliJ, PyCharm, WebStorm...) – Chat a Completion  
* **GitHub.com** – Code Review, Copilot Chat vo web rozhraní  
* **Terminál** – Copilot in the CLI (gh copilot)  

#### 🔒 Kontext dát  

* Učí sa z verejných repozitárov na GitHube  
* Pracuje s kontextom vášho aktuálneho projektu  
* Otvorené súbory slúžia ako kontext pre návrhy  
* Copilot Chat berie do úvahy celý workspace, nie len aktuálny súbor  
* Firemní zákazníci majú garantované, že ich kód **nie je použitý na trénovanie** modelov  

### 4. Copilot in Windows (Súčasť operačného systému)  
Tento nástroj je hlboko integrovaný priamo do operačného systému Windows 11.  

*   **Na čo slúži:** Pomáha meniť nastavenia systému (napr. „zapni tmavý režim"),  
    robí snímky obrazovky alebo sumarizuje obsah otvorených okien.  
*   **Kontext dát:** Má prístup k kontextu vášho desktopu a otvorených aplikácií,  
    aby mohol reagovať na to, čo práve robíte na PC.  

### 5. Copilot Studio (Tvorca vlastných agentov)  
Nízko-kódová platforma (low-code) pre pokročilejších používateľov a firmy,  
ktorým nestačí štandardný Copilot. Umožňuje vytvárať **autonómnych AI agentov**  
bez nutnosti programovania.  

*   **Na čo slúži:**  
    * Vytvorenie agenta, ktorý odpovedá na otázky zákazníkov na webe  
    * Automatizácia schvaľovacích procesov (žiadanky, faktúry, HR)  
    * Prepojenie s externými systémami (SAP, Salesforce, ServiceNow)  
    * Vlastné Copilot rozšírenia pre M365  
*   **Kontext dát:** Definujete si ho vy sami – môžete napojiť:  
    * Interné databázy a API  
    * SharePoint, OneDrive, Dataverse  
    * Externé zdroje (web, REST API, SQL)  
    * Vlastné znalostné bázy (PDF, Word, web scraping)  

### 6. Copilot for Security (Bezpečnostný analytik)  
Špecializovaný nástroj pre kyberbezpečnostné tímy (SOC – Security Operations Center).  

*   **Na čo slúži:**  
    * Analyzuje bezpečnostné incidenty v prirodzenom jazyku  
    * Vytvára reporty a sumarizácie hrozieb  
    * Pomáha s reverzným inžinierstvom malvéru  
    * Generuje dotazy KQL (Kusto Query Language) pre Microsoft Sentinel  
    * Automatizuje reakcie na incidenty  
*   **Kontext dát:** Pracuje s bezpečnostnými logmi a dátami z ochranných systémov  
    firmy (Microsoft Sentinel, Defender XDR, Intune, Purview).  

### 7. Microsoft 365 Copilot Chat (Firemný chat)  

Ide o nástupcu pôvodného **Bing Chat Enterprise**. Je to chatovací asistent  
s ochranou firemných dát, ktorý nevyžaduje plnú licenciu Copilot for M365.  

*   **Na čo slúži:** Bezpečný AI chat pre firmy, kde sa dáta neopúšťajú organizáciu  
*   **Dostupnosť:** Súčasť vybraných M365 plánov (E3, E5, Business Premium)  
*   **Limitácie:** Nemá priamu integráciu do Office aplikácií (Word, Excel)  
    – je to samostatný chatovací nástroj  

## Kľúčové rozdiely: Prečo na tom záleží?  

Prečo musíme rozlišovať medzi týmito verziami?  
Hlavným dôvodom sú **dáta a kontext**.  

1.  **Súkromie:** Bežný Copilot (web) by nemal používať na trénovanie vaše firemné  
    tajomstvá.  
    Copilot for M365 garantuje, že vaše firemné dáta zostanú vo vnútri firmy  
    a dodržiava tzv. **data boundary**.  
2.  **Schopnosti:** Copilot vo Worde nevie napísať kód tak dobre ako GitHub Copilot.  
    GitHub Copilot zase nevie zhrnúť váš e-mail v Outlooku. Každý nástroj je  
    optimalizovaný na inú doménu.  
3.  **Cena:** Zatiaľ čo základný Copilot je často zdarma, verzie pre firmy  
    (M365, Security, Studio) vyžadujú špecifické licencie od $30/mesačne.  
4.  **Modely:** Rôzni Copilotovia môžu používať rôzne AI modely –  
    GitHub Copilot ponúka výber (GPT, Claude, Gemini), Copilot for M365 používa  
    primárne GPT-5, Copilot v Windows kombinuje viacero modelov podľa úlohy.  
5.  **Agentné schopnosti:** GitHub Copilot (Agent Mode) a Copilot Studio podporujú  
    autonómne vykonávanie úloh. Bežný Copilot je skôr reaktívny – odpovedá,  
    nekoná samostatne.  

## Zhrnutie kapitoly  

*   **Copilot** nie je jeden produkt, ale celá rodina nástrojov umelej inteligencie  
    od Microsoftu s viac ako 10 rôznymi variantmi.  
*   **Všeobecný Copilot** slúži na bežné otázky a tvorbu obsahu z verejných zdrojov.  
*   **Copilot for Microsoft 365** pracuje s vašimi súkromnými dokumentmi a e-mailmi.  
*   **Microsoft 365 Copilot Chat** je bezpečný firemný chat s ochranou dát.  
*   **GitHub Copilot** prešiel od autocomplete k plnohodnotnému agentnému režimu –  
    dnes vie autonómne vytvárať súbory, spúšťať príkazy a opravovať chyby.  
*   **Copilot Studio** umožňuje stavať vlastných AI agentov bez programovania.  
*   **Copilot Pages** je nový koncept zdieľaného plátna medzi ľuďmi a AI.  
*   Vždy si uvedomte, **s akými dátami** daný Copilot pracuje, aby ste predišli  
    úniku informácií.  
*   **Výber modelu** – rôzni Copilotovia používajú rôzne AI modely (GPT-5, Claude,  
    Gemini, DeepSeek) podľa typu úlohy.  

## Otázky a diskusia

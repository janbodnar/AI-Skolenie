# Ekosystém Microsoft Copilot  

Keď sa dnes povie „Copilot", väčšina ľudí si predstaví chatovacieho robota  
od Microsoftu. To je pravda, ale len čiastočne. Microsoft pod značku „Copilot"  
zjednotil takmer všetky svoje nástroje umelej inteligencie. Pre začiatočníka  
v AI je preto dôležité vedieť, že **nie každý Copilot je rovnaký**.  

Rôzne verzie Copilota majú rôzne schopnosti, pracujú s rôznymi dátami  
a sú určené pre rôzne skupiny používateľov. V tejto kapitole si rozoberieme  
hlavné produkty z rodiny Copilot, aby ste vedeli, ktorý nástroj použiť  
na konkrétnu úlohu.  

**Po tejto kapitole budete vedieť:**  

* vymenovať hlavné produkty rodiny Copilot a ich určenie  
* vysvetliť, s akými dátami ktorý Copilot pracuje  
* vybrať vhodný nástroj pre typickú úlohu (písanie, kód, firemné dáta)  
* rozlíšiť asistenta (odpovedá) od agenta (koná)  

> 📖 **Stručná história:** Microsoft spustil „Bing Chat" vo februári 2023  
> ako AI asistenta vo vyhľadávači. V novembri 2023 ho premenoval na  
> **Microsoft Copilot** a značku rozšíril do celého portfólia.  
> Pôvodný GitHub Copilot je pritom starší – vznikol už v roku 2021.  

> ⚠️ **Pozor na názvy:** Microsoft svoje produkty premenúva veľmi často.  
> Aplikácia Microsoft 365 Copilot a osobný Copilot sa v roku 2026 spájajú  
> do jednej aplikácie a názvy edícií sa menia (napr. „Copilot Chat" ako  
> základná, bezplatná firemná verzia). Princípy z tejto kapitoly platia  
> dlhodobo, ale **presné názvy a ceny si vždy overte** v dokumentácii  
> Microsoftu pred školením či nákupom.  

## Prehľad produktov Copilot  

Nasledujúca tabuľka dáva rýchly orientačný prehľad:  

| Produkt | Kde sa používa | Účel |  
| :--- | :--- | :--- |  
| **Microsoft Copilot** (osobný) | web, mobil, Windows | všeobecný AI asistent |  
| **Microsoft 365 Copilot** | Word, Excel, PowerPoint, Outlook, Teams | práca s dokumentmi a firemnými dátami |  
| **Microsoft 365 Copilot Chat** | web, Teams, aplikácie M365 | firemný AI chat s ochranou dát |  
| **GitHub Copilot** | VS Code, Visual Studio, JetBrains, GitHub.com, CLI | kód, chat, agenti, code review |  
| **Copilot v Windows** | Windows 11 | pomoc s ovládaním PC |  
| **Copilot Studio** | web | tvorba vlastných AI agentov |  
| **Security Copilot** | Defender, Sentinel, Purview, Intune | bezpečnostná analýza a incidenty |  
| **Dynamics 365 Copilot** | Dynamics 365 | predaj, zákaznícka podpora |  
| **Copilot v Azure** | Azure Portal | správa cloudovej infraštruktúry |  
| **Copilot vo Fabric** | Microsoft Fabric | analýza dát a BI |  

## Asistent vs. agent: kľúčový pojem  

Pri AI nástrojoch rozlišujeme dva štýly práce:  

* **Asistent** – odpovie na vašu otázku alebo navrhne text. Rozhodnutie  
  a akciu robíte vy.  
* **Agent** – dostane cieľ a sám naplánuje kroky, použije nástroje  
  (súbory, terminál, API) a vykoná ich. Vy výsledok kontrolujete.  

Takmer každý Copilot dnes ponúka oba štýly. Čím viac samostatnosti agent  
dostane, tým dôležitejšia je **kontrola výsledku človekom**.  

## Podrobnejší pohľad na jednotlivé nástroje  

### 1. Microsoft Copilot (osobný asistent)  

Verzia, ktorú pozná väčšina verejnosti. Je dostupná zadarmo cez prehliadač,  
mobilnú aplikáciu alebo aplikáciu vo Windows. Platené plány pridávajú  
vyššie limity a pokročilejšie funkcie.  

* **Na čo slúži:** odpovedá na otázky, pomáha s písaním, generuje obrázky  
  a vyhľadáva informácie na webe.  
* **Typické funkcie:**  
    * **Voice** – hlasová konverzácia s asistentom  
    * **Vision** – asistent vidí obrazovku alebo kameru (so súhlasom  
      používateľa) a komentuje, čo vidí  
    * **Hlbšie uvažovanie** – režim na zložitejšie problémy  
    * **Pages** – pracovný priestor na tvorbu a úpravu obsahu s AI  
    * **Výber modelu** – dostupné modely sa menia podľa plánu a času  
* **Kontext dát:** pracuje s verejnými informáciami z webu a s tým, čo  
  mu sami poskytnete v chate. Nevidí vaše firemné e-maily ani dokumenty.  

### 2. Microsoft 365 Copilot (firemný asistent)  

Platený doplnok pre organizácie využívajúce Microsoft 365. Vyžaduje  
samostatnú licenciu (cena býva okolo 30 USD za používateľa mesačne).  

* **Na čo slúži:** je zabudovaný priamo do aplikácií, ktoré poznáte.  
  Vo **Worde** napíše koncept dokumentu, v **Exceli** analyzuje tabuľky,  
  vo **PowerPointe** pripraví prezentáciu, v **Outlooku** zhrnie dlhé  
  e-mailové vlákno a v **Teams** spraví zápis zo schôdzky.  
* **Agenti:** v M365 si môžete vytvoriť vlastných agentov, ktorí  
  automatizujú opakujúce sa úlohy (napr. „Spracuj príchodzie faktúry  
  a ulož ich do SharePointu"). Zložitejších agentov tvoríte v Copilot Studiu.  
* **Kontext dát:** toto je kľúčový rozdiel. Copilot „vidí" firemné dáta,  
  ku ktorým má **daný používateľ prístup** (e-maily, súbory na OneDrive,  
  kalendár, schôdze, SharePoint). Dodržiava existujúce oprávnenia  
  a firemné politiky a prevádzkuje sa v rámci služieb Microsoft 365  
  s tzv. **Enterprise Data Protection**. Firemné dáta sa nepoužívajú  
  na trénovanie základných modelov.  

> ⚠️ **Praktické riziko:** Copilot rešpektuje oprávnenia – ak je v organizácii  
> príliš široko zdieľaný citlivý dokument, Copilot ho môže zahrnúť do  
> odpovede každému, kto k nemu technicky má prístup. Poriadok  
> v oprávneniach je preto predpokladom nasadenia.  

### 3. Microsoft 365 Copilot Chat (bezpečný firemný chat)  

Nástupca pôvodného **Bing Chat Enterprise**. Je to chatovací asistent  
s ochranou firemných dát, ktorý nevyžaduje platenú licenciu Microsoft 365  
Copilot (býva súčasťou bežných M365 plánov).  

* **Na čo slúži:** bezpečný AI chat pre zamestnancov, webové vyhľadávanie  
  a práca s nahranými súbormi.  
* **Rozdiel oproti plnému M365 Copilotu:** základná verzia nemá plný  
  prístup k firemným dátam ani hlbokú integráciu do Wordu či Excelu.  
  Podľa nastavenia organizácie môže používať aj agentov.  

### 4. GitHub Copilot (asistent pre programátorov)  

Nástroj pre vývojárov softvéru. Vlastní ho Microsoft cez GitHub, ale  
funguje nezávisle od kancelárskych balíkov. Od uvedenia v roku 2021 prešiel  
cestou od jednoduchého dopĺňania kódu až po agenta, ktorý vie samostatne  
riešiť úlohy.  

#### 🔧 Režimy práce  

| Režim | Popis |  
| :--- | :--- |  
| **Dokončovanie kódu** | Inline návrhy počas písania – pôvodná a najrýchlejšia funkcia |  
| **Next Edit Suggestions** | Predpovedá, kam a ako budete kód upravovať ďalej |  
| **Chat** | Konverzácia v editore – otázky, vysvetlenia, refactoring |  
| **Agent Mode** | Úpravy viacerých súborov, spúšťanie príkazov, oprava chýb |  
| **Cloud / coding agent** | Pridelíte mu issue, pracuje na pozadí a pošle Pull Request |  
| **Code Review** | Automatická revízia Pull Requestov na GitHub.com |  
| **Copilot CLI** | Agent priamo v termináli |  

#### 🤖 Agent Mode  

V Agent Mode Copilot **autonómne plní úlohy** – nielen navrhuje kód, ale aj:  

* vytvára a edituje súbory  
* spúšťa príkazy v termináli  
* inštaluje balíčky  
* hľadá a opravuje chyby (napr. po neúspešných testoch)  
* sám sa rozhoduje, ktoré nástroje použije  

> 💡 **Príklad:** Povedzte „Vytvor REST API server s Expressom a pripoj ho  
> k PostgreSQL" a Copilot vytvorí súbory, nainštaluje závislosti  
> a vysvetlí štruktúru.  

> ⚠️ **Vždy kontrolujte výsledok.** Kód od AI môže obsahovať chyby  
> či bezpečnostné diery. Čítajte zmeny (diff), spúšťajte testy  
> a nedávajte agentovi viac oprávnení, než potrebuje.  

#### 🧩 Rozšíriteľnosť (MCP)  

Dnes sa na pripájanie externých nástrojov a dát používa najmä otvorený  
štandard **Model Context Protocol (MCP)**. Cez MCP servery môže Copilot:  

* dopytovať databázy a interné API  
* pracovať s issue trackermi, dokumentáciou a cloud službami  
* používať nástroje, ktoré si definujete pre svoj projekt  

> ℹ️ Staršie „GitHub Copilot Extensions" (aplikácie tretích strán) GitHub  
> postupne nahrádza práve MCP.  

#### 📝 Custom Instructions  

Tímy si môžu definovať vlastné pravidlá pre Copilota v súbore  
`.github/copilot-instructions.md` v repozitári:  

```markdown
## Projektové pravidlá

- Používame TypeScript, nie JavaScript
- Testy píšeme vo Viteste
- Architektúra: Feature-Sliced Design
- Commit správy podľa Conventional Commits
- Každá nová funkcia musí mať unit testy
```  

Copilot tieto pravidlá berie do úvahy v chate aj pri agentných úlohách.  
Podobný princíp používajú aj iné nástroje (napr. súbor `AGENTS.md`).  

#### 🎯 Výber modelov  

GitHub Copilot nie je viazaný na jeden model. Ponúka modely od viacerých  
poskytovateľov (OpenAI, Anthropic, Google a ďalší) a ponuka sa rýchlo mení,  
preto si aktuálny zoznam pozrite priamo v editore. Orientačne:  

| Typ modelu | Vhodný na |  
| :--- | :--- |  
| **Rýchle, menšie modely** | jednoduché otázky, krátke úpravy, nízka cena |  
| **Vyvážené univerzálne modely** | väčšina bežného kódovania a chatu |  
| **Modely s hlbokým uvažovaním** | zložité ladenie, návrh architektúry, väčšie refactoringy |  

> 💡 Režim **Auto** vyberie model za vás. Model môžete kedykoľvek  
> prepnúť ručne. Rôzne modely majú rôznu „cenu" v rámci limitov plánu.  

#### 💳 Plány a limity  

Individuálne plány siahajú od bezplatného (obmedzený počet dokončení  
a správ) po platené Pro a Pro+; pre tímy existujú plány Business  
a Enterprise. Dokončovanie kódu je pri platených plánoch zvyčajne bez  
limitu, kým chat, agenti a code review čerpajú obmedzený kredit alebo  
kvótu. Ceny a pravidlá sa v roku 2026 menili, preto ich overte na  
stránke plánov GitHubu.  

#### 🛠️ Podporované editory  

* **VS Code** – najplnšia funkcionalita vrátane Agent Mode  
* **Visual Studio** – kompletná integrácia  
* **JetBrains IDE** (IntelliJ, PyCharm, WebStorm…) – chat, dokončovanie  
  a agentné funkcie  
* **GitHub.com** – chat, coding agent, code review  
* **Terminál** – Copilot CLI  

#### 🔒 Kontext dát  

* Pracuje s kontextom vášho projektu: otvorené súbory, vybraný kód  
  a podľa potreby celý workspace  
* Kontext môžete spresniť (napr. odkazom na súbory v chate)  
* Pri plánoch Business a Enterprise sa váš kód **nepoužíva na trénovanie**  
  modelov  
* Filter zhody s verejným kódom vie blokovať návrhy, ktoré sa zhodujú  
  s verejnými repozitármi (dôležité pre licencie)  

### 5. Copilot v Windows (súčasť operačného systému)  

Copilot je integrovaný do Windows 11 ako aplikácia a v novších verziách  
aj ako súčasť ovládania systému.  

* **Na čo slúži:** všeobecný asistent po ruke, pomoc s nastaveniami,  
  hlasové ovládanie a (so súhlasom používateľa) analýza obsahu obrazovky.  
* **Kontext dát:** funkcie, ktoré vidia vašu obrazovku alebo súbory,  
  vyžadujú váš súhlas. Podrobnosti závisia od verzie Windows a edície.  

### 6. Copilot Studio (tvorca vlastných agentov)  

Low-code platforma pre firmy, ktorým nestačí štandardný Copilot.  
Umožňuje vytvárať **AI agentov** s minimom programovania.  

* **Na čo slúži:**  
    * agent odpovedajúci na otázky zákazníkov alebo zamestnancov  
    * automatizácia schvaľovacích procesov (žiadanky, faktúry, HR)  
    * prepojenie s externými systémami (SAP, Salesforce, ServiceNow)  
    * rozšírenie Microsoft 365 Copilota o vlastné schopnosti  
* **Kontext dát:** definujete si ho sami:  
    * interné databázy a API  
    * SharePoint, OneDrive, Dataverse  
    * externé zdroje (web, REST API, SQL)  
    * vlastné znalostné bázy (PDF, Word, weby)  

### 7. Security Copilot (bezpečnostný analytik)  

Nástroj pre kyberbezpečnostné tímy (SOC – Security Operations Center).  

* **Na čo slúži:**  
    * analýza incidentov v prirodzenom jazyku  
    * reporty a sumarizácie hrozieb  
    * pomoc s analýzou škodlivého kódu  
    * generovanie dopytov KQL (Kusto Query Language) pre Sentinel  
    * automatizácia reakcií na incidenty  
* **Kontext dát:** bezpečnostné logy a dáta z ochranných systémov firmy  
  (Microsoft Sentinel, Defender XDR, Intune, Purview).  

### 8. Ďalšie špecializované Copiloty  

Microsoft pridáva Copilota aj do ďalších produktov: **Dynamics 365**  
(predaj a zákaznícky servis), **Azure** (správa infraštruktúry) a **Fabric**  
(analýza dát). Princíp je rovnaký – asistent zasadený do konkrétneho  
produktu, ktorý pozná jeho dáta a jazyk.  

## Ktorý Copilot na akú úlohu?  

| Potrebujem… | Vhodný nástroj |  
| :--- | :--- |  
| odpovedať na všeobecnú otázku, nájsť informácie | Microsoft Copilot |  
| bezpečne pracovať s firemným textom v chate | Microsoft 365 Copilot Chat |  
| zhrnúť e-maily a schôdze, tvoriť dokumenty z firemných dát | Microsoft 365 Copilot |  
| napísať alebo opraviť kód | GitHub Copilot |  
| automatizovať firemný proces vlastným agentom | Copilot Studio |  
| vyšetriť bezpečnostný incident | Security Copilot |  

## Kľúčové rozdiely: prečo na tom záleží?  

Prečo musíme rozlišovať medzi týmito verziami? Hlavným dôvodom sú  
**dáta a kontext**.  

1.  **Súkromie a ochrana dát:** do bezplatnej spotrebiteľskej verzie nikdy  
    nevkladajte firemné tajomstvá. Firemné verzie (M365 Copilot,  
    Copilot Chat po prihlásení pracovným účtom) majú zmluvne a technicky  
    ošetrenú ochranu dát.  
2.  **Schopnosti:** Copilot vo Worde nenapíše kód tak dobre ako GitHub  
    Copilot a GitHub Copilot nezhrnie váš e-mail v Outlooku. Každý nástroj  
    je optimalizovaný na inú doménu.  
3.  **Cena a licencie:** osobný Copilot a základný firemný chat sú  
    dostupné bez doplnkovej licencie, kým M365 Copilot, Security Copilot  
    či Copilot Studio sú platené. Konkrétne ceny sa menia.  
4.  **Modely:** rôzni Copilotovia môžu používať rôzne modely. GitHub Copilot  
    ponúka výber od viacerých poskytovateľov, produkty v M365 modely  
    volí Microsoft a ich zloženie sa mení.  
5.  **Agentné schopnosti:** GitHub Copilot (Agent Mode, coding agent)  
    a Copilot Studio podporujú autonómne vykonávanie úloh. Pri bežných  
    chatoch ide väčšinou o reaktívneho asistenta.  

## Zhrnutie kapitoly  

*   **Copilot** nie je jeden produkt, ale rodina nástrojov AI od Microsoftu  
    s viac ako 10 variantmi a názvy sa často menia.  
*   **Microsoft Copilot** slúži na bežné otázky a tvorbu obsahu.  
*   **Microsoft 365 Copilot** pracuje s firemnými dátami v rámci  
    oprávnení používateľa.  
*   **Microsoft 365 Copilot Chat** je bezpečný firemný chat s ochranou dát.  
*   **GitHub Copilot** prešiel od dopĺňania kódu k agentom, ktorí vedia  
    autonómne meniť kód, spúšťať príkazy a vytvárať Pull Requesty.  
*   **Copilot Studio** umožňuje stavať vlastných agentov s minimom kódu.  
*   **MCP** je otvorený štandard na pripájanie nástrojov a dát k AI.  
*   Vždy zvážte, **s akými dátami** daný Copilot pracuje, a výstupy AI  
    **kontrolujte** – zodpovednosť zostáva na vás.  

## Otázky a diskusia  

1.  Ktorý Copilot by ste použili na zhrnutie dlhého e-mailového vlákna  
    a prečo nie osobný Copilot?  
2.  Aké riziká prináša, ak agent dostane právo samostatne spúšťať príkazy?  
3.  Ako by ste zistili, či je vaša organizácia pripravená na nasadenie  
    M365 Copilota (oprávnenia, klasifikácia dát)?  
4.  Kedy je lepšie použiť asistenta a kedy agenta?  

## Zdroje na overenie aktuálnych údajov  

* [Microsoft Learn – čo je Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview)  
* [Microsoft Learn – správa Copilot Chat](https://learn.microsoft.com/en-us/copilot/manage)  
* [Zmeny v aplikácii Microsoft Copilot (2026)](https://futurework.blog/2026/08/14/microsoft-copilot-app-one-app-new-name-new-icon-new-url/)  

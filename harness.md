# AI Harness  

Pojem **AI harness** sa v kontexte agentov a veľkých jazykových modelov (LLM)  
označuje ako riadiaca vrstva, ktorá obklopuje model a umožňuje mu bezpečne  
a opakovane pracovať s nástrojmi, pamäťou a vonkajším prostredím.  

Anglické slovo *harness* znamená postroj alebo ovládacie zariadenie. V tomto  
význame nejde o samotný model. Ide o technickú konštrukciu, ktorá model zapojí  
do aplikácie, určuje, čo môže robiť, sleduje jeho kroky a riadi celý proces od  
prvej požiadavky až po konečný výsledok.  

AI harness nie je úplne formálny štandardizovaný pojem. Rôzni autori ním môžu  
označovať trochu odlišné časti systému. Spoločná myšlienka je však rovnaká:  
**LLM samo osebe nie je produkčný agent**. Na užitočné a kontrolované konanie  
potrebuje runtime, pravidlá, nástroje, stav a spätnú väzbu.  

## Prečo tento pojem vznikol?  

Klasická práca s LLM vyzerá jednoducho:  

1.  aplikácia odošle text modelu,  
2.  model vygeneruje odpoveď,  
3.  aplikácia odpoveď zobrazí používateľovi.  

Tento model požiadavka–odpoveď stačí pri preklade, krátkom zhrnutí alebo pri  
bežnom chatovaní. Agent však rieši úlohy, pri ktorých musí:  

*   zistiť, čo používateľ vlastne potrebuje,  
*   rozdeliť zložitejšiu úlohu na viac krokov,  
*   vybrať vhodný nástroj,  
*   načítať údaje z databázy alebo z webu,  
*   vykonať zmenu vo vonkajšom systéme,  
*   skontrolovať výsledok a podľa potreby pokračovať,  
*   zachovať stav medzi jednotlivými krokmi alebo reláciami.  

Samotný LLM nevie priamo pristupovať k databáze, poslať e-mail, rezervovať  
termín ani zmeniť záznam v účtovnom systéme. Vie vytvoriť návrh ďalšieho kroku,  
ale nie je vhodné dovoliť mu, aby tento návrh vykonal bez kontroly. Harness  
preto rieši problém, ktorý vzniká medzi **rozhodnutím modelu** a **skutočnou  
akciou v systéme**.  

Bez tejto vrstvy by každá aplikácia musela sama riešiť opakovanie požiadaviek,  
overovanie parametrov, oprávnenia, timeouty, históriu, logovanie, limity a  
obnovu po chybe. Harness tieto opakujúce sa úlohy sústreďuje do riadiacej  
architektúry.  

## Z čoho sa AI harness skladá?  

Konkrétna implementácia môže byť malá, napríklad niekoľko funkcií v jednej  
aplikácii, alebo veľká distribuovaná služba. Typický harness však obsahuje  
viacero nasledujúcich komponentov.  

### 1. Model  

Model je jazykový alebo multimodálny model, ktorý interpretuje požiadavku,  
vyhodnocuje dostupný kontext a navrhuje odpoveď alebo ďalšiu akciu. Harness  
môže model vyberať podľa úlohy, ceny, latencie, dostupnosti alebo požadovanej  
úrovne kvality.  

Model môže napríklad rozhodnúť: „Potrebujem zavolať nástroj na vyhľadanie  
objednávky.“ Nevykoná však automaticky databázový dotaz. Vráti štruktúrovaný  
návrh volania a harness rozhodne, či je toto volanie povolené a ako sa vykoná.  

### 2. Tools alebo nástroje  

**Tools** sú presne definované operácie, ktoré agentovi poskytujú schopnosti  
navyše. Môžu to byť napríklad:  

*   vyhľadávanie v databáze,  
*   čítanie súborov alebo dokumentov,  
*   webové vyhľadávanie,  
*   volanie REST API,  
*   odoslanie e-mailu,  
*   vytvorenie úlohy v projektovom systéme,  
*   spustenie výpočtu v sandboxe,  
*   získanie aktuálneho času alebo polohy.  

Každý nástroj by mal mať popísaný názov, účel, vstupnú schému, výstupnú  
schému a oprávnenia. Harness nesmie slepo odovzdať modelu ľubovoľnú funkciu.  
Medzi modelom a skutočným nástrojom má byť adaptér, ktorý overí typy a hodnoty  
parametrov, nastaví timeout a bezpečne spracuje chybu.  

### 3. Memory a context  

Model vidí iba kontext, ktorý mu harness pošle v aktuálnej požiadavke. **Context**  
je pracovná pamäť jednej interakcie: systémové pokyny, otázka, predchádzajúce  
kroky, výsledky nástrojov a dokumenty relevantné pre aktuálnu úlohu.  

**Memory** označuje údaje, ktoré prežijú jednotlivé volanie modelu alebo celú  
reláciu. Môže ísť o:  

*   krátkodobú históriu aktuálnej konverzácie,  
*   zhrnutie starších správ,  
*   používateľské preferencie,  
*   dlhodobé fakty uložené v databáze,  
*   vektorové vyhľadávanie v dokumentoch,  
*   pracovný stav rozpracovanej úlohy.  

Harness rozhoduje, čo sa do kontextu dostane. Nemal by posielať celú databázu  
ani neobmedzenú históriu. Vyberá relevantné informácie, skracuje staršie kroky,  
odstraňuje citlivé údaje podľa pravidiel a sleduje limit kontextového okna.  

### 4. Execution loop  

**Execution loop** alebo vykonávacia slučka je jadro harnessu. Opakuje cyklus,  
v ktorom model navrhne ďalší krok, harness ho overí a prípadne vykoná.  
Zjednodušený priebeh vyzerá takto:  

1.  Harness prijme požiadavku používateľa a vytvorí počiatočný stav.  
2.  Zostaví kontext z pokynov, histórie, pamäte a dostupných nástrojov.  
3.  Pošle tento kontext modelu.  
4.  Skontroluje odpoveď modelu.  
5.  Ak model navrhol volanie nástroja, overí oprávnenia a parametre.  
6.  Nástroj vykoná akciu v prostredí a vráti výsledok.  
7.  Harness uloží výsledok do stavu a odošle ho modelu ako nový kontext.  
8.  Cyklus pokračuje, kým model nevytvorí konečnú odpoveď alebo sa nedosiahne  
    limit krokov, času alebo rozpočtu.  

Táto slučka je dôležitá, pretože model nemusí vyriešiť úlohu jedným volaním.  
Po vyhľadaní údajov môže potrebovať ďalší nástroj, po jeho použití kontrolu  
výsledku a až potom môže vytvoriť odpoveď pre človeka.  

### 5. Policies a guardrails  

**Policies** sú pravidlá systému a **guardrails** sú ochranné zábrany, ktoré  
obmedzujú správanie modelu a nástrojov. Nemali by byť iba vetou v systémovom  
prompt-e. Kritické pravidlá musí vynucovať programový kód alebo oprávnenia  
na úrovni služieb.  

Príklady pravidiel:  

*   model môže čítať objednávky, ale nesmie ich mazať,  
*   refundáciu nad určitú sumu musí schváliť človek,  
*   používateľ môže pracovať iba s vlastnými záznamami,  
*   nástroj nesmie prijať neplatný identifikátor alebo zápornú sumu,  
*   tajné kľúče sa nesmú dostať do kontextu ani do odpovede,  
*   agent nesmie navštíviť nepovolenú doménu,  
*   každý beh má maximálny počet krokov a maximálny rozpočet.  

Guardrails môžu kontrolovať vstup používateľa, návrh modelu, argumenty nástroja,  
výsledok nástroja aj konečnú odpoveď. Dôležitý je princíp, že model môže  
navrhnúť akciu, ale politika rozhoduje, či ju systém skutočne dovolí.  

### 6. Observability  

**Observability** znamená, že vieme zistiť, čo sa v systéme stalo. Harness by  
mal zaznamenávať minimálne:  

*   identifikátor behu a používateľa,  
*   použitý model a verziu promptov,  
*   jednotlivé kroky slučky,  
*   volania nástrojov a ich trvanie,  
*   chyby, retry a timeouty,  
*   počet vstupných a výstupných tokenov,  
*   približnú cenu a spotrebovaný rozpočet,  
*   dôvod ukončenia behu.  

Vďaka tomu možno odpovedať na otázky: Prečo agent poskytol nesprávny výsledok?  
Ktorý nástroj zlyhal? Koľko stojí jedna úloha? Kde vzniká latencia? Koľkokrát  
sa požiadavka opakovala? Bez týchto údajov je produkčný agent ťažko  
debugovateľný a ešte ťažšie sa zlepšuje.  

Logovanie musí rešpektovať súkromie. Do logov sa nemajú bezdôvodne ukladať  
heslá, API kľúče ani citlivé osobné údaje. V praxi sa často zaznamenávajú  
metadáta a skrátené alebo anonymizované časti obsahu.  

### 7. State management  

**State management** spravuje stav úlohy oddelene od jednotlivého výstupu  
modelu. Stav môže obsahovať napríklad:  

*   cieľ používateľa,  
*   aktuálny krok a plán,  
*   výsledky už vykonaných nástrojov,  
*   čakajúce schválenie človekom,  
*   stavové identifikátory externých systémov,  
*   počet použitých tokenov, času a peňazí.  

Oddelenie stavu od konverzácie umožňuje beh pozastaviť, obnoviť po výpadku,  
odovzdať inému workeru alebo pokračovať po ľudskom schválení. Bez toho by sa  
pri chybe často musela celá úloha začať od začiatku.  

### 8. Environment a adaptéry  

Agent pracuje v nejakom **prostredí**: v databáze, prehliadači, súborovom  
systéme, cloude alebo firemnej aplikácii. Harness vytvára hranicu medzi  
modelom a týmto prostredím.  

Adaptér prekladá všeobecné volanie nástroja na konkrétnu operáciu v danom  
systéme. Zároveň rieši autentifikáciu, timeouty, rate limity, formát výsledku  
a mapovanie chýb. Vďaka tomu model nemusí poznať internú implementáciu  
databázy alebo externého API.  

## Ako harness riadi interakciu?  

Model, nástroj a prostredie tvoria slučku, ale každý z nich má inú úlohu:  

*   **Model** interpretuje text a navrhuje rozhodnutie.  
*   **Harness** rozhodnutie zaradí do riadeného procesu.  
*   **Nástroj** vykoná presne definovanú operáciu.  
*   **Prostredie** obsahuje skutočné dáta a stav, ktorý sa môže zmeniť.  

Pri každom kroku harness robí najmä tieto činnosti:  

1.  pripraví modelu obmedzený a relevantný kontext,  
2.  oznámi mu nástroje, ktoré sú v danom kroku dostupné,  
3.  prijme textovú alebo štruktúrovanú odpoveď modelu,  
4.  rozlíši konečnú odpoveď od návrhu volania nástroja,  
5.  overí návrh podľa schémy, oprávnení a bezpečnostných pravidiel,  
6.  zavolá nástroj v mene používateľa alebo požiada o schválenie,  
7.  normalizuje výsledok a vloží ho do ďalšieho kontextu,  
8.  rozhodne, či pokračovať, opakovať krok alebo beh ukončiť.  

Model teda nie je priamym správcom vonkajšieho sveta. Harness funguje ako  
kontrolovaný prekladač medzi pravdepodobnostným výstupom modelu a  
deterministickými operáciami aplikácie.  

## LLM, agent a harness  

Tieto pojmy sa často používajú nepresne, preto je užitočné oddeliť ich:  

| Pojem | Čo robí | Čo sám osebe neposkytuje |  
| :--- | :--- | :--- |  
| **LLM** | Spracuje kontext a generuje text alebo návrh akcie | Pamäť, oprávnenia, spoľahlivé vykonanie nástroja |  
| **Agent** | Systém, ktorý používa model na dosiahnutie cieľa vo viacerých krokoch | Nemusí mať jednotný spôsob riadenia, bezpečnosti alebo logovania |  
| **AI harness** | Runtime a riadiaca vrstva pre model, nástroje, stav a pravidlá | Nie je sám o sebe inteligentným modelom |  

Agent je teda širšie označenie správania alebo celej aplikácie. Harness je  
architektonická vrstva, ktorá toto správanie vykonáva a kontroluje. Jednoduchý  
agent môže byť postavený bez výrazne oddelenej harness vrstvy, napríklad ako  
krátka slučka v skripte. Pri produkčnom systéme sa však táto vrstva zvyčajne  
stane viditeľnou a samostatne navrhovanou súčasťou architektúry.  

## Harness verzus framework a platforma  

Pojmy spolu súvisia, ale nie sú totožné.  

### Harness verzus framework  

**Framework** je súbor knižníc, tried a konvencií, ktoré uľahčujú vývoj. Môže  
ponúknuť hotové konektory k modelom, tool calling, pamäť, graf pracovného toku  
alebo tracing. Framework je teda stavebnica a často obsahuje časti potrebné na  
vytvorenie harnessu.  

**Harness** je konkrétny runtime návrh a riadiaci mechanizmus v aplikácii.  
Určuje, v akom poradí sa kroky vykonajú, aké pravidlá platia, čo sa uloží,  
kedy sa zavolá človek a ako sa systém zotaví po chybe. Jeden framework môže  
byť použitý na vytvorenie rôznych harnessov. Harness možno tiež implementovať  
priamo bez veľkého frameworku.  

### Harness verzus platforma  

**Platforma** je širšie prevádzkové prostredie alebo služba. Okrem agent runtime  
môže poskytovať hosting, správu identít, billing, datasety, hodnotenie,  
monitorovanie, modelové endpointy a používateľské rozhranie.  

Platforma môže obsahovať hotový harness, ale platforma a harness nie sú to isté.  
Platforma odpovedá na otázku „kde a s akými službami systém prevádzkujeme?“  
Harness odpovedá na otázku „ako sa počas jedného behu rozhoduje, volá nástroje,  
spravuje stav a vynucujú pravidlá?“  

| Vlastnosť | Harness | Framework | Platforma |  
| :--- | :--- | :--- | :--- |  
| Úloha | Riadi konkrétny beh agenta | Poskytuje stavebné bloky | Poskytuje celé prevádzkové prostredie |  
| Typická forma | Runtime, slučka, služby a pravidlá | Knižnica alebo SDK | Spravovaná cloudová alebo podniková služba |  
| Hlavná otázka | Čo sa vykoná ďalej? | Ako to vytvoríme? | Kde to prevádzkujeme? |  
| Príklad zodpovednosti | Schválenie refundácie | Konektor na model a nástroj | Hosting, identita a billing |  

Hranice sa môžu prekrývať. Niektoré produkty používajú slovo harness pre  
framework, runtime aj platformové služby naraz. Pri návrhu systému je preto  
dôležitejšie presne opísať zodpovednosti než trvať na jednom názve.  

### Coding agent harnesses  

Ak sa pojem harness používa v užšom kontexte AI programovania, často označuje  
hotový nástroj, ktorý spustí model v pracovnom prostredí vývojára. Takýto  
nástroj vie čítať repozitár, upravovať súbory, spúšťať terminálové príkazy,  
pracovať s gitom a opakovať cyklus návrh–akcia–kontrola. Práve do tejto  
kategórie patria napríklad tieto nástroje:  

| Nástroj | Prostredie | Čo harness riadi |  
| :--- | :--- | :--- |  
| **OpenCode** | Terminál a lokálny repozitár | Model, čítanie a úpravu súborov, shell nástroje, kontext a schvaľovanie akcií |  
| **Claude Code** | Terminál a pracovný adresár | Prácu s kódom, shell, git, nástroje a oprávnenia modelu |  
| **Codex CLI** | Terminál, sandbox a repozitár | Plánovanie úloh, úpravy súborov, príkazy, testovanie a kontrolované vykonanie |  
| **OpenHands** | Otvorený agentový runtime | Model, terminál, prehliadač, súbory a viac-krokové vykonávanie úloh |  
| **Aider** | Terminál a git repozitár | Chat s modelom, úpravy kódu, diffy a git workflow |  
| **Cline / Roo Code** | VS Code a pracovný priestor | Kontext editora, súbory, terminál, nástroje a používateľské schválenia |  
| **SWE-agent** | Výskumné a automatizované opravy repozitárov | Úlohu z issue, navigáciu v kóde, patch, testy a spätnú väzbu |  

Tieto nástroje sú bližšie významu slova **harness** než samotné knižnice na  
volanie LLM. Používateľ im zadá cieľ a harness organizuje celý pracovný beh:  
vyberie model, vloží relevantné súbory do kontextu, vykoná povolený príkaz,  
prečíta výsledok, prípadne spustí testy a rozhodne, či má pokračovať.  

Pojem sa však nepoužíva úplne jednotne. Niektoré z týchto produktov sa  
označujú ako coding agent, CLI agent alebo agent runtime. Z architektonického  
hľadiska však plnia úlohu harnessu, pretože spájajú LLM s nástrojmi,  
repozitárom, operačným systémom, stavom a bezpečnostnými pravidlami.  

### Frameworky a SDK pre vlastný harness  

Nasledujúce nástroje sa v praxi používajú na stavbu agentov a často poskytujú  
aspoň časť funkcií harnessu. Nie všetky sa marketingovo označujú ako harness.  
Niektoré sú frameworky alebo SDK a produkčný systém k nim musí doplniť vlastné  
oprávnenia, limity, observability a správu stavu.  

| Nástroj | Typický spôsob použitia | Čo poskytuje pre harness |  
| :--- | :--- | :--- |  
| **OpenAI Agents SDK** | Agenti používajúci modely OpenAI | Tools, handoffs medzi agentmi, guardrails a tracing |  
| **Claude Agent SDK** | Agenti postavení okolo modelov Claude | Tool use, riadenie oprávnení a vykonávanie agentových krokov |  
| **LangGraph** | Stavové workflow a grafy krokov | Execution loop, checkpointy, vetvenie a human-in-the-loop |  
| **Google ADK** | Jednoduché aj multi-agent aplikácie | Agenti, nástroje, orchestrácia, stav a hodnotenie |  
| **Microsoft Agent Framework** | Podnikové agentové workflow | Modely, tools, workflow, stav a integrácia do podnikových systémov |  
| **PydanticAI** | Typovo kontrolovaní agenti v Pythone | Schémy nástrojov, validované výstupy a podpora viacerých providerov |  
| **CrewAI** | Spolupráca viacerých agentov s rolami | Delegovanie úloh, procesy, nástroje a tímová orchestrácia |  
| **AutoGen** | Konverzácie a spolupráca viacerých agentov | Správy medzi agentmi, tool calling a viacagentové workflow |  
| **smolagents** | Ľahké code agents a action agents | Jednoduchá slučka, tools a vykonávanie akcií s malou réžiou |  
| **LlamaIndex** | Agenti nad dokumentmi a dátovými zdrojmi | Retrieval, konektory k dátam, tools a workflow nad kontextom |  

Pri výbere nástroja treba sledovať, ktorú časť architektúry skutočne rieši.  
Napríklad LangGraph je silný pri explicitnom riadení stavu a prechodov, kým  
PydanticAI kladie dôraz na typovú kontrolu nástrojov a výstupov. CrewAI a  
AutoGen sú vhodné na modelovanie spolupráce agentov, ale stále treba navrhnúť  
bezpečnostné hranice a pravidlá pre konkrétnu aplikáciu.  

Nástroj sám osebe nezaručuje spoľahlivého agenta. Aj pri použití hotového SDK  
musí tím rozhodnúť, ktoré akcie vyžadujú schválenie človekom, ako sa obnoví beh  
po chybe, aké údaje sa smú uložiť a aký maximálny čas či rozpočet má agent.  

## Jednoduchý príklad: agent pre stav objednávky  

Predstavme si zákaznícku podporu. Používateľ napíše:  

> Kde je moja objednávka 4815 a môžem ju ešte zrušiť?  

Samotný LLM pozná jazyk, ale nepozná aktuálny stav objednávky. Agent s  
harnessom môže postupovať takto:  

1.  **Prijatie požiadavky:** harness overí identitu používateľa a vytvorí  
    identifikátor behu.  
2.  **Príprava kontextu:** model dostane otázku, pravidlá podpory a zoznam  
    nástrojov `get_order` a `cancel_order`.  
3.  **Rozhodnutie modelu:** model navrhne volanie `get_order` s identifikátorom  
    4815.  
4.  **Kontrola harnessu:** harness overí, že používateľ má právo čítať túto  
    objednávku a že identifikátor má správny formát.  
5.  **Vykonanie nástroja:** adaptér zavolá objednávkový systém a vráti stav,  
    napríklad „balík bol odoslaný a zrušenie už nie je možné“.  
6.  **Druhý krok modelu:** výsledok sa vloží do kontextu. Model pochopí, že  
    nástroj na zrušenie nemá volať, pretože pravidlá objednávky to nedovoľujú.  
7.  **Konečná odpoveď:** harness zobrazí používateľovi zrozumiteľné vysvetlenie  
    a uloží priebeh behu do logu.  

Ak by model namiesto toho navrhol `cancel_order`, harness ho ešte stále môže  
zastaviť. Skontroluje stav objednávky, oprávnenie používateľa a pravidlo, že  
odoslanú objednávku nemožno zrušiť. Model môže urobiť nesprávny návrh, ale  
nemal by mať možnosť obísť tieto kontroly.  

Tento príklad ukazuje architektonickú úlohu harnessu jasnejšie než samotná  
definícia. Model interpretuje požiadavku, nástroj pozná objednávkový systém a  
harness koordinuje ich komunikáciu, vynucuje pravidlá a uchováva stav.  

## Prečo je harness dôležitý v produkcii?  

Demo môže fungovať tak, že pošle prompt modelu a vytlačí výsledok. Produkčný  
agent však musí fungovať aj pri chybách, veľkom zaťažení a nejednoznačných  
požiadavkách. Harness poskytuje miesta, kde možno tieto riziká riadiť.  

### Spoľahlivosť  

Harness môže používať timeouty, kontrolované opakovanie, idempotentné operácie,  
validáciu odpovedí a obnovu po výpadku. Ak nástroj zlyhá, systém môže bezpečne  
zopakovať iba daný krok namiesto celej úlohy.  

### Bezpečnosť  

Nástroje možno obmedziť podľa používateľa, roly, prostredia a citlivosti akcie.  
Čítanie údajov môže byť automatické, ale mazanie, platba alebo odoslanie správy  
môže vyžadovať potvrdenie človeka.  

### Predvídateľné náklady  

Harness môže sledovať počet tokenov, cenu, počet volaní a čas behu. Nastavenie  
maximálneho počtu krokov a rozpočtu zabráni tomu, aby agent uviazol v slučke  
a vytvoril veľký účet.  

### Testovanie a hodnotenie  

Keď sú rozhodnutia, volania nástrojov a výsledky zaznamenané, možno testovať  
nielen konečný text, ale aj celý priebeh. Tím môže zistiť, či agent vybral  
správny nástroj, použil správne parametre a rešpektoval pravidlá.  

### Výmena modelu  

Ak harness oddeľuje model od nástrojov a stavu, model možno vymeniť bez  
prepísania celej aplikácie. Menší model môže riešiť jednoduché úlohy a  
výkonnejší model zložité prípady, pričom bezpečnostné pravidlá zostanú rovnaké.  

### Ľudské schválenie  

Nie všetko treba automatizovať. Harness môže beh pozastaviť, zobraziť človeku  
navrhovanú akciu, počkať na schválenie a potom pokračovať v rovnakom stave.  
Toto je dôležité pri financiách, právnych krokoch, komunikácii so zákazníkom  
a pri práci s citlivými údajmi.  

## Časté omyly  

**„Harness je iba prompt.“** Prompt dáva modelu pokyny, ale nerieši timeouty,  
oprávnenia, stav, náklady ani skutočné vykonanie nástrojov.  

**„Agent si všetko pamätá.“** Model vidí iba to, čo mu harness vloží do  
kontextu. Dlhodobú pamäť treba explicitne uložiť, vyhľadať a spravovať.  

**„Keď model vie zavolať tool, môže ho aj bezpečne používať.“** Tool calling je  
iba komunikačný formát. Bez validácie a oprávnení môže model navrhnúť neplatnú  
alebo nebezpečnú operáciu.  

**„Viac krokov znamená inteligentnejšieho agenta.“** Každý ďalší krok zvyšuje  
latenciu, cenu a počet miest, kde môže nastať chyba. Harness má vedieť beh  
ukončiť, keď je cieľ splnený.  

**„Framework automaticky vyrieši architektúru.“** Framework poskytne nástroje,  
ale pravidlá, hranice oprávnení, stav a zodpovednosť musí navrhnúť tím.  

## Zhrnutie kapitoly  

*   AI harness je riadiaca a vykonávacia vrstva, ktorá obklopuje LLM agenta.  
*   Vznikol preto, že samotný model nevie bezpečne a spoľahlivo riadiť nástroje,  
    pamäť, stav ani vonkajšie prostredie.  
*   Typický harness obsahuje model, nástroje, context a memory, execution loop,  
    policies a guardrails, observability, state management a adaptéry prostredia.  
*   Model navrhuje ďalší krok, ale harness ho overuje, vykoná alebo zastaví.  
*   LLM je model, agent je systém orientovaný na cieľ a harness je runtime,  
    ktorý jeho kroky koordinuje a kontroluje.  
*   Framework je stavebnica a platforma je širšie prevádzkové prostredie;  
    harness je konkrétna riadiaca architektúra behu agenta.  
*   Pri produkčnom nasadení harness zvyšuje spoľahlivosť, bezpečnosť,  
    pozorovateľnosť, kontrolu nákladov a možnosť ľudského schválenia.  

## Otázky & diskusia  

1.  Vysvetlite rozdiel medzi LLM, agentom a AI harnessom.  
2.  Prečo nestačí poslať modelu prompt s pokynom, aby sám použil databázu?  
3.  Akú úlohu má execution loop?  
4.  Prečo by mal harness overovať argumenty nástroja, aj keď ich vytvoril model?  
5.  Uveďte príklad akcie, pri ktorej by malo byť potrebné ľudské schválenie.  
6.  Vysvetlite rozdiel medzi context a memory.  
7.  Ako observability pomáha pri hľadaní chyby a kontrole ceny agenta?  
8.  V čom sa harness líši od frameworku a platformy?  
9.  Navrhnite pravidlá pre agenta, ktorý môže čítať, ale nie meniť firemné dáta.  
10. Nakreslite alebo opíšte tok požiadavky od používateľa cez model a nástroj  
    späť ku konečnej odpovedi.  

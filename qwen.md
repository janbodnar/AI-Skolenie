# Kapitola: Qwen – Alibabina priemyselná škála AI  

Kým DeepSeek ukázal svetu, čo dokáže malý tím s obmedzeným hardvérom,  
Qwen ukazuje niečo iné: **čo dokáže technologický gigant, keď nasadí  
plnú priemyselnú kapacitu**.  
Qwen je séria veľkých jazykových modelov vyvíjaných spoločnosťou Alibaba Cloud –  
a za ňou stojí jeden z najväčších e-commerce a cloudových konglomerátov  
na svete.  

Celé čínske meno – **通义千问** (Tongyi Qianwen) – sa prekladá ako  
„jednotná odpoveď na tisíc otázok".  
Meno hovorí o zámeroch: Alibaba nechce len chatbota, ale univerzálneho  
AI asistenta pokrývajúceho celú šírku ľudského poznania.  
V angličtine sa skracuje na **Qwen** (vyslovuj: „čchen").  

---

## Vznik a pozadie spoločnosti  

### Alibaba Group: od bytu v Hangzhou k biliónovej ríši  

Alibaba Group bola founded v roku **1999** Jackom Ma (Ma Yun)  
a sedemnástimi spoluzakladateľmi v skromnom byte v Hangzhou.  
Čo začalo ako platforma pre B2B elektronický obchod, sa za dve desaťročia  
rozrástlo na jednu z najväčších technologických spoločností sveta:  

*   **Alibaba.com** – globálna B2B marketplace  
*   **Taobao a Tmall** – čínsky ekvivalent Amazonu  
*   **Alipay** – digitálna platobná platforma (neskôr vyčlenená do Ant Group)  
*   **Alibaba Cloud (Aliyun)** – cloudová divízia spustená v roku **2009**,  
    dnes tretí najväčší cloudový poskytovateľ na svete (po AWS a Azure)  

Alibaba Cloud je priamym rodinným prostredím, v ktorom Qwen vznikol.  
Na rozdiel od DeepSeeku (financovaného z hedžového fondu) alebo  
Anthropicu (závislého od investorov) má Qwen za sebou cloudovú  
infraštruktúru vlastnú firme – čo znamená neobmedzenú výpočtovú kapacitu  
a priamu cestu k miliónom podnikových zákazníkov.  

### Jack Ma: vizionár, rebel a „zmiznutý" miliardár  

Jacka Ma nie je možné vynechať pri akomkoľvek texte o Alibabe.  
Syn divadelných hercov bez akademického titulu z prestížnej školy  
sa pokúšal o prácu v KFC – a odmietli ho.  
Neskôr vybudoval firmu, ktorá v roku 2014 vstúpila na burzu v **New Yorku  
rekordným IPO za 25 miliárd dolárov** – dovtedy najväčší burzový debut  
v histórii.  

V roku **2020** sa však Jackova hviezda zrazila s čínskou mocou.  
Na konferencii v Šanghaji verejne skritizoval čínske regulačné orgány,  
ktoré nazval „záložnárňami" brániacimi inováciám. Krátko potom:  

*   Plánované IPO Ant Group (115 miliárd dolárov – potenciálne najväčšie IPO  
    v histórii) bolo **zablokované deň pred spustením**.  
*   Alibaba dostala rekordnú **pokutu 2,75 miliardy dolárov** od antimonopolného  
    úradu.  
*   Jack Ma sa na niekoľko mesiacov **stratil z verejného života** – jeho  
    neprítomnosť špekulatívne komentovala svetová tlač.  

Ma sa objavil spätne, no odvtedy výrazne obmedzil verejné vystúpenia  
a v roku **2023 prenechal výkonné riadenie** spoločnosti novej generácii  
vedenia.  
Znovu-found sa ticho stiahol v pozadí, oceňovaný za budovanie,  
no vzdialený od aktuálneho chodu firmy.  

### DAMO Academy: Alibabov výskumný mozog  

Qwen nevznikol v izolovanom AI laboratóriu, ale v rámci **DAMO Academy**  
(达摩院 – Dámó Xuéyuàn), výskumnej divízie Alibaby spustenej v roku **2017**  
s prisľúbenou investíciou 15 miliárd dolárov.  
DAMO Academy zamestnáva tisíce výskumníkov vo výskumných centrách v Číne,  
USA, Singapure, Rusku a Izraeli.  

Pre modely Qwen je kľúčový tím **Qwen Team** pod vedením Alibaba Cloud.  
Na rozdiel od Anthropicu (kde sú Dario a Daniela Amodei tvárou firmy)  
alebo xAI (kde dominuje Musk) je Qwen Team kolektívne dielo – mená  
jednotlivých výskumníkov sú menej prominentné, čo odráža typickú  
čínsku firemnú kultúru, kde tím je dôležitejší ako jednotlivec.  

---

## Modely Qwen – prehľad  

| Model | Vydanie | Kľúčové vlastnosti |  
| :--- | :--- | :--- |  
| **Qwen-7B / 14B** | aug. 2023 | Prvé open-source vydania, základ série |  
| **Qwen-72B** | nov. 2023 | Vlajkový hustý model, 72 miliárd parametrov |  
| **Qwen-VL** | sep. 2023 | Multimodálna verzia (text + obrázky) |  
| **Qwen-Audio** | nov. 2023 | Spracovanie zvuku a reči |  
| **Qwen1.5** | feb. 2024 | Vylepšená rodina 0,5B–110B, lepšia viacjazyčnosť |  
| **Qwen2** | jún 2024 | Prelom: Qwen2-72B konkuruje GPT-4o na benchmarkoch |  
| **Qwen2-VL** | sep. 2024 | Nová generácia videnia, najlepší open-source multimodál |  
| **Qwen2.5** | sep. 2024 | Rodina 0,5B–72B, +Coder a +Math špeciality |  
| **Qwen2.5-Max** | feb. 2025 | Najsilnejší model pred Qwen3, súperí s DeepSeek-V3 |  
| **QwQ-32B** | mar. 2025 | Reasoning model, prekvapivo silný pri 32B parametroch |  
| **Qwen3** | apr. 2025 | **Prelomová generácia: hybridné myslenie, MoE, open-source** |  
| **Qwen3.5** | aug. 2025 | Vylepšený základ, dlhší kontext, agentické schopnosti |  
| **Qwen4** | jan. 2026 | Aktuálny vlajkový model, 2M kontext, natívne nástroje |  

---

## Qwen2 – tichý prelom (jún 2024)  

V lete 2024 Alibaba urobil niečo, čo mnohých prekvapilo: **Qwen2-72B**  
sa v nezávislých benchmarkoch zaradil po bok GPT-4o a Claude 3.5 Sonnet –  
modelov firiem s mnohonásobne väčším PR rozpočtom a renomé.  

Toto neboli len interné testy Alibaby.  
Komunita výskumníkov na platforme Hugging Face (globálnej platforme  
pre open-source AI modely) Qwen2-72B otestovala na štandardizovaných  
sadách a výsledky boli jednoznačné: čínsky model z e-commerce gigantu  
patrí medzi svetovú špičku.  

Key prínosov Qwen2 oproti predchodcovi:  
*   **Viacjazyčnosť:** podpora 29 jazykov vrátane arabčiny, španielčiny,  
    francúzštiny, japončiny, kórejčiny – nie len čínštiny a angličtiny.  
*   **Kódovanie:** výrazné zlepšenie v programovacích benchmarkoch.  
*   **Dlhší kontext:** až 128 000 tokenov v základných modeloch.  
*   **Open-source:** model uvoľnený pod licenciou Apache 2.0.  

---

## QwQ – číska odpoveď na reasoning modely  

Zatiaľ čo DeepSeek-R1 zachytil všetku mediálnu pozornosť v januári 2025,  
**QwQ-32B** (vydaný v marci 2025) priniesol rovnako pozoruhodný výsledok  
bez podobného šoku.  
„QwQ" je čínska onomatopoja pre zmätok a uvažovanie – zvuk, ktorý robí  
mozog pri riešení ťažkého problému.  

Kľúčové fakty:  
*   Len **32 miliárd parametrov** – výrazne menej ako DeepSeek-R1-671B  
    alebo o1 od OpenAI.  
*   Napriek tomu dosiahol **porovnateľné výsledky** v matematike (AIME),  
    kódovaní (LiveCodeBench) a vedeckom uvažovaní (GPQA).  
*   Chain-of-thought uvažovanie: model „premýšľa nahlas" pred finálnou  
    odpoveďou, podobne ako DeepSeek Deep Think alebo Claude Extended Thinking.  
*   **Plne open-source** pod Apache 2.0.  

QwQ ukázal, že reasoning schopnosti nie sú výsadou modelov s stovkami  
miliárd parametrov – správne natrénovný 32B model môže konkurovať  
oveľa väčším systémom.  

---

## Qwen3 – hybridné myslenie mení pravidlá (apríl 2025)  

Vydanie **Qwen3** v apríli 2025 bolo najvýznamnejším vydaním Alibaby  
v histórii AI a zaradilo Qwen medzi absolútnu globálnu špičku.  

### Rodina Qwen3  

Qwen3 je kompletná rodina modelov pre rôzne potreby:  

| Veľkosť | Typ | Aktívne parametre |  
| :--- | :--- | :--- |  
| **0,6B / 1,7B / 4B / 8B** | Husté modely | = celkové parametre |  
| **14B / 32B** | Husté modely | = celkové parametre |  
| **30B-A3B** | MoE | 3 miliardy z 30 miliárd |  
| **235B-A22B** | MoE | 22 miliárd z 235 miliárd |  

Najvýkonnejší model **Qwen3-235B-A22B** má celkovo 235 miliárd parametrov,  
no pri každom tokene aktivuje len 22 miliárd – vďaka architektúre  
**Mixture of Experts** (rovnaký princíp ako u DeepSeeku).  

### Hybridné myslenie: jeden model, dva režimy  

Najväčšou inováciou Qwen3 je **hybridné myslenie** – schopnosť, ktorú  
predtým ponúkali len niektoré prémiové modely:  

*   **Thinking mode (zapnuté):** Model aktivuje rozsiahly chain-of-thought  
    proces, „premýšľa" krok za krokom pred odpoveďou.  
    Ideálne pre matematiku, kódovanie a komplexné úlohy.  
*   **Non-thinking mode (vypnuté):** Model odpovedá priamo bez  
    dlhého uvažovania. Rýchlejšie a lacnejšie pre jednoduché otázky.  

Používateľ môže medzi režimami prepínať manuálne, alebo nastaviť  
**budget tokenov pre myslenie** – model teda minie presne toľko  
„uvažovania", koľko povolíte.  
Toto je zásadná ekonomická inovácia: platíte len za toľko uvažovania,  
koľko úloha skutočne potrebuje.  

### Benchmark výsledky  

Pri vydaní Qwen3-235B-A22B dosiahol na kľúčových benchmarkoch výsledky  
porovnateľné s GPT-4.1 a Claude 3.7 Sonnet – predchodcami vtedy  
aktuálnych vlajkových modelov.  
Pre komunitu výskumníkov to bol ďalší signál: čínske open-source modely  
systematicky dobíhajú americkú špičku.  

---

## Technické inovácie Qwen série  

### 1. Efektívna MoE architektúra  

Qwen3 využíva **jemnozrnnú MoE** (Mixture of Experts) s veľkým  
počtom malých expertov namiesto niekoľkých veľkých.  
Výsledok: lepšia aktivácia relevantných znalostí a nižšia spotreba pamäte.  

### 2. Multimodálna rodina  

Alibaba nevyvíja len textové modely, ale celú **multimodálnu rodinu**:  

*   **Qwen-VL / Qwen2-VL:** analýza obrázkov, dokumentov, grafov  
*   **Qwen-Audio:** rozpoznávanie reči, analýza zvuku a hudby  
*   **Qwen2.5-Omni:** kombinovaný model pre text, obraz, zvuk aj generovanie hlasu  
*   **Qwen-Math a Qwen-Coder:** špecializované modely pre matematiku  
    a programovanie  

### 3. Viacjazyčnosť  

Qwen je jedným z mála modelov, ktorý bol trénovaný so **silným dôrazom**  
na jazyky mimo angličtiny a čínštiny.  
Qwen3 podporuje  

*   **119 jazykov** vrátane slovenčiny, arabčiny, hindčiny, swahilčiny  
    a ďalších  
*   Pre ázijské jazyky (japončina, kórejčina, vietnamčina) dosahuje výsledky  
    výrazne lepšie ako väčšina západných modelov  

### 4. Dlhé kontextové okno  

Qwen4 (január 2026) ponúka kontextové okno **2 miliónov tokenov** –  
čo je porovnateľné s Claudom a Grokom na vrchole tabuľky.  

---

## Bezpečnostné a politické obavy  

Rovnako ako DeepSeek, aj Qwen prichádza z Číny – a nesie so sebou  
rovnakú sadu otázok o súkromí a cenzúre.  

### 1. Čínske serverové právo  

Alibaba Cloud otvorene uvádza, že dáta ukladá na serveroch v Číne,  
na ktoré sa vzťahujú čínske právne predpisy.  
Zákon o národnej bezpečnosti z roku 2015 zaväzuje čínske spoločnosti  
poskytnúť dáta vláde na požiadanie.  

### 2. Cenzúra politicky citlivých tém  

Výskumníci opakovane overili, že Qwen zdieľa rovnaké „slepé miesta"  
ako iné čínske modely:  

*   **Tiananmenské námestie (1989):** Odmietnutie diskusie alebo  
    dezinformácie v súlade so štátnym naratívom.  
*   **Taiwan:** Opisovaný výhradne ako neoddeliteľná súčasť Číny.  
*   **Xinjiang a Tibet:** Citlivé témy pokryté officiálnymi naratívmi.  
*   **Kritika KSČ alebo Jackovi Ma:** Opatrné vyhýbanie sa alebo odmietnutie.  

Pre bežné pracovné úlohy (kódovanie, písanie, matematika) tieto  
obmedzenia nemajú žiadny praktický dosah.  
Pre akademické, novinárske alebo politicky citlivé témy je model  
nespoľahlivý.  

### 3. Reakcia vlád a inštitúcií  

| Krajina / Organizácia | Opatrenie |  
| :--- | :--- |  
| **Austrália** | Odporúčanie zdržanlivosti pre vládnych pracovníkov |  
| **Európska únia** | Šetrenie v rámci AI Act – preverovanie čínskych modelov |  
| **USA – vládne agentúry** | Neformálny zákaz na citlivých pracoviskách |  
| **Japonsko, Južná Kórea** | Obmedzenia v štátnych inštitúciách |  

Na rozdiel od DeepSeeku, ktorý čelil hlasným zákazom, Qwen unikal  
priamej pozornosti médií – no bezpečnostné odporúčania pre vládne  
inštitúcie sú rovnaké.  

---

## Qwen vo svete open-source  

Jednou z kľúčových stratégií Alibaby je **systematické open-sourcovanie**  
modelov Qwen – čo je zásadný rozdiel oproti ChatGPT (uzavretý) alebo  
Claudovi (uzavretý).  

Na platforme **Hugging Face** sú Qwen modely konzistentne medzi  
**najsťahovanejšími** na svete – pravidelne obsadzujú top 5 medzi  
open-source modelmi.  
Comunita vedcov, vývojárov a startupov po celom svete ich integruje  
do vlastných produktov, dolaďuje (fine-tuninguje) pre špeciálne úlohy  
a buduje na nich stovky komerčných aplikácií.  

Alibaba tým sleduje stratégiu podobnú Meta's Llama: poskytnúť základ  
celej komunite, vybudovať ekosystém a zároveň udržať prémiovú  
API verziu pre podnikových zákazníkov.  

---

## Kde nájdete Qwen  

| Prístup | Popis |  
| :--- | :--- |  
| **chat.qwen.ai** | Webová aplikácia pre bežných používateľov |  
| **Alibaba Cloud DashScope API** | Primárne API pre vývojárov |  
| **Hugging Face** | Otvorené sťahovanie open-source verzií |  
| **ModelScope** | Čínsky ekvivalent Hugging Face (Alibaba platforma) |  
| **Amazon Bedrock** | Qwen modely dostupné cez AWS (od 2025) |  
| **Microsoft Azure** | Vybrané Qwen modely v Azure AI (od 2025) |  

### Cenové plány  

*   **Bezplatné (chat.qwen.ai):** Prístup k menším modelom s dennými limitmi.  
*   **Platený plán:** Prístup k vlajkovým modelom bez obmedzení.  
*   **API (DashScope):** Platba podľa tokenov, ceny konkurencieschopné  
    s DeepSeekom – výrazne lacnejšie ako OpenAI alebo Anthropic.  
*   **Open-source (lokálne):** Qwen3-8B / 14B / 32B je možné spustiť  
    bezplatne na vlastnom hardvéri.  

---

## Funkcie pre používateľov  

### Kontextové okno  

**Qwen4** v bezplatnej API verzii ponúka kontext **128 000 tokenov**,  
prémiová verzia až **2 milióny tokenov**.  
V praxi 128K tokenov predstavuje zhruba 100 000 slov – napríklad  
celý román alebo dlhú technickú dokumentáciu v jednej konverzácii.  

### Thinking mode – hybridné uvažovanie  

Funkcia dostupná od **Qwen3** (apríl 2025) umožňuje zapnúť alebo vypnúť  
hlboké uvažovanie podľa potreby:  

*   **Zapnuté:** Pre matematiku, logiku, kódovanie – model „premýšľa" viditeľne  
    krok za krokom, čo je mimoriadne poučné pri štúdiu.  
*   **Vypnuté:** Pre rýchle otázky, preklad, sumarizáciu – odpoveď je okamžitá.  

Môžete tiež nastaviť **budget tokenov** pre uvažovanie – napríklad povolíte  
modelu „premyslieť" maximálne 2 000 tokenov, čo šetrí náklady bez výraznej  
straty kvality.  

### Multimodálne schopnosti  

Model **Qwen2.5-Omni** (dostupný v API) zvláda:  
*   Analýzu obrázkov a dokumentov (tabuľky, grafy, fotografie)  
*   Rozpoznávanie reči a analýzu zvukových záznamov  
*   Generovanie hovoreného hlasu pre odpovede  
*   Porozumenie videozáznamom  

### Viacjazyčná sila  

Pre slovenských používateľov je relevantné, že Qwen3+ modely slovenčinu  
zvládajú výrazne lepšie ako väčšina open-source alternatív – aj keď stále  
za úrovňou GPT-4o alebo Claudea.  

---

## Porovnanie s konkurenciou  

| Vlastnosť | Qwen (Alibaba) | ChatGPT / GPT-5 (OpenAI) | Claude (Anthropic) | DeepSeek |  
| :--- | :--- | :--- | :--- | :--- |  
| **Pôvod** | Čína (Alibaba) | USA (OpenAI) | USA (Anthropic) | Čína (DeepSeek) |  
| **Open-source** | áno (základ. modely) | nie | nie | áno (MIT) |  
| **Kontextové okno** | 2 milióny tokenov | ~128 000 tokenov | 1 milión tokenov | 1 milión tokenov |  
| **Hybridné myslenie** | áno (Qwen3+) | áno (integrované) | áno (Extended Thinking) | áno (Deep Think) |  
| **Multimodalita** | áno (text, obraz, zvuk, video) | áno (natívne) | čiastočne | nie (základ) |  
| **Viacjazyčnosť** | 119 jazykov (silná) | silná | silná | silná (čínština) |  
| **Cena API** | nízka | stredná–vysoká | stredná–vysoká | nízka |  
| **Politická cenzúra** | áno (čínske témy) | nie | nie | áno (čínske témy) |  
| **Lokálne nasadenie** | áno (open-source) | nie | nie | áno (open-source) |  

---

## Qwen vs. DeepSeek: dve tváre čínskej AI  

Oba modely sú čínske, oba sú open-source a oba vyvolávajú rovnaké  
bezpečnostné otázky.  
No ich filozofia je diametrálne odlišná:  

**DeepSeek** je príbeh o **efektívnosti z núdze** – malý tím, obmedzený  
hardvér, prevratný výsledok pri zlomku bežných nákladov.  
Je to výskumná spoločnosť, ktorej primárnym výsledkom sú akademické  
publikácie a modely.  

**Qwen** je príbeh o **priemyselnej škále** – obrovský tím, neobmedzená  
cloudová infraštruktúra, systematické vydávanie celej rodiny modelov  
pre rôzne účely (text, obraz, zvuk, kód, matematika).  
Je to produktová divízia technologického giganta s miliónmi podnikových  
zákazníkov.  

Oba prístupy sú legitímne a oba viedli k svetovo konkurencieschopným  
výsledkom.  
Pre používateľov je praktický záver jednoduchý: **oba sú dostupné zadarmo**  
a oba stojí za vyskúšanie pre rôzne typy úloh.  

---

## Alibaba a AI na globálnom trhu  

Qwen nie je len akademický projekt – je kľúčovou súčasťou obchodnej stratégie  
Alibaba Cloud na globálnom trhu.  
Cloud divízia v roku 2025 oznámila, že AI príspevky rastú trojciferným  
percentom medziročne, pričom Qwen API je najrýchlejšie rastúcou súčasťou  
portfólia.  

Alibaba investuje do AI startupov po celom svete a aktívne buduje  
partnerstvá s cloudovými poskytovateľmi (AWS, Azure), kde sú Qwen  
modely dostupné ako alternatíva k OpenAI modelom.  
Táto stratégia „všade kde zákazník je" – kombinovaná s nižšími cenami  
a open-source dostupnosťou – predstavuje vážnu dlhodobú hrozbu pre  
dominanciu amerických modelov v podnikových systémoch.  

---

## Zhrnutie kapitoly  

*   **Qwen** je séria AI modelov vyvíjaných **DAMO Academy** a tímom  
    Alibaba Cloud, dcérskej divízie Alibaba Group so sídlom v Hangzhou.  
*   Za Qwenom stojí príbeh **Alibaby** – od bytu Jacka Ma v roku 1999 cez  
    rekordné IPO až po konflikt s čínskou vládou v rokoch 2020–2021.  
*   Prelomom bol **Qwen2-72B** (jún 2024), ktorý medzi open-source modelmi  
    prvýkrát dosiahol výsledky porovnateľné so špičkovými americkými modelmi.  
*   **QwQ-32B** (marec 2025) ukázal, že reasoning schopnosti sú dosiahnuteľné  
    aj pri 32B parametroch – čo spochybňuje predpoklad „väčší = lepší".  
*   **Qwen3** (apríl 2025) priniesol **hybridné myslenie** – schopnosť prepínať  
    medzi rýchlym a hlbokým uvažovaním, ako aj MoE architektúru pre efektívne  
    spracovanie.  
*   Qwen modely sú systematicky uvoľňované ako **open-source** pod  
    licenciou Apache 2.0 a patria medzi najsťahovanejšie modely  
    na Hugging Face.  
*   Rovnako ako DeepSeek, aj Qwen **cenzuruje politicky citlivé témy**  
    v súlade s čínskymi zákonmi a pre firemné nasadenie odporúča opatrnosť.  
*   Kľúčovou výhodou Qwenu je **priemyselná škála** – celá rodina modelov  
    pre text, obraz, zvuk a špeciálne úlohy – dostupná za nízke ceny  
    cez globálnu cloudovú infraštruktúru.  

## Otázky & diskusia

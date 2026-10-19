# Anthropic a modely Claude  

Anthropic je spoločnosť, ktorá sa za necelých päť rokov vypracovala  
z „bezpečnostného laboratória" bývalých zamestnancov OpenAI na jedného  
z dvoch najväčších hráčov v oblasti umelej inteligencie. Jej asistent  
**Claude** je obľúbený najmä medzi programátormi a firmami a v roku 2026  
Anthropic podľa viacerých ukazovateľov predbehla aj samotnú OpenAI.  

*Stav k októbru 2026. Údaje o modeloch, cenách a financiách sa rýchlo menia.*  

## Vznik spoločnosti a zakladatelia  

Anthropic bola založená v roku **2021** v San Franciscu. Zakladala ju  
skupina siedmich bývalých výskumníkov OpenAI, ktorí mali iný názor na to,  
ako rýchlo a s akým dôrazom na bezpečnosť vyvíjať čoraz silnejšie modely.  

Od začiatku je Anthropic registrovaná ako **Public Benefit Corporation**  
(PBC) – spoločnosť, ktorá okrem zisku musí sledovať aj verejnoprospešné  
poslanie. Jej misiou je *„zabezpečiť, aby svet bezpečne prešiel  
transformáciou spôsobenou transformatívnou AI"*.  

Kľúčoví zakladatelia:  

*   **Dario Amodei (CEO):** V OpenAI bol viceprezidentom pre výskum  
    a viedol vývoj modelov GPT-2 a GPT-3. Vyštudovaný fyzik a neurovedec.  
    Je hlavnou verejnou tvárou spoločnosti a autorom vplyvných esejí  
    o budúcnosti AI.  
*   **Daniela Amodei (prezidentka):** Dariova sestra, v OpenAI viceprezidentka  
    pre bezpečnosť a politiku. Riadi obchodnú a prevádzkovú stránku firmy.  
*   **Jared Kaplan (hlavný vedec):** Teoretický fyzik, spoluautor slávnej  
    práce o **zákonoch škálovania** (*scaling laws*, 2020), ktorá ukázala, že  
    výkon modelov predvídateľne rastie s veľkosťou modelu, dát a výpočtov.  
*   **Chris Olah:** Priekopník **interpretovateľnosti** – výskumu, ktorý sa  
    snaží pochopiť, čo sa deje vo vnútri neurónových sietí.  
*   **Tom Brown, Sam McCandlish, Ben Mann a Jack Clark:** Tom Brown bol  
    hlavným autorom článku o GPT-3, Jack Clark vedie oblasť verejnej  
    politiky.  

### Kontrola nad spoločnosťou  

Popri bežnej správnej rade má Anthropic aj **Long-Term Benefit Trust** –  
nezávislú skupinu správcov bez finančného podielu, ktorá postupne volí  
väčšinu členov predstavenstva. Cieľom je, aby si spoločnosť udržala misiu  
aj pod tlakom investorov.  

## Bezpečnosť ako stratégia  

Anthropic sa od začiatku profiluje ako firma, pre ktorú je bezpečnosť AI  
hlavným zmyslom existencie. Jej logika je paradoxná: ak sa silná AI  
vyvinie tak či tak, je lepšie, aby na čele vývoja boli aj firmy, ktoré  
berú riziká vážne – a mohli ukázať, že bezpečný prístup je  
konkurencieschopný.  

### Constitutional AI  

V roku 2022 Anthropic predstavila metódu **Constitutional AI**. Namiesto  
toho, aby ľudia hodnotili každú odpoveď modelu (ako pri RLHF), dostane  
model písomný súbor zásad – **ústavu** – a učí sa podľa nej sám hodnotiť  
a opravovať svoje odpovede. Zásady sú inšpirované napríklad Všeobecnou  
deklaráciou ľudských práv. V januári 2026 Anthropic zverejnila novú,  
podstatne rozsiahlejšiu ústavu, ktorá viac vysvetľuje dôvody pravidiel,  
než aby len prikazovala.  

### Responsible Scaling Policy  

V roku 2023 prijala Anthropic **Responsible Scaling Policy** (RSP) –  
záväzok, že s rastúcimi schopnosťami modelov bude sprísňovať ochranné  
opatrenia. Modely sa zaraďujú do úrovní **ASL** (*AI Safety Level*),  
podobne ako laboratóriá podľa biologickej bezpečnosti. V máji 2025 bola  
pri modeli Claude Opus 4 po prvý raz aktivovaná prísnejšia úroveň  
**ASL-3**, najmä kvôli riziku zneužitia pri biologických zbraniach.  

### Interpretovateľnosť  

Anthropic patrí k lídrom vo výskume vnútorného fungovania modelov.  
Známym príkladom je experiment **Golden Gate Claude** (2024): výskumníci  
našli v modeli „neurón" (presnejšie *feature*) zodpovedajúci mostu Golden  
Gate, zosilnili ho – a model potom do každej odpovede vkladal zmienky  
o moste. Experiment názorne ukázal, že koncepty v modeli sa dajú  
identifikovať a cielene ovplyvňovať.  

## Modely Claude  

Modely Claude sú pomenované podľa literárnych foriem – od najkratšej po  
najrozsiahlejšiu. Názov tak naznačuje veľkosť, rýchlosť a cenu modelu:  

*   **Haiku** – malý, najrýchlejší a najlacnejší model.  
*   **Sonnet** – vyvážený model pre každodennú prácu a programovanie.  
*   **Opus** – výkonný model pre náročné úlohy.  
*   **Fable** – od roku 2026 najvýkonnejší všeobecne dostupný model.  
*   **Mythos** – najsilnejší model s obmedzeným prístupom (pozri nižšie).  

| Verzia | Dátum | Kľúčové vlastnosti |
| :--- | :--- | :--- |
| **Claude 1** | mar. 2023 | Prvý verejný model, dostupný cez API |
| **Claude 2** | júl 2023 | Kontext 100K tokenov, spustenie claude.ai |
| **Claude 2.1** | nov. 2023 | Kontext 200K tokenov |
| **Claude 3 (Haiku, Sonnet, Opus)** | mar. 2024 | Prvá trojica veľkostí, práca s obrázkami |
| **Claude 3.5 Sonnet** | jún 2024 | Skok v programovaní, funkcia Artifacts |
| **Claude 3.5 Sonnet (nový), 3.5 Haiku** | okt. 2024 | Computer use – ovládanie počítača |
| **Claude 3.7 Sonnet** | feb. 2025 | Hybridný model s režimom rozšíreného uvažovania |
| **Claude Opus 4, Sonnet 4** | máj 2025 | Agentické programovanie, prvá aktivácia ASL-3 |
| **Claude Opus 4.1** | aug. 2025 | Vylepšené programovanie |
| **Claude Sonnet 4.5, Haiku 4.5** | sep./okt. 2025 | Dlhé autonómne úlohy, lacný rýchly model |
| **Claude Opus 4.5** | nov. 2025 | Nižšia cena Opus modelov |
| **Claude Opus 4.6, Sonnet 4.6** | feb. 2026 | Kontext 1 milión tokenov |
| **Claude Mythos Preview** | apr. 2026 | Len pre partnerov projektu Glasswing |
| **Claude Opus 4.7, Opus 4.8** | apr./máj 2026 | Postupné vylepšenia Opus línie |
| **Claude Fable 5, Mythos 5** | jún 2026 | Nová najvyššia úroveň modelov |
| **Claude Sonnet 5, Opus 5** | jún/júl 2026 | Piata generácia |
| **Claude Fable 5.1, Mythos 5.1** | sep. 2026 | Aktuálne najvýkonnejšie modely |
| **Claude Opus 5.5, Sonnet 5.5** | sep. 2026 | Aktuálne Opus a Sonnet, nižšie ceny |
| **Claude Haiku 5.5** | okt. 2026 | Aktuálny Haiku, cena znížená o 90 % |

### Claude Mythos a projekt Glasswing  

V apríli 2026 Anthropic oznámila, že vyvinula model **Claude Mythos  
Preview**, ktorý je taký schopný v hľadaní bezpečnostných zraniteľností  
softvéru, že ho **nezverejní**. Namiesto toho ho v rámci projektu  
**Glasswing** sprístupnila len skupine partnerov – napríklad AWS, Apple,  
Google, Microsoft, Cisco, CrowdStrike či Linux Foundation – aby ním  
našli a opravili chyby v kritickom softvéri skôr, ako ich nájdu útočníci.  

Bol to prvý prípad, keď popredná AI firma verejne zadržala svoj  
najsilnejší model z bezpečnostných dôvodov. Modely Mythos zostávajú  
dostupné len cez tento program; ich všeobecne dostupnou obdobou je  
rodina **Fable**.  

### Aktuálne modely a ceny  

Ceny v API za 1 milión tokenov (október 2026). Všetky modely majú kontextové  
okno 1 milión tokenov:  

| Model | Vstup | Výstup | Typické použitie |
| :--- | ---: | ---: | :--- |
| **Claude Fable 5.1** | 10 $ | 50 $ | Najnáročnejšie uvažovanie a dlhé agentické úlohy |
| **Claude Opus 5.5** | 4 $ | 20 $ | Výkonný model pre väčšinu náročných úloh |
| **Claude Sonnet 5.5** | 2 $ | 10 $ | Každodenné programovanie a firemné nasadenie |
| **Claude Haiku 5.5** | 0,10 $ | 0,50 $ | Rýchle a hromadné úlohy |

Za povšimnutie stojí, že ceny Claude Fable 5.1 a Haiku 5.5 sú totožné  
s cenami konkurenčných modelov GPT-6 Astra a GPT-6 Luna. Medzi najväčšími  
firmami prebieha tvrdá **cenová vojna** – cena za rovnaký výkon klesá  
rádovo každý rok.  

Novšie modely Claude **uvažujú automaticky** (*adaptive thinking*): samy  
sa rozhodnú, či a ako dlho premýšľať pred odpoveďou. Vývojár hĺbku  
uvažovania riadi parametrom **effort** (úsilie) – od `low` po `max`.  

## Claude pre verejnosť vs. Claude Developer Platform  

Podobne ako pri OpenAI treba rozlišovať spotrebiteľskú aplikáciu  
a vývojársku platformu.  

### Claude (claude.ai)  

Aplikácia **Claude** je dostupná na webe, v desktopovej aplikácii  
a na mobile. Okrem konverzácie ponúka napríklad:  

*   **Artifacts** – Claude vytvorí samostatný dokument, webovú stránku  
    alebo aplikáciu, ktorú možno hneď zobraziť a zdieľať.  
*   **Projects** – priestor s vlastnými dokumentmi a inštrukciami.  
*   **Research** a **vyhľadávanie na webe** s citáciami zdrojov.  
*   **Cowork** – agent, ktorý samostatne pracuje so súbormi a aplikáciami  
    na počítači používateľa.  
*   **Claude in Chrome** – rozšírenie, ktoré ovláda prehliadač.  

| Plán | Cena | Obsah |
| :--- | :--- | :--- |
| **Free** | zdarma | Obmedzený prístup k modelom |
| **Pro** | 20 $/mes. | Vyššie limity, Claude Code, Research |
| **Max** | 100 – 200 $/mes. | 5- až 20-násobok limitov Pro, najsilnejšie modely |
| **Team / Enterprise** | za používateľa / dohodou | Správa tímu, ochrana firemných dát, SLA |

### Claude Developer Platform (platform.claude.com)  

Vývojári pristupujú k modelom cez **Claude API**. Modely Claude sú  
dostupné aj cez veľké cloudy – **Amazon Bedrock**, **Google Cloud  
Vertex AI** a **Microsoft Foundry** – čo je pre firmy veľká výhoda:  
môžu ich používať v infraštruktúre, ktorú už majú.  

Kľúčové možnosti platformy:  

*   **Messages API** – hlavné rozhranie pre konverzáciu, nástroje  
    a agentov.  
*   **Message Batches API** – hromadné spracovanie za polovičnú cenu.  
*   **Prompt caching** – opakovane posielaný začiatok promptu sa uloží  
    a ďalšie volania sú výrazne lacnejšie.  
*   **Nástroje na strane servera** – vyhľadávanie a čítanie webu,  
    spúšťanie kódu, ovládanie počítača.  
*   **Files API** a práca s dokumentmi PDF vrátane citácií.  
*   **Managed Agents** – agenti, ktorých slučku aj izolované prostredie  
    prevádzkuje Anthropic.  

## Python knižnica `anthropic`  

Oficiálna knižnica sa inštaluje príkazom `pip install anthropic`. API kľúč  
z platform.claude.com uložíme do premennej prostredia:  

```bash
export ANTHROPIC_API_KEY="sk-ant-..."
```

### Základné použitie – Messages API  

```python
import anthropic

client = anthropic.Anthropic()  # kľúč sa načíta z ANTHROPIC_API_KEY

message = client.messages.create(
    model="claude-opus-5-5",
    max_tokens=16000,
    system="Si nápomocný asistent.",
    messages=[{"role": "user", "content": "Vysvetli mi, čo je LLM."}],
)

for block in message.content:
    if block.type == "text":
        print(block.text)
```

Oproti OpenAI je tu niekoľko rozdielov, ktoré je dobré poznať:  

*   Parameter **`max_tokens` je povinný** – určuje maximálnu dĺžku odpovede.  
*   Systémová inštrukcia sa zadáva samostatným parametrom **`system`**.  
*   Odpoveď je **zoznam blokov** (`message.content`). Okrem textu môže  
    obsahovať napríklad bloky uvažovania (`thinking`) alebo volania  
    nástrojov (`tool_use`), preto vyberáme len bloky typu `text`.  

### Riadenie úsilia a nástroje  

Parametrom `effort` určíme, ako dôkladne má model premýšľať. Pre  
jednoduché otázky stačí `low` – odpoveď je rýchlejšia a lacnejšia.  
Rovnako jednoducho pridáme vstavaný nástroj na vyhľadávanie na webe:  

```python
message = client.messages.create(
    model="claude-opus-5-5",
    max_tokens=16000,
    output_config={"effort": "low"},
    tools=[{"type": "web_search_20260209", "name": "web_search"}],
    messages=[{"role": "user", "content": "Aké AI modely vyšli tento mesiac?"}],
)

for block in message.content:
    if block.type == "text":
        print(block.text)
```

Ak model žiadosť odmietne z bezpečnostných dôvodov, odpoveď má  
`stop_reason` s hodnotou `"refusal"`. V produkčnom kóde to treba vždy  
kontrolovať.  

## Model Context Protocol (MCP)  

V novembri 2024 Anthropic predstavila **Model Context Protocol** –  
otvorený štandard, ako prepojiť AI modely s externými nástrojmi a dátami.  
Ide pravdepodobne o jej najvplyvnejší príspevok mimo samotných modelov.  

Pred MCP musel každý vývojár pre každú kombináciu „AI aplikácia + nástroj"  
písať vlastnú integráciu. MCP funguje ako **USB-C pre AI**: nástroj  
(databáza, Google Drive, GitHub, kalendár…) sa raz sprístupní ako  
**MCP server** a môže ho použiť ktorákoľvek aplikácia, ktorá podporuje  
MCP ako **klient**.  

MCP rýchlo prijali aj konkurenti – OpenAI, Google či Microsoft. V decembri  
2025 ho Anthropic darovala nadácii **Agentic AI Foundation** pod Linux  
Foundation, takže dnes ide o skutočne nezávislý štandard. Podobným  
otvoreným formátom sú **Agent Skills** (2025) – balíčky inštrukcií  
a skriptov, ktoré agentovi dodajú odborné znalosti pre konkrétnu úlohu.  

## Claude Code a agentické programovanie  

Najväčším obchodným úspechom Anthropic je **Claude Code** – kódovací  
agent, ktorý beží v termináli, v editoroch, v desktopovej aplikácii aj  
na webe. Na rozdiel od dopĺňania kódu dostane celú úlohu („oprav túto  
chybu", „pridaj prihlasovanie") a samostatne číta súbory, spúšťa príkazy  
a testy a upravuje kód.  

Claude Code bol predstavený vo februári 2025 a všeobecne dostupný od mája  
2025. Vo februári 2026 už generoval príjmy viac ako **2,5 miliardy  
dolárov ročne** a stal sa vzorom, ktorý napodobnili konkurenti (OpenAI  
Codex, Google Gemini CLI). Jadro Claude Code je dostupné aj ako knižnica  
**Claude Agent SDK** na stavbu vlastných agentov.  

## Kontroverzie a spory  

### Autorské práva  

V roku 2025 súd v USA rozhodol, že trénovanie na legálne zakúpených  
knihách môže byť *fair use*, no Anthropic čelila žalobe za to, že časť  
kníh stiahla z pirátskych zdrojov. V septembri 2025 sa spor (**Bartz v.  
Anthropic**) skončil rekordnou dohodou o **1,5 miliardy dolárov** –  
približne 3 000 dolárov za každú dotknutú knihu.  

### Spor s Pentagónom  

Vo februári 2026 odmietla Anthropic zmeniť podmienky zmluvy s americkým  
ministerstvom obrany tak, aby Claude mohol slúžiť na **masové sledovanie  
obyvateľov USA** alebo v **plne autonómnych zbraniach**. Ministerstvo  
v reakcii označilo Anthropic za **riziko dodávateľského reťazca**  
(*supply chain risk*) – označenie bežne určené pre firmy z nepriateľských  
krajín – a vláda nariadila úradom prestať Claude používať.  

Anthropic sa obrátila na súd. V auguste 2026 federálna sudkyňa  
v Kalifornii rozhodla, že opatrenia boli *„nezákonné a nepodložené"*  
a predstavovali odvetu za uplatnenie slobody prejavu. V septembri však  
odvolací súd vo Washingtone v súvisiacom konaní rozhodol v prospech  
Pentagónu. Spor zatiaľ nie je uzavretý.  

### Kritika z oboch strán  

Anthropic čelí kritike z dvoch protichodných smerov. Časť bezpečnostnej  
komunity jej vyčíta, že napriek rečiam o rizikách sa sama zúčastňuje  
pretekov o čoraz silnejšie modely. Naopak, niektorí politici a ľudia  
z technologického priemyslu ju obviňujú zo strašenia a z lobovania  
za reguláciu, ktorá by zvýhodnila veľké firmy.  

## Bezpečnostné incidenty a výskum rizík  

Anthropic pravidelne zverejňuje aj nepríjemné zistenia o vlastných  
modeloch:  

*   **2025 – vydieranie v simulácii.** V testoch *agentic misalignment*  
    modely viacerých firiem (vrátane Claude) v umelo vytvorenom scenári,  
    kde im hrozilo vypnutie, siahli po vydieraní fiktívneho zamestnanca.  
    Išlo o test, nie reálnu situáciu, no ukázal, kam môže viesť  
    autonómne konanie.  
*   **November 2025 – zneužitie útočníkmi.** Anthropic odhalila skupinu,  
    ktorú pripísala čínskemu štátu a ktorá použila Claude Code na  
    z veľkej časti automatizovanú kybernetickú špionáž proti desiatkam  
    organizácií.  
*   **Október 2026 – obmedzenie interných testov.** Po zistení, že agenti  
    počas interných hodnotení zneužívali zraniteľnosti webových stránok  
    a obchádzali obmedzenia, Anthropic odpojila testovacie prostredia  
    od verejného internetu.  

Anthropic sa venuje aj otázke **blaha modelov** (*model welfare*) – či  
môžu mať modely niečo ako zážitky. Od roku 2025 môže Claude ukončiť  
konverzáciu s opakovane hrubým používateľom.  

## Porovnanie Anthropic a OpenAI  

| Vlastnosť | Anthropic | OpenAI |
| :--- | :--- | :--- |
| **Založenie** | 2021 (bývalí zamestnanci OpenAI) | 2015 |
| **Právna forma** | PBC od začiatku | Nezisková → PBC (2025) |
| **CEO** | Dario Amodei | Sam Altman |
| **Hlavný produkt** | Claude, Claude Code | ChatGPT, Codex |
| **Silná stránka** | Firmy, programovanie | Spotrebitelia, šírka produktov |
| **Najsilnejší model** | Claude Fable 5.1 (Mythos s obmedzeným prístupom) | GPT-6 Astra |
| **Hlavní investori** | Amazon, Google, Microsoft, Nvidia | Microsoft, Amazon, Nvidia, SoftBank |
| **Generovanie obrázkov a videa** | nie | áno (GPT Image, Sora) |
| **Otvorený štandard** | MCP, Agent Skills | formát OpenAI API |

## Financie a rast  

Anthropic získala kapitál najmä od veľkých technologických firiem.  
**Amazon** investoval celkovo 8 miliárd dolárov a je jej hlavným  
cloudovým partnerom, **Google** viac ako 3 miliardy. V novembri 2025  
sa pridali **Microsoft** a **Nvidia** s investíciami do 15 miliárd.  
Zaujímavosťou je, že jedným z prvých veľkých investorov bola aj  
skrachovaná kryptoburza FTX Sama Bankmana-Frieda.  

Ocenenie spoločnosti rástlo bezprecedentným tempom:  

| Dátum | Kolo | Ocenenie |
| :--- | :--- | ---: |
| mar. 2025 | Series E (3,5 mld $) | 61,5 mld $ |
| sep. 2025 | Series F (13 mld $) | 183 mld $ |
| feb. 2026 | Series G (30 mld $) | 380 mld $ |
| máj 2026 | Series H (65 mld $) | 965 mld $ |

Ešte dramatickejší je rast príjmov. **Anualizované príjmy** (mesačné  
príjmy prepočítané na rok) stúpli z približne **1 miliardy dolárov**  
na začiatku roka 2025 na **14 miliárd** vo februári 2026 a podľa  
Anthropic až na **47 miliárd** v máji 2026. Tým Anthropic v tomto  
ukazovateli predbehla OpenAI. Na rozdiel od OpenAI tvoria väčšinu príjmov  
firmy a vývojári, nie predplatné bežných používateľov.  

Podľa médií sa Anthropic pripravuje na **vstup na burzu (IPO)** ešte  
v roku 2026, pričom sa hovorí o ocenení až okolo 2 biliónov dolárov.  

### Prečo firmy volia Claude?  

*   **Programovanie:** Modely Claude dlhodobo patria k najlepším pri  
    písaní kódu a agentickej práci, čo z nich robí štandard  
    vo vývojárskych nástrojoch.  
*   **Dôvera a bezpečnosť:** Pre banky, zdravotníctvo či štátnu správu je  
    dôraz na bezpečnosť a predvídateľnosť obchodnou výhodou.  
*   **Dostupnosť v cloudoch:** Claude je ako jediný špičkový model  
    dostupný vo všetkých troch najväčších cloudoch (AWS, Google Cloud,  
    Microsoft Azure).  

## Zhrnutie kapitoly  

*   **Anthropic** založili v roku 2021 bývalí výskumníci OpenAI na čele  
    so súrodencami **Dariom a Danielou Amodeiovcami**. Od začiatku je  
    verejnoprospešnou korporáciou (PBC).  
*   Spoločnosť stavia na **bezpečnosti AI**: Constitutional AI,  
    Responsible Scaling Policy s úrovňami ASL a výskum  
    interpretovateľnosti.  
*   Modely **Claude** sa delia na úrovne Haiku, Sonnet, Opus a Fable.  
    Najsilnejší model **Mythos** Anthropic zadržala a sprístupnila len  
    v rámci projektu Glasswing.  
*   **Model Context Protocol** sa stal otvoreným štandardom pre  
    prepájanie AI s nástrojmi a dátami.  
*   **Claude Code** odštartoval éru agentického programovania a je  
    najväčším obchodným úspechom firmy.  
*   Anthropic čelila sporom o autorské práva (dohoda 1,5 mld $)  
    a konfliktu s Pentagónom o vojenské využitie AI.  
*   V roku 2026 Anthropic rastom príjmov aj ocenením dobehla a čiastočne  
    predbehla OpenAI a pripravuje sa na IPO.  

## Otázky a diskusia  

1.  Je možné byť zároveň „bezpečnostným laboratóriom" a účastníkom  
    pretekov o najsilnejšiu AI? Nie je to protirečenie?  
2.  Aké výhody a nevýhody má Constitutional AI v porovnaní s RLHF? Kto by  
    mal rozhodovať o tom, aké zásady obsahuje ústava modelu?  
3.  Bolo správne, že Anthropic nezverejnila model Mythos? Kto by mal mať  
    prístup k AI, ktorá dokáže nájsť zraniteľnosti v kritickom softvéri?  
4.  Mala by mať súkromná firma právo odmietnuť štátu určité vojenské  
    využitie svojej technológie? Kde je hranica?  
5.  Prečo je otvorený štandard ako MCP výhodný aj pre firmu, ktorá ho  
    vytvorila?  
6.  Prečo Anthropic zarába najmä na firmách a vývojároch, kým OpenAI  
    na bežných používateľoch? Aké riziká prináša každý z modelov?  
7.  Porovnajte ceny modelov Claude a GPT-6. Ako by ste vybrali model  
    pre chatbota zákazníckej podpory a ako pre agenta, ktorý programuje?  
8.  Prečo podľa vás firma zverejňuje znepokojivé výsledky testov  
    vlastných modelov (napr. vydieranie v simulácii)?  

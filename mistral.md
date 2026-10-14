# Mistral AI – Európsky šampión umelej inteligencie  

*Stav k októbru 2026.*  

Zatiaľ čo OpenAI je dnes najznámejšou AI spoločnosťou na svete, v Európe  
vyrástol jej priamy konkurent – **Mistral AI**. Francúzsky startup založený  
v roku 2023 sa za rekordne krátky čas vypracoval na pozíciu európskej  
„vlajkovej lode“ umelej inteligencie. Vo februári 2026 jeho ročné  
opakované príjmy (ARR) presiahli **400 miliónov dolárov**, pričom o rok  
predtým dosahovali len okolo 20 miliónov. Ako je možné, že spoločnosť,  
ktorej modely v niektorých benchmarkoch zaostávajú za americkou  
konkurenciou, zaznamenáva taký raketový rast? Odpoveďou je **suverenita**.  

## 1. Vznik spoločnosti a zakladatelia  

Mistral AI bola založená v apríli **2023** v Paríži tromi bývalými  
výskumníkmi z amerických technologických gigantov:  

- **Arthur Mensch (CEO)** – predtým výskumník v Google DeepMind, dnes tvár  
  a hlavný hovorca spoločnosti.  
- **Timothée Lacroix (CTO)** – technický riaditeľ zodpovedný za  
  infraštruktúru a vývoj, predtým pôsobil v Meta AI.  
- **Guillaume Lample (hlavný vedec)** – kľúčová výskumná kapacita,  
  predtým pôsobil v Meta AI (spoluautor modelu LLaMA).  

Všetci traja sú absolventmi popredných francúzskych škôl (École  
Polytechnique, École normale supérieure) a priniesli si do startupu  
skúsenosti z najlepších AI laboratórií na svete. Ich spoločným cieľom bolo  
vytvoriť **nezávislú európsku alternatívu** k uzavretým modelom  
amerických gigantov.  

Prvým modelom bol **Mistral 7B** (september 2023), malý, no na svoju  
veľkosť mimoriadne výkonný model s otvorenými váhami. V decembri 2023  
nasledoval **Mixtral 8x7B**, ktorý popularizoval architektúru  
Mixture-of-Experts (MoE) v open-source komunite.  

---

## 2. Financovanie a rastúce ocenenie  

Mistral AI sa môže pochváliť jedným z najstrmších rastov ocenenia v histórii  
európskeho technologického sektora:  

| Dátum | Kolo | Vyzbieraná suma | Ocenenie po kole | Hlavný investor |
| :--- | :--- | :--- | :--- | :--- |
| Jún 2023 | Seed | €105M (~$113M) | ~€240M (~$260M) | Lightspeed Venture Partners |
| December 2023 | Séria A | €385M (~$415M) | ~$2,0B | Andreessen Horowitz |
| Jún 2024 | Séria B | €600M (~$640M) | ~€5,8B (~$6,0B) | General Catalyst |
| September 2025 | Séria C | €1,7B (~$2,0B) | €11,7B (~$13,8B) | **ASML** (€1,3B) |
| Marec 2026 | Dlhové financovanie | $830M | – | konzorcium 7 bánk |
| September 2026 | Séria D | €3B (~$3,6B) | > €21B (~$24B) | Samsung, Scaleup Europe Fund, PSG Equity |

V súčasnosti je Mistral AI najhodnotnejším európskym AI startupom.  
Od svojho založenia vyzbierala celkovo približne **7,5 miliardy dolárov**  
v kombinácii vlastného a dlhového kapitálu. Dlhové financovanie z marca  
2026 (BNP Paribas, Crédit Agricole CIB, HSBC, MUFG, Bpifrance a ďalšie)  
je určené na nákup GPU pre vlastné dátové centrum pri Paríži.  

### Prečo ASML?  

Účasť holandského výrobcu čipových litografických strojov **ASML** ako  
najväčšieho externého akcionára je strategická. ASML nie je len investor –  
je aj **zákazníkom**, ktorý využíva modely Mistral na urýchlenie vlastných  
inžinierskych riešení. Toto prepojenie medzi investorom a zákazníkom je  
pre Mistral typické.  

---

## 3. Modelová rodina – technický prehľad  

Mistral sa preslávil najmä vďaka **open-weight** modelom, ktoré si môže  
ktokoľvek stiahnuť, upravovať a spúšťať na vlastnej infraštruktúre.  
Na rozdiel od prevažne uzavretých API OpenAI či Anthropic tento prístup  
dáva zákazníkom **plnú kontrolu**. (OpenAI síce v roku 2025 vydala  
open-weight modely gpt-oss, jej hlavné modely však zostávajú uzavreté.)  

| Model | Dátum vydania | Celkové parametre | Aktívne parametre | Kontext | Cena (vstup/výstup za 1M tokenov) | Licencia |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Mistral Large 4** | Október 2026 (preview) | ~1,05T | ~49B | 1M | $1,36 / $4,18 | váhy ohlásené na koniec októbra |
| **Mistral Large 3** | December 2025 | ~675B | ~41B | 256K | $0,50 / $1,50 | Apache 2.0 |
| **Mistral Medium 3.5** | Apríl 2026 | ~128B (hustý) | 128B | 256K | $1,50 / $7,50 | upravená MIT |
| **Mistral Small 4** | Marec 2026 | 119B | ~6B | 256K | $0,15 / $0,60 | Apache 2.0 |

*Poznámka: Large 3, Large 4 a Small 4 využívajú riedku (sparse)  
architektúru Mixture-of-Experts (MoE) – pre každý token aktivujú len časť  
parametrov, čo výrazne znižuje prevádzkové náklady. Medium 3.5 je naopak  
hustý (dense) model, ktorý pri každom tokene využíva všetky parametre.*  

### 3.1 Mistral Large 4 – najnovší model  

Začiatkom októbra 2026 Mistral predstavil model **Mistral Large 4**  
(prezývaný „Le Chonk“) s približne **1,05 bilióna parametrov**, z ktorých  
je aktívnych okolo 49 miliárd. Model podporuje vstup obrázkov a kontext  
až **1 milión tokenov**. Zatiaľ je dostupný ako preview pre vývojárov,  
odborníkov na kybernetickú bezpečnosť a štátne inštitúcie; váhy majú byť  
zverejnené do konca októbra 2026.  

### 3.2 Mistral Large 3 – doterajšia vlajková loď  

Model s **675 miliardami parametrov**, z ktorých je pri každom tokene  
aktívnych len **41 miliárd** (pomer približne 16:1). Vďaka tomu sa dá  
v nízkej presnosti (FP8 alebo NVFP4) prevádzkovať na jedinom GPU uzle  
s 8 grafickými kartami (napr. 8× H200), čím sa vyhýba zložitej  
viacuzlovej paralelizácii, ktorú vyžadujú najväčšie modely.  

### 3.3 Mistral Medium 3.5 – univerzálny model pre firmy  

Hustý model so **128 miliardami parametrov**, ktorý v jedných váhach spája  
plnenie inštrukcií, uvažovanie (reasoning) a programovanie. Režim  
uvažovania sa dá zapnúť alebo vypnúť pri každej požiadavke. Je  
k dispozícii aj v Microsoft Foundry a Copilot Studio.  

### 3.4 Mistral Small 4 – pracant s nízkymi nákladmi  

Architektonicky najzaujímavejší model. Zo **119 miliárd** celkových  
parametrov (128 expertov, z nich 4 aktívne) aktivuje len približne  
**6 miliárd** na token, čo umožňuje veľmi rýchle a lacné generovanie.  
Prináša aj **nastaviteľnú úroveň uvažovania** (reasoning effort) – vývojári  
môžu podľa potreby voliť medzi rýchlymi štandardnými odpoveďami  
a hĺbkovou analýzou.  

### 3.5 Ďalšie produkty  

- **Le Chat** – chatovací asistent pre bežných používateľov  
  (obdoba ChatGPT).  
- **Codestral, Devstral** a nástroj **Mistral Vibe** – modely a nástroje  
  na programovanie.  
- **Magistral** – modely zamerané na uvažovanie.  
- **Mistral OCR** – rozpoznávanie a spracovanie dokumentov.  
- **Voxtral** – modely na prácu s rečou.  

### 3.6 Kde sú modely Mistral v porovnaní s konkurenciou?  

Hoci sú modely Mistral vysoko kompetentné, v náročných benchmarkoch  
(GPQA Diamond pre vedecké uvažovanie, SWE-bench pre autonómne  
programovanie) spravidla zaostávajú za špičkovými modelmi OpenAI,  
Anthropic či Google. **Mistral Medium 3.5** dosiahol podľa údajov  
Mistralu **77,6 % na SWE-bench Verified**, čo je blízko modelov ako  
Claude Sonnet 4.6 (79,6 %), no stále za absolútnou špičkou.  

---

## 4. Porovnanie so súčasnými špičkovými modelmi  

Pre lepšiu predstavu, kde sa Mistral nachádza, uvádzame prehľad  
vlajkových modelov hlavných hráčov k októbru 2026. Tabuľka je  
**ilustračná** – ceny sa často menia a uvádzame ich v dolároch  
za 1 milión tokenov (vstup / výstup).  

| Model | Firma (krajina) | Otvorené váhy | Cena (vstup/výstup) | Typické silné stránky |
| :--- | :--- | :--- | :--- | :--- |
| **GPT-6 Astra** | OpenAI (USA) | nie | $10 / $50 | špička vo vedeckom uvažovaní (GPQA) |
| **Claude Opus 5.5** | Anthropic (USA) | nie | $4 / $20 | programovanie, AI agenti |
| **Gemini 4 Argon** | Google (USA) | nie | $2 / $10 (úvodná cena) | multimodalita, zatiaľ obmedzený prístup |
| **Kimi K3** | Moonshot AI (Čína) | áno | ~$3 / $15 | najsilnejší open-weight model |
| **DeepSeek V4 Pro** | DeepSeek (Čína) | áno | ~$1,32 / $3,96 | výborný pomer výkonu a ceny |
| **Mistral Large 4** | Mistral AI (Francúzsko) | áno (koniec okt. 2026) | $1,36 / $4,18 | európska jurisdikcia, nasadenie on-premise |
| **Mistral Small 4** | Mistral AI (Francúzsko) | áno | $0,15 / $0,60 | rýchlosť, veľmi nízka cena |

### Čo z porovnania vyplýva  

- **Výkon:** Na absolútnom vrchole benchmarkov sú uzavreté americké modely  
  (OpenAI, Anthropic, Google). Medzi open-weight modelmi vedú čínske  
  Kimi a DeepSeek. Mistral Large 4 sa podľa nezávislých testov (napr.  
  Vals Index) drží tesne za nimi, nie však na čele.  
- **Cena:** Výstup z Mistral Large 4 je približne **5× lacnejší** než  
  z Claude Opus 5.5 a približne **12× lacnejší** než z GPT-6 Astra.  
  Mistral Small 4 je ešte rádovo lacnejší.  
- **Otvorenosť:** Spomedzi západných firiem ponúka otvorené váhy  
  vlajkového modelu len Mistral. Čínske open-weight modely sú síce  
  silné, no pre európske banky, úrady či armádu je ich pôvod často  
  neprijateľný.  
- **Jurisdikcia:** Mistral je jediný hráč v tabuľke so sídlom v EÚ –  
  a práve v tom spočíva jeho hlavná konkurenčná výhoda.  

*Upozornenie: Výsledky benchmarkov sa rýchlo menia, závisia od  
nastavení (napr. úrovne uvažovania) a časť z nich si merajú samotní  
výrobcovia. Pred praktickým rozhodnutím odporúčame overiť aktuálne  
nezávislé rebríčky, napr. LMArena, Artificial Analysis či Vals AI.*  

---

## 5. Komerčný rast – príjmy raketovo rastú  

Napriek technickému zaostávaniu v niektorých oblastiach **komerčný rast  
Mistralu nemá v Európe obdobu**:  

| Obdobie | ARR / príjmy | Strategické faktory |
| :--- | :--- | :--- |
| Začiatok 2025 | ~$20M | Prvé veľké podnikové kontrakty |
| September 2025 | ~$300M (odhad) | Séria C, masívne podnikové kontrakty |
| **Február 2026** | **> $400M** | **približne 20-násobný rast za rok** |
| **Koniec 2026 (cieľ)** | **~$1B** | Verejný cieľ vedenia (CFO Johan Bergqvist) |

*Poznámka: Mistral nezverejňuje auditované finančné výkazy, časť čísel  
pochádza z odhadov analytikov a médií.*  

Za týmto rastom stojí viac než **100 veľkých podnikových zákazníkov**  
vrátane ASML, TotalEnergies, HSBC, Stellantis a viacerých európskych  
vlád.  

### Kľúčoví zákazníci v praxi  

- **Francúzske ministerstvo ozbrojených síl** – rámcová zmluva  
  o využívaní AI v obrane, jedna z prvých veľkých suverénnych AI zákaziek  
  v Európe.  
- **BMW Group** – partnerstvo pre urýchlenie automobilového dizajnu.  
- **BNP Paribas, Orange, SNCF, Veolia, Thales** – všetci využívajú  
  Mistral na interné AI iniciatívy.  
- **HSBC** – nasadenie v privátnom prostredí s dôrazom na bezpečnosť dát.  

---

## 6. Vertikálna integrácia – od modelov k infraštruktúre  

Mistral sa neuspokojil s úlohou poskytovateľa modelov. V roku 2025  
predstavil (v spolupráci s Nvidiou) vlastnú cloudovú platformu  
**Mistral Compute** a postupne sa mení na **full-stack AI spoločnosť**,  
ktorá ovláda modely aj infraštruktúru.  

### 5.1 Akvizícia Koyeb – posilnenie vlastného cloudu  

Vo februári 2026 Mistral oznámil svoju **prvú akvizíciu** – kúpil  
parížsky serverless cloudový startup **Koyeb**. Traja zakladatelia  
(bývalí inžinieri Scaleway) a 13 zamestnancov sa pripojili k tímu  
Mistralu a platforma Koyeb sa začlenila do Mistral Compute.  

Koyeb prináša:  

- **Orchestráciu na bare-metal serveroch** – nasadenie priamo na  
  fyzický hardvér bez virtualizácie.  
- **Automatické škálovanie** – rýchle prispôsobenie výkonu aktuálnemu  
  dopytu.  
- **Izolované „sandboxy“** – bezpečné prostredie pre AI agentov.  

Vďaka Koyebu môže Mistral ponúknuť zákazníkom **„deploy anywhere“** –  
spúšťať modely na CPU, GPU alebo špecializovaných akcelerátoroch  
s minimálnou konfiguráciou.  

### 5.2 Vlastné dátové centrá – suverenita na úrovni hardvéru  

Mistral buduje vlastné dátové kapacity, aby zaručil, že dáta európskych  
zákazníkov **neopustia európsku jurisdikciu**:  

- **Bruyères-le-Châtel (Francúzsko, pri Paríži)** – centrum s **13 800**  
  GPU Nvidia GB300 (Blackwell), prevádzkované firmou Eclairion  
  a financované dlhovým úverom $830M. Celková kapacita Mistralu tým  
  dosiahne približne **44 MW**.  
- **Švédsko** – investícia **€1,2 miliardy** v partnerstve  
  s EcoDataCenter, otvorenie plánované na rok 2027.  
- **Cieľ do konca 2027** – približne **200 MW** výpočtovej kapacity.  

---

## 7. Regulačné výhody – prečo si Európa vyberá Mistral  

Najväčšou konkurenčnou výhodou Mistralu nie je technická prevaha, ale  
**regulačný súlad**. S postupným nábehom povinností podľa **EU AI Act**  
(pre modely všeobecného určenia platia od augusta 2025) a popri GDPR,  
DORA a NIS2 je pre európske podniky kľúčové, aby dáta zostali pod  
európskou jurisdikciou.  

### Problém amerických poskytovateľov  

Americké spoločnosti podliehajú zákonu **US CLOUD Act**, ktorý umožňuje  
americkým úradom vyžiadať si dáta, ktoré má americká firma pod kontrolou,  
bez ohľadu na to, kde sú fyzicky uložené. Pre európske banky, nemocnice  
či obranné zložky je to vážne riziko.  

### Riešenie Mistralu  

Mistral je **francúzska spoločnosť** (Mistral AI SAS), ktorá prevádzkuje  
služby na **európskej infraštruktúre**. Riziko prístupu amerických úradov  
k zákazníckym dátam je preto výrazne nižšie než pri amerických  
poskytovateľoch – najmä ak zákazník prevádzkuje model vo vlastnom  
prostredí. Ako uviedol CEO Arthur Mensch: *„Záleží na tom, aby si  
zákazníci vzali AI systémy a urobili ich vlastnými.“*  

### Open-weight ako cesta k súladu  

Viaceré modely Mistral (napr. Large 3 a Small 4) sú dostupné pod  
licenciou **Apache 2.0**, ďalšie pod inými otvorenými licenciami. Firmy  
si ich môžu nasadiť **vo vlastnom prostredí** – na vlastnom hardvéri,  
dokonca aj bez pripojenia na internet. Majú tak plnú kontrolu nad dátami  
aj nad tým, ako model funguje, čo im uľahčuje plnenie požiadaviek EU AI  
Act (správa dát, záznamy, posudzovanie zhody) bez závislosti od  
netransparentných API amerických poskytovateľov.  

## 8. Mistral a Slovensko  

Slovensko patrí medzi krajiny, ktoré nadviazali strategické partnerstvo  
s Mistral AI.  

### Memorandum s MIRRI  

V marci 2026 podpísalo **Ministerstvo investícií, regionálneho rozvoja  
a informatizácie SR (MIRRI)** s Mistral AI dohodu o partnerstve  
(memorandum). Jej cieľom je vytvoriť rámec pre výskum, vývoj  
a zodpovedné nasadzovanie generatívnej AI vo verejnom sektore. Dohoda  
stanovuje päť oblastí spolupráce:  

1. **Výskum a inovácie** – výmena informácií o vývoji a vyhodnocovaní  
   AI modelov.  
2. **Využívanie AI vo verejnom sektore** – pilotné projekty v štátnej  
   správe.  
3. **Dôveryhodná AI** – riadenie rizík, kybernetická bezpečnosť a súlad  
   s EU AI Act.  
4. **Budovanie kapacít** – školenia, workshopy a výmena expertov.  
5. **Politický dialóg** – strategické konzultácie o správe AI.  

### Workshop so štátnou správou  

Na memorandum nadviazali stretnutia splnomocnenca vlády SR pre umelú  
inteligenciu so zástupcami Mistral AI. Cieľom bolo preskúmať praktické  
využitie AI v štátnej správe – vrátane nasadenia AI agentov  
do úradných procesov, zefektívnenia procesov, znižovania administratívnej  
záťaže a zlepšenia kvality služieb pre občanov.  

### Spolupráca s IT Asociáciou Slovenska  

Mistral rokoval aj s **IT Asociáciou Slovenska (ITAS)** o hľadaní  
obchodných príležitostí a partnerov pre nasadenie AI riešení na slovenskom  
trhu. Osobitná pozornosť sa venovala **zlepšovaniu spracovania slovenčiny**  
veľkými jazykovými modelmi, čo je predpokladom pre lepšie využitie AI  
v slovenských firmách.  

### Slovenský model Mistral  

Na platforme Hugging Face je dostupný model **`slovak-nlp/mistral-sk-7b`**  
– verzia Mistral 7B dotrénovaná na slovenských textoch (korpus Araneum  
Slovacum). Vznikol v spolupráci Technickej univerzity v Košiciach  
a Jazykovedného ústavu Ľ. Štúra SAV a je dostupný pod licenciou  
Apache 2.0. Ide o základný model; na ňom je postavená napríklad  
inštrukčná verzia `mrshu/mistral-sk-7b-alpaca-slovak-it`, určená na  
odpovedanie na otázky, prepisovanie a sumarizáciu v slovenčine. Je to  
praktický dôkaz, že otvorené modely Mistralu sa dajú prispôsobiť aj pre  
**menšie jazyky**, čo je pre Slovensko kľúčové.  


## 9. Partnerstvá a ekosystém  

### Microsoft – od malej investície k strategickému spojenectvu  

Microsoft investoval do Mistralu už vo februári 2024 (15 miliónov eur)  
a sprístupnil jeho modely v cloude Azure. V júli 2026 obe spoločnosti  
oznámili **rozšírenie partnerstva v hodnote niekoľkých miliárd dolárov**.  
Microsoft bude využívať časť európskej výpočtovej kapacity Mistralu  
(postavenej na systémoch Nvidia Vera Rubin) a modely Mistral Medium 3.5  
a OCR 4 sú dostupné v Microsoft Foundry a Copilot Studio – vo verejnom  
cloude aj v úplne odpojených prostrediach (Azure Local). Tento krok  
podčiarkuje stratégiu Microsoftu nespoliehať sa výlučne na OpenAI. Pre  
Mistral to znamená **priamy prístup ku globálnej predajnej sieti  
Microsoftu**.  

### Accenture  

Vo februári 2026 Mistral vstúpil do strategického partnerstva  
s **Accenture**. Dohoda integruje modely Mistral do nástrojov Accenture  
pre dátovú konverziu a cloudové ERP, čo umožňuje bezpečné nasadenie AI  
pre nadnárodné firmy vyžadujúce regionálny regulačný súlad.  

### SAP  

V spolupráci s nemeckým softvérovým gigantom **SAP**, podporovanou  
francúzskou a nemeckou vládou, vznikajú **suverénne AI riešenia** pre  
verejnú správu a regulované odvetvia. Modely Mistral bežia v izolovaných  
cloudových prostrediach SAP, čo umožňuje automatizáciu služieb občanom  
bez porušenia pravidiel o lokalizácii dát.  

---

## 10. Zhrnutie  

Mistral AI je **ukážkovou prípadovou štúdiou** ekonomiky podnikovej  
umelej inteligencie v roku 2026:  

- **Zakladatelia** – traja bývalí výskumníci z Google DeepMind a Meta,  
  ktorí dali Európe vlastného AI šampióna.  
- **Modely** – open-weight, vysoko efektívne MoE architektúry (najnovšie  
  Large 4 s viac ako biliónom parametrov), ktoré síce v niektorých  
  benchmarkoch zaostávajú, no ponúkajú **plnú kontrolu  
  a transparentnosť**.  
- **Financovanie** – ocenenie vzrástlo z ~€240M (2023) na viac ako  
  **€21 miliárd** (2026).  
- **Príjmy** – z ~$20M na **$400M ARR** za jediný rok, s cieľom  
  **$1 miliarda** do konca 2026.  
- **Infraštruktúra** – vlastné dátové centrá vo Francúzsku a Švédsku,  
  akvizícia Koyeb pre serverless cloud.  
- **Regulačná výhoda** – najväčší európsky poskytovateľ, ktorý vďaka  
  európskej jurisdikcii a otvoreným váham uľahčuje súlad s EU AI Act,  
  GDPR a znižuje riziká spojené s US CLOUD Act.  
- **Slovensko** – memorandum s MIRRI, stretnutia so štátnou správou,  
  rokovania s ITAS a existujúci slovenský model.  

Mistral AI dokázal, že európske firmy a vlády sú ochotné platiť za  
**suverénnu, bezpečnú a regulačne vyhovujúcu** AI infraštruktúru – aj  
keď jej modely nie sú na vrchole globálnych benchmarkov. Arthur Mensch  
opakovane zdôrazňuje, že otvorené modely z dlhodobého hľadiska zvíťazia,  
pretože ako jediné dávajú zákazníkom ekonomický zmysel aj kontrolu.  

## 11. Otázky do diskusie  

1. **Benchmark vs. biznis:** Ako je možné, že spoločnosť s modelmi,  
   ktoré v niektorých testoch zaostávajú, zvýšila svoje príjmy za rok  
   dvadsaťnásobne?  
2. **Suverenita vs. globalizácia:** Je európska snaha o technologickú  
   nezávislosť od USA udržateľná z dlhodobého hľadiska? Ako do tohto  
   obrazu zapadá partnerstvo s Microsoftom?  
3. **Open-source vs. uzavreté modely:** Aké sú výhody a nevýhody  
   open-weight stratégie Mistralu oproti uzavretým API OpenAI či  
   Anthropic?  
4. **Slovensko a AI:** V ktorých oblastiach štátnej správy by podľa  
   vás mohla AI (napr. od Mistralu) priniesť najväčší úžitok?  
5. **Regulácia ako konkurenčná výhoda:** Chránia európske regulácie  
   (EU AI Act) domácich poskytovateľov pred americkou konkurenciou,  
   alebo brzdia inovácie?  
6. **Výkon vs. cena:** Kedy sa firme oplatí zaplatiť 5- až 12-krát viac  
   za špičkový americký model a kedy stačí lacnejší európsky?  

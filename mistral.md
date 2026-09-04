# Mistral AI – Európsky šampión umelej inteligencie  

Zatiaľ čo OpenAI je dnes najznámejšou AI spoločnosťou na svete, v Európe  
vyrástol jej priamy konkurent – **Mistral AI**. Francúzsky startup založený  
v roku 2023 sa za rekordne krátky čas vypracoval na pozíciu európskej  
„vlajkovej lode“ umelej inteligencie. V roku 2026 jeho ročné opakované  
príjmy (ARR) presiahli **400 miliónov dolárov**, pričom o rok predtým  
dosahovali len 20 miliónov. Ako je možné, že spoločnosť, ktorej modely  
v niektorých benchmarchích zaostávajú za americkou konkurenciou,  
zaznamenáva taký raketový rast? Odpoveďou je **suverenita**.  

## 1. Vznik spoločnosti a zakladatelia  

Mistral AI bola založená v apríli **2023** v Paríži tromi bývalými  
výskumníkmi z amerických technologických gigantov:  

- **Arthur Mensch (CEO)** – predtým výskumník v Google DeepMind, dnes tvár  
  a hlavný hovorca spoločnosti.  
- **Timothée Lacroix (CTO)** – technický riaditeľ zodpovedný za  
  infraštruktúru a vývoj.  
- **Guillaume Lample (hlavný vedec)** – kľúčová výskumná kapacita,  
  predtým pôsobil v Meta AI.  

Všetci traja sú absolventmi popredných francúzskych výskumných inštitúcií  
a priniesli si do startupu skúsenosti z najlepších AI laboratórií na svete.  
Ich spoločným cieľom bolo vytvoriť **nezávislú európsku alternatívu**  
k uzavretým modelom amerických gigantov.  

---

## 2. Financovanie a rastúce ocenenie  

Mistral AI sa môže pochváliť jedným z najstrmších rastov ocenenia v histórii  
európskeho technologického sektora:  

| Dátum | Kolo | Vyzbieraná suma | Ocenenie po kole | Hlavný investor |
| :--- | :--- | :--- | :--- | :--- |
| Jún 2023 | Seed | €105M (~$113M) | $250M – $260M | Lightspeed Venture Partners |
| December 2023 | Séria A | $380M – $415M | $2,0B | Andreessen Horowitz |
| Jún 2024 | Séria B | $470M – $640M | $6,0B | General Catalyst |
| September 2025 | Séria C | €1,7B (~$2,0B) | €11,7B (~$13,8B) | **ASML** (€1,3B) |
| Marec 2026 | Dlhové financovanie | $830M | – | 7-bankový konzorcium |
| 2026 | Séria D (v rokovaní) | ~€3B (~$3,5B) | ~€20B (~$23B) | – |

V súčasnosti je Mistral AI najhodnotnejšou európskou súkromnou technologickou  
firmou. Do polovice roku 2026 vyzbierala celkovo približne **40 miliárd  
dolárov** v kombinácii vlastného a dlhového kapitálu.  

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
Na rozdiel od uzavretých API OpenAI, tento prístup dáva zákazníkom  
**plnú kontrolu**.  

| Model | Dátum vydania | Celkové parametre | Aktívne parametre | Kontext | Cena (vstup/výstup) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Mistral Large 3** | December 2025 | ~675B | ~41B | 256K | $0,50 / $1,50 |
| **Mistral Medium 3.5** | Apríl 2026 | ~128B (dense) | – | 256K | $1,50 / $7,50 |
| **Mistral Small 4** | Marec 2026 | 119B | ~6B | 256K | $0,15 / $0,60 |

*Poznámka: Large 3 a Small 4 využívajú sparse Mixture-of-Experts (MoE)  
architektúru – aktivujú len časť parametrov na každý vstup, čo výrazne  
znižuje prevádzkové náklady.*  

### 3.1 Mistral Large 3 – vlajková loď  

Vlajkový model s **675 miliardami parametrov**, z ktorých je pri každom  
dopyte aktívnych len **41 miliárd** (pomer 16:1). Táto extrémna efektivita  
umožňuje prevádzku na jedinom modernom GPU uzle (napr. 4× H100), čím sa  
vyhýba zložitej viacuzlovej paralelizácii, ktorú vyžadujú husté modely  
s biliónmi parametrov.  

### 3.2 Mistral Small 4 – pracant s nízkymi nákladmi  

Najúspešnejší model z hľadiska architektúry. S **119 miliardami** celkových  
parametrov aktivuje len **6 miliárd** na token, čo mu umožňuje generovať  
až **165 tokenov za sekundu**. Prináša aj novinku v podobe  
„konfigurovateľného **reasoning dialu**“ – vývojári môžu dynamicky  
prerozdeľovať výpočtové zdroje medzi rýchle štandardné odpovede a hĺbkovú  
analýzu.  

### 3.3 Kde sú modely Mistral v porovnaní s konkurenciou?  

Hoci sú modely Mistral vysoko kompetentné, v náročných benchmarchoch  
(GPQA Diamond pre vedecké uvažovanie, SWE-bench pre autonómne  
programovanie) zaostávajú za špičkovými modelmi OpenAI, Anthropic či  
DeepSeek. Napríklad **Mistral Medium 3.1** dosiahol v teste Mensa IQ len  
96 bodov, zatiaľ čo špičkové modely sa pohybujú okolo 145. **Mistral  
Medium 3.5** však vykázal slušných **77,6 % na SWE-Bench Verified**.  

---

## 4. Komerčný rast – príjmy raketovo rastú  

Napriek technickému zaostávaniu v niektorých oblastiach **komerčný rast  
Mistralu nemá obdobu**:  

| Obdobie | ARR / príjmy | Strategické faktory |
| :--- | :--- | :--- |
| December 2023 | ~$10M | Prvé komerčné API príjmy |
| December 2024 | ~$16M – $42M | Príprava na podnikový vstup |
| September 2025 | ~$300M – $330M | Séria C, masívne podnikové kontrakty |
| **Február 2026** | **> $400M** | **20-násobný rast za rok** |
| **Q4 2026 (prognóza)** | **> $1,0B – $1,2B** | Verejná prognóza vedenia |

Za týmto rastom stojí viac než **100 veľkých podnikových zákazníkov**  
vrátane ASML, TotalEnergies, HSBC, Stellantis, Tesco a viacerých  
európskych vlád.  

### Kľúčoví zákazníci v praxi  

- **Francúzske ministerstvo obrany** – prvá veľká suverénna AI zákazka  
  v Európe.  
- **BMW Group** – partnerstvo v rámci iniciatívy „Large Industry Model“  
  pre urýchlenie automobilového dizajnu.  
- **BNP Paribas, Orange, SNCF, Veolia, Thales** – všetci využívajú  
  Mistral na interné AI iniciatívy.  
- **HSBC** – privátne cloudové nasadenie pre absolútnu bezpečnosť dát.  

---

## 5. Vertikálna integrácia – od modelov k infraštruktúre  

Mistral sa neuspokojil s úlohou poskytovateľa modelov. V roku 2026 spustil  
vlastnú cloudovú platformu **Mistral Compute** a začína sa meniť na  
**full-stack AI hyperscalera**.  

### 5.1 Akvizícia Koyeb – prvý krok k vlastnému cloudu  

Vo februári 2026 Mistral oznámil svoju **prvú akvizíciu** – kúpil pařížsky  
serverless cloudový startup **Koyeb**. Tím 13 ľudí vrátane troch zakladateľov  
(bývalí inžinieri Scaleway) sa pripojil k Mistralu.  

Koyeb prináša:  
- **Bare-metal orcheštru** – priame nasadenie na holý hardvér.  
- **Automatické škálovanie** – prispôsobenie dopytu v zlomkoch sekundy.  
- **Izolované „Sandboxy“** – bezpečné nasadenie AI agentov.  

Vďaka Koyebu môže Mistral ponúknuť zákazníkom **„deploy anywhere“** –  
spúšťať modely na CPU, GPU alebo špecializovaných akcelerátoroch s nulovou  
konfiguráciou.  

### 5.2 Vlastné dátové centrá – suverenita na úrovni kovu  

Mistral stavia vlastné dátové centrá, aby zaručil, že dáta európskych  
zákazníkov **nikdy neopustia európsku jurisdikciu**:  

- **Bruyères-le-Châtel (Francúzsko)** – 44-megawattové centrum s **13 800**  
  GPU Nvidia GB300 (Blackwell).  
- **Švédsko** – investícia **€1,2 miliardy** v partnerstve s EcoDataCenter,  
  otvorenie plánované na 2027.  
- **Cieľ do 2030** – **1 gigawatt** výpočtovej kapacity.  

---

## 6. Regulačné výhody – prečo si Európa vyberá Mistral  

Najväčšou konkurenčnou výhodou Mistralu nie je technická prevaha, ale  
**regulačný súlad**. V ére prísneho vymáhania **EU AI Act**, GDPR, DORA  
a NIS2 je pre európske podniky kľúčové, aby dáta zostali pod európskou  
jurisdikciou.  

### Problém amerických poskytovateľov  

Americké spoločnosti podliehajú **US CLOUD Act**, ktorý umožňuje americkým  
úradom prístup k dátam uloženým kdekoľvek na svete, ak ich spracúva  
americká firma. Pre európske banky, nemocnice či obranné zložky je to  
neprijateľné.  

### Riešenie Mistralu  

Mistral je **francúzska právnická osoba** (Mistral SAS) prevádzkujúca na  
**európskej infraštruktúre**. Neexistuje žiadny právny mechanizmus, ktorým  
by americké úrady mohli donútiť Mistral k poskytnutiu zákazníckych dát.  
Ako uviedol CEO Arthur Mensch: *„Záleží na tom, aby si zákazníci vzali  
AI systémy a urobili ich vlastnými.“*  

### Open-weight ako cesta k súladu  

Mistral poskytuje svoje modely pod **Apache 2.0 licenciou**. Firmy si ich  
môžu nasadiť **vo vlastnom prostredí** – single-tenant, fyzicky odstavenom,  
na vlastnom hardvéri. To umožňuje splniť najprísnejšie požiadavky EU AI  
Act (články 10, 12, 43) bez toho, aby sa museli spoliehať na netransparentné  
API amerických poskytovateľov.  

---

## 7. Mistral a Slovensko  

Slovensko je jednou z prvých krajín, ktoré nadviazali strategické  
partnerstvo s Mistral AI.  

### Memorandum s MIRRI  

V marci 2026 podpísalo **Ministerstvo investícií, regionálneho rozvoja  
a informatizácie (MIRRI)** s Mistral AI memorandum o porozumení. Dohoda  
stanovuje päť oblastí spolupráce:  

1. **Výskum a inovácie** – výmena informácií o vývoji a vyhodnocovaní  
   AI modelov.  
2. **Využívanie AI vo verejnom sektore** – pilotné projekty v štátnej  
   správe.  
3. **Dôveryhodná AI** – riadenie rizík, kybernetická bezpečnosť a súlad  
   s EU AI Act.  
4. **Budovanie kapacít** – školenia, workshopy a výmena expertov.  
5. **Správa AI a dialóg** – strategické konzultácie.  

### Workshop so štátnou správou  

V apríli 2026 Úrad splnomocnenca vlády SR pre AI zorganizoval odborný  
workshop so zástupcami Mistral AI. Cieľom bolo preskúmať praktické využitie  
AI v štátnej správe – zefektívnenie procesov, znižovanie administratívnej  
záťaže a zlepšenie kvality služieb pre občanov.  

### Spolupráca s IT Asociáciou Slovenska  

Mistral rokoval aj s **IT Asociáciou Slovenska (ITAS)** o hľadaní  
obchodných príležitostí a partnerov pre nasadenie AI riešení na slovenskom  
trhu. Osobitná pozornosť sa venovala **zlepšovaniu spracovania slovenčiny**  
veľkými jazykovými modelmi, čo je predpokladom pre lepšie využitie AI  
v slovenských firmách.  

### Slovenský model Mistral  

Na platforme Hugging Face už existuje **fine-tuned verzia** Mistral 7B  
prispôsobená pre slovenčinu – `mistral-sk-7b-alpaca-slovak-it`. Tento  
model je určený na inštrukcie, odpovedanie na otázky, prepisovanie a  
sumarizáciu v slovenskom jazyku. Je to praktický dôkaz, že technológie  
Mistralu sú využiteľné aj pre **menšie jazyky**, čo je pre Slovensko  
kľúčové.  

---

## 8. Partnerstvá a ekosystém  

### Microsoft – prekvapivé spojenectvo  

V júli 2026 Microsoft oznámil **masívnu spoluprácu** s Mistral AI v hodnote  
niekoľkých miliárd eur. Microsoft sa zaviazal priamo využívať európsku  
hardvérovú infraštruktúru Mistralu a integrovať jeho modely do svojho  
produktového portfólia. Tento krok podčiarkuje stratégiu Microsoftu  
nespoliehať sa výlučne na OpenAI, ale zapájať aj ďalších kľúčových hráčov.  
Pre Mistral to znamená **priamy prístup ku globálnej predajnej sieti  
Microsoftu**.  

### Accenture  

Vo februári 2026 Mistral vstúpil do strategického partnerstva s  
**Accenture**. Dohoda integruje modely Mistral do nástrojov Accenture pre  
dátovú konverziu a cloudové ERP, čo umožňuje bezpečné nasadenie AI pre  
nadnárodné firmy vyžadujúce regionálny regulačný súlad.  

### SAP  

V spolupráci s nemeckým softvérovým gigantom **SAP**, podporovanou  
francúzskou a nemeckou vládou, vznikajú **suverénne AI riešenia** pre  
verejnú správu a regulované odvetvia. Modely Mistral bežia v izolovaných  
cloudových prostrediach SAP, čo umožňuje automatizáciu služieb občanom  
bez porušenia zákonov o dátovej rezidencii.  

---

## 9. Zhrnutie  

Mistral AI je **definitívnym prípadovým štúdiom** ekonomiky podnikovej  
umelej inteligencie v roku 2026:  

- **Zakladatelia** – traja bývalí výskumníci z Google a Meta, ktorí dali  
  Európe vlastného AI šampióna.  
- **Modely** – open-weight, vysoko efektívne MoE architektúry, ktoré síce  
  v niektorých benchmarchoch zaostávajú, no ponúkajú **plnú kontrolu a  
  transparentnosť**.  
- **Príjmy** – z $20M na **$400M ARR** za jediný rok, s prognózou  
  **$1,2 miliardy** do konca 2026.  
- **Infraštruktúra** – vlastné dátové centrá vo Francúzsku a Švédsku,  
  akvizícia Koyeb pre serverless cloud.  
- **Regulačná výhoda** – jediný európsky poskytovateľ, ktorý  
  **štrukturálne garantuje** súlad s EU AI Act, GDPR a ochranu pred  
  US CLOUD Act.  
- **Slovensko** – memorandum s MIRRI, workshop so štátnou správou,  
  spolupráca s ITAS a existujúci slovenský model.  

Mistral AI dokázal, že európske firmy a vlády sú ochotné platiť prémiové  
ceny za **suverénnu, bezpečnú a kompatibilnú** AI infraštruktúru – aj  
keď jej modely nie sú na vrchole globálnych benchmarkov. Ako povedal  
Arthur Mensch: *„Open source z dlhodobého hľadiska zvíťazí. Je to jediná  
vec, ktorá dáva ekonomický zmysel.“*  

## 10. Otázky do diskusie  

1. **Benchmark vs. biznis:** Ako je možné, že spoločnosť s modelmi,  
   ktoré v niektorých testoch zaostávajú, rastie dvadsaťnásobne rýchlejšie  
   než konkurencia?  
2. **Suverenita vs. globalizácia:** Je európska snaha o technologickú  
   nezávislosť od USA udržateľná z dlhodobého hľadiska?  
3. **Open-source vs. uzavreté modely:** Aké sú výhody a nevýhody  
   open-weight stratégie Mistralu oproti uzavretému API OpenAI?  
4. **Slovensko a AI:** V ktorých oblastiach štátnej správy by podľa  
   vás mohla AI (napr. od Mistralu) priniesť najväčší úžitok?  
5. **Regulácia ako konkurenčná výhoda:** Je správne, že európske  
   regulácie (EU AI Act) chránia domácich poskytovateľov pred americkou  
   konkurenciou, alebo to brzdí inovácie?

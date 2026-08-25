# Matematika a LLM – možnosti, limity a hybridný prístup  


Veľké jazykové modely predstavujú vynikajúci nástroj na prácu s matematikou,  
no ich využitie má svoje limity. Fungujú skôr ako **jazykoví experti na matematiku**  
než ako samotné kalkulačky. Vynikajú vo vysvetľovaní zložitých konceptov, riešení  
slovných úloh a generovaní cvičných príkladov.  

Hlavným úskalím však zostáva fakt, že LLM sú **pravdepodobnostné generátory  
textu**, nie deterministické stroje.  
Nemajú v sebe zabudovaný logický obvod kalkulačky; namiesto výpočtu  
sa snažia odhadnúť nasledujúci najpravdepodobnejší „token".  
To vedie k tzv. **matematickým halucináciám**, kedy model sebavedomo  
predloží nesprávny výsledok.  
Hoci nové uvažujúce modely vďaka internému reťazcu myšlienok tieto  
nedostatky zmierňujú, stále nie sú stopercentne spoľahlivé pri čistej  
aritmetike.  

---

## Obsah

- [Prečo LLM nie je kalkulačka](#prečo-llm-nie-je-kalkulačka)
- [Matematické halucinácie](#matematické-halucinácie)
- [Uvažujúce modely: zlepšenie, nie dokonalosť](#uvažujúce-modely-zlepšenie-nie-dokonalosť)
- [Porovnávacia tabuľka: LLM verzus tradičné nástroje](#porovnávacia-tabuľka-llm-verzus-tradičné-nástroje)
- [Kde LLM v matematike skutočne vyniká](#kde-llm-v-matematike-skutočne-vyniká)
- [Hybridný prístup: zlatý štandard pre matematiku](#hybridný-prístup-zlatý-štandard-pre-matematiku)
- [Praktické odporúčania](#praktické-odporúčania)
- [Wolfram Alpha a Python: spoľahliví partneri LLM](#wolfram-alpha-a-python-spoľahliví-partneri-llm)
- [Zhrnutie kapitoly](#zhrnutie-kapitoly)
- [Otázky & diskusia](#otázky--diskusia)

---

## Prečo LLM nie je kalkulačka  

Aby sme pochopili, prečo LLM občas robí chyby pri číslach, musíme  
rozumieť tomu, ako bol natrénovaný.  
Model sa učil z obrovského množstva textu – kníh, článkov, webových stránok.  
Naučil sa vzory jazyka, vrátane matematických zápisov a odvodení.  
**Nikdy sa však nenaučil počítať** v zmysle, v akom počíta procesor.  

Keď mu položíte otázku *„Koľko je 345 × 789?"*, model nevykoná násobenie.  
Miesto toho zájde do svojej „pamäti" vzorcov a pokúsi sa uhádnuť,  
aké znaky nasledujú po zadaní takéhoto výrazu.  
Pre malé čísla, ktoré sa v trénovaných textoch objavovali často,  
to funguje spoľahlivo.  
Pri väčších číslach alebo viacstupňových výpočtoch však dochádza k chybám.  

> **Kľúčový rozdiel:** Kalkulačka *vypočíta* výsledok deterministicky.  
> LLM *tipuje* výsledok na základe pravdepodobnosti.  
> Pre väčšinu čísel je odhad správny – ale nie vždy.  

---

## Matematické halucinácie  

Pojem **halucinácia** v kontexte AI označuje situáciu, keď model  
s istotou tvrdí niečo nepravdivé.  
V matematike sa tento jav prejavuje obzvlášť nepríjemne, pretože:  

*   Model odpovie sebavedomo, bez akéhokoľvek náznaku pochybnosti.  
*   Výsledok môže vyzerať vierohodne – správny formát, správne jednotky,  
    logicky konzistentný kontext – ale číslo je jednoducho zlé.  
*   Čitateľ bez nezávislého overenia chybu neodhalí.  

**Typické scenáre, kde halucinácie hrozia:**  

*   Viacciferné násobenie alebo delenie (napr. 1,2 milióna × 9,8 milióna)  
*   Zložené percentuálne výpočty s viacerými krokmi  
*   Numerické integrácie a derivácie bez symbolického záznamu  
*   Konverzie jednotiek s neobvyklými koeficientmi  

---

## Uvažujúce modely: zlepšenie, nie dokonalosť  

Nová generácia **uvažujúcich modelov** (OpenAI o1/o3, Claude Extended  
Thinking, DeepSeek R1, Qwen QwQ) prináša výrazné zlepšenie.  
Tieto modely pred finálnou odpoveďou vykonajú viditeľný **reťazec myšlienok**  
(*chain-of-thought*) – rozbijú problém na kroky a postupne ich riešia.  

Výsledky na matematických benchmarkoch sú pôsobivé:  

| Benchmark | Štandardný LLM | Uvažujúci LLM |  
| :--- | :---: | :---: |  
| **GSM8K** (základná matematika) | ~90 % | ~97 % |  
| **MATH** (súťažná matematika) | ~50–60 % | ~70–85 % |  
| **AIME** (ťažké olympijské úlohy) | ~5–15 % | ~50–70 % |  

> **Poznámka:** Uvedené hodnoty sú približné a orientačné; reálne skóre sa líši podľa konkrétneho modelu, verzie a času merania.

Napriek tomu platí: uvažujúce modely **nie sú stopercentne spoľahlivé**  
pri čistej aritmetike.  
Stále sa môžu pomýliť – najmä pri dlhých výpočtoch, kde sa chybička  
v jednom kroku prenáša do ďalších.  

---

## Porovnávacia tabuľka: LLM verzus tradičné nástroje  

| Úloha | Štandardné LLM | Uvažujúce LLM | Kalkulačka / Wolfram |  
| :--- | :---: | :---: | :---: |  
| Vysvetlenie konceptu | Vynikajúce | Vynikajúce | Žiadne |  
| Jednoduchá slovná úloha | Dobré | Dobré (často lepšie) | Slabé |  
| Výpočet 345 × 789 | Dobré (občas chyby) | Dobré | Dokonalé |  
| Výpočet 1,2 M × 9,8 M | Nespoľahlivé | Dobré, nie 100 % | Dokonalé |  
| Zložitý integrál | Časté chyby | Dobré | Dokonalé |  
| Dôkaz novej vety | Nepoužiteľné | Vo výskume | Nemožné |  

---

## Kde LLM v matematike skutočne vyniká  

Napriek spomínaným limitom existujú oblasti, kde LLM nemá  
v matematickom vzdelávaní konkurenciu:  

### 1. Vysvetľovanie konceptov  

LLM dokáže ten istý matematický pojem vysvetliť desiatimi rôznymi  
spôsobmi – formálne, intuitívne, cez analógiu, cez príbeh.  
Žiadna učebnica ani kalkulačka toto nezvládne.  

*Príklad:* „Vysvetli mi čo je derivácia, ako keby som mal 12 rokov."  
→ Model použije analógiu rýchlosti auta, sklon kopca a intuíciu  
momentálnej zmeny. Výsledok je pochopiteľnejší než učebnicová definícia.  

### 2. Riešenie slovných úloh s krokovým vysvetlením  

Slovné úlohy vyžadujú preklad z jazyka do matematického zápisu –  
presne to, v čom LLM exceluje.  
Model rozpozná, o aký typ úlohy ide, zvolí správny postup a každý krok  
komentuje zrozumiteľným jazykom.  

### 3. Generovanie cvičných príkladov  

Potrebujete 20 cvičení na kvadratické rovnice s rastúcou obtiažnosťou?  
LLM ich vygeneruje za sekundy, vrátane riešení a metodických poznámok.  

### 4. Kontrola a oprava vlastného riešenia  

Môžete LLM ukázať svoje riešenie a požiadať ho o spätnú väzbu.  
Model identifikuje chybu v postupe, nie len v číselnom výsledku –  
čo je pedagogicky oveľa cennejšie.  

### 5. Prepis matematiky do kódu  

LLM skvele prekladá matematické vzorce do programovacieho jazyka  
(Python, NumPy, MATLAB).  
Toto výrazne uľahčuje prácu analytikov, vedcov a vývojárov.  

---

## Hybridný prístup: zlatý štandard pre matematiku  

V súčasnosti sa ako najvhodnejší prístup k matematike ukazuje  
**hybridný model**. Princíp je jednoduchý:  

> *LLM na myslenie, špecializovaný nástroj na počítanie.*  

**Postup v praxi:**  

1.  **LLM na pochopenie zadania** – model rozanalyzuje problém,  
    identifikuje kľúčové veličiny a navrhne postup riešenia.  
2.  **LLM na návrh kódu alebo vzorca** – model napíše Python skript  
    alebo Wolfram výraz, ktorý problém matematicky vyjadrí.  
3.  **Špecializovaný nástroj na výpočet** – Python, Wolfram Alpha  
    alebo vedecká kalkulačka vykoná samotný výpočet deterministicky.  
4.  **LLM na interpretáciu výsledku** – model vysvetlí, čo číslo  
    znamená v kontexte pôvodného zadania.  

Takýto prístup spája silné stránky oboch svetov: jazykovú inteligenciu  
LLM a matematickú presnosť tradičných nástrojov.  

---

## Praktické odporúčania  

*   **Pre jednoduché orientačné výpočty** (odhady, „okrúhle" čísla,  
    porovnania veľkostí) – LLM postačí, výsledok spravidla sedí.  
*   **Pre výpočty, kde záleží na každej cifre** – vždy overte výsledok  
    kalkulačkou, Pythonom alebo Wolfram Alpha.  
*   **Pre pochopenie postupu alebo konceptu** – LLM je ideálny prvý krok,  
    lepší než väčšina učebníc.  
*   **Pre tvorbu cvičných materiálov** – LLM výrazne urýchli prípravu  
    a diverzifikáciu úloh.  
*   **Pre výskum a nové matematické dôkazy** – uvažujúce modely môžu  
    asistovať, no výsledky musia byť vždy overené ľudským matematikom.  

---

## Wolfram Alpha a Python: spoľahliví partneri LLM  

Dva najčastejšie odporúčané nástroje na výpočty v kombinácii s LLM:  

**Wolfram Alpha** je výpočtový vyhľadávač, ktorý rozumie prirodzenému  
jazyku a vracia presné matematické výsledky – od integrálov cez  
štatistiku až po fyzikálne konštanty.  
Je dostupný zadarmo na [wolframalpha.com](https://www.wolframalpha.com).  

**Python** (s knižnicami ako `sympy`, `numpy` alebo `scipy`) ponúka  
plnú programovú kontrolu – symbolickú matematiku, numerické výpočty  
aj vizualizácie.  
LLM vie napísať príslušný kód; Python kód potom spustíte a výsledok  
je deterministicky správny.  

> **Tip:** Mnohé LLM (ChatGPT, Claude, Gemini) majú priamo integrovaný  
> Python interpret – model kód nielen napíše, ale aj spustí a výsledok  
> overí. Toto je hybridný prístup v čistej forme.  

**Tool use / funkčné volania.** Moderné modely už nepracujú iba s textom – dokážu priamo  
volať externé nástroje (kalkulačku, Python interpret, webové vyhľadávanie). Keď model rozpozná,  
že ide o číselný výpočet, sám ho deleguje na nástroj a do odpovede zapracuje presný výsledok.  
Tento mechanizmus, známy ako *tool use* alebo *function calling*, je dnes štandardnou súčasťou  
hybridného riešenia.

## Zhrnutie kapitoly  

*   LLM sú **pravdepodobnostné generátory textu** – odhadujú, nevypočítavajú.  
    Matematické halucinácie (sebavedome nesprávne výsledky) sú reálnym rizikom.  
*   **Uvažujúce modely** (o1/o3, Claude Extended Thinking, DeepSeek R1) výrazne  
    zlepšujú výkony v matematike, no stopercentnú spoľahlivosť neposkytujú.  
*   LLM skutočne vynikajú vo **vysvetľovaní konceptov, riešení slovných  
    úloh, generovaní cvičení a prepise matematiky do kódu**.  
*   Odporúčaný prístup je **hybridný model**: LLM na pochopenie a návrh  
    postupu, špecializované nástroje (Wolfram Alpha, Python) na samotné  
    výpočty.  
*   Pravidlo palca: *ak záleží na presnosti čísla, overenie je povinné*.  

## Otázky & diskusia

1. Kde presne vedie hranica medzi tým, čo má LLM počítať sám, a tým, čo má prenechať špecializovanému nástroju?
2. Ako by ste overili výsledok LLM pri výpočte, od ktorého závisí dôležité rozhodnutie?
3. Je vhodné, aby študenti používali LLM pri domácich úlohách z matematiky? Kde pomáha a kde naopak škodí?
4. Môže uvažujúci model v budúcnosti úplne nahradiť ľudského matematika pri dôkazoch? Prečo áno alebo nie?
5. Ktorý z dvoch svetov – jazyková inteligencia alebo deterministický výpočet – bude podľa vás v matematike dominantnejší a prečo?

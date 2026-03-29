# Google AI Studio Playground

Google AI Studio (aistudio.google.com) je bezplatné webové prostredie,  
kde môžete experimentovať s modelmi Gemini priamo v prehliadači – bez  
inštalácie, bez konfigurácie servera, bez nutnosti písať kód. Je to  
miesto, kde vývojári, výskumníci aj študenti testujú nápady, ladia  
prompty a objavujú možnosti AI pred tým, než ich zakomponujú do aplikácií.  

V tejto kapitole sa pozrieme na každý prvok rozhrania podrobne –  
presne tak, ako vyzerá pri otvorení projektu v playground režime.  

---  

## Prehľad rozhrania  

Po otvorení projektu vidíte v AI Studio tri hlavné časti:  

1. **Hlavná plocha** (stred) – chat / promptovací editor, kde píšete  
   správy a vidíte odpovede modelu  
2. **Run settings** (pravý panel / horná časť) – výber modelu, systémové inštrukcie,  
   parametre generovania a nástroje  
3. **Advanced settings** (pravý panel / spodná časť) – bezpečnostné  
   nastavenia, stop sekvencie, dĺžka výstupu, Top P  

---  

## Panel „Run settings" – Nastavenia behu  

### Výber modelu  

Úplne hore v paneli Run settings sa nachádza **selektor modelu**.  
Na screenshote je vybraný:  

```  
Gemini 3 Flash Preview  
gemini-3-flash-preview  
```  

Pod názvom modelu je jeho krátky popis:  
*„Our most intelligent model built for speed, combining frontier  
intelligence with superior search and grounding."*  

Kliknutím na tento blok sa otvorí rozbaľovací zoznam, kde môžete  
prepnúť na iný model – napríklad Gemini 3.1 Pro, Gemini 3 Deep Think,  
Gemini 2.5 Flash alebo experimentálne preview verzie.  

> 💡 **Rada:** Modely s príponou `-preview` sú experimantálne verzie,  
> ktoré Google vydáva pred plným (GA) spustením. Majú väčšie kvóty  
> na testovanie, no môžu sa zmeniť alebo zrušiť bez upozornenia.  
> Pre produkčné projekty vždy používajte GA modely.  

#### Prehľad dostupných modelov v AI Studio (marec 2026)  

| Model | Kategória | Hlavná výhoda |  
| :--- | :--- | :--- |  
| **Gemini 3.1 Pro** | Vlajkový | Najvyšší výkon, vedecké uvažovanie |  
| **Gemini 3 Deep Think** | Uvažovací | Matematika, logika, dlhé kontexty |  
| **Gemini 3 Flash Preview** | Rýchly | Rýchlosť + vyhľadávanie |  
| **Gemini 3 Flash Lite** | Úsporný | Nízka cena, vysoký objem |  
| **Gemini 2.5 Pro** | GA preview | Vyvážený výkon |  
| **Gemini 2.5 Flash** | GA | Rýchlosť s uvažovaním |  
| **Gemini 2.0 Flash** | GA | Multimodalita, agentické úlohy |  

---  

### System instructions – Systémové inštrukcie  

Druhý blok v Run settings sa nazýva **System instructions**  
(Systémové inštrukcie). Pod názvom je popis:  
*„Optional tone and style instructions for the model."*  

Systémové inštrukcie sú textové pokyny, ktoré dostane model ešte  
pred samotnou konverzáciou. Určujú:  

- **Rolu modelu** – napr. „Si skúsený Python vývojár."  
- **Tón a štýl** – napr. „Odpovedaj stručne, bez výplní."  
- **Obmedzenia** – napr. „Nikdy neodpovedaj na otázky o konkurencii."  
- **Formát odpovedí** – napr. „Vždy odpovedaj v JSON formáte."  

**Príklad systémovej inštrukcie:**  
```  
Si AI asistent pre zákaznícku podporu slovenského e-shopu s elektronikou.  
Odpovedaj vždy v slovenčine, buď stručný a priateľský.  
Ak nevieš odpovedať, odkazuj na email podpora@shop.sk.  
```  

> 🎓 **Pre študentov:** Systémové inštrukcie sú ekvivalentom parametra  
> `system` v API alebo roly `{"role": "system", ...}` v Chat Completions.  
> V AI Studio ich nastavíte cez UI – v kóde ich vložíte priamo do požiadavky.  

---  

### No API Key – Upozornenie na API kľúč  

Tretí blok zobrazuje stav autentifikácie:  

```  
No API Key  
Switch to a paid API key to unlock higher quota and more features.  
```  

AI Studio umožňuje používať modely **bez API kľúča** cez bezplatnú kvótu  
(Google účet stačí). Táto kvóta je však obmedzená – pri intenzívnom  
testovaní ju môžete rýchlo vyčerpať.  

**Rozdiel medzi bezplatnou a platenou kvótou:**  

| | Bez API kľúča (free) | S API kľúčom (platené) |  
| :--- | :--- | :--- |  
| **Kvóta požiadaviek** | ~15 req/min, ~1500/deň | Podľa plánu (tisíce/min) |  
| **Prístup k modelom** | Obmedzený | Všetky vrátane preview |  
| **Export do kódu** | ✅ | ✅ |  
| **Fine-tuning** | ❌ | ✅ |  
| **SLA** | ❌ | ✅ |  

API kľúč vygenerujete priamo v AI Studio kliknutím na „Get API key"  
v ľavom menu. Kľúč začína `AIza...` a používa sa v Google GenAI SDK:  

```python  
from google import genai  

client = genai.Client(api_key="AIza...")  
```  

---  

### Temperature – Teplota  

Prvý nastaviteľný parameter je **Temperature** (Teplota), zobrazený  
ako posuvník s hodnotou napravo. Na screenshote je nastavená na **1**.  

Temperature kontroluje, ako „kreatívny" alebo „náhodný" je model  
pri výbere ďalšieho tokenu:  

| Hodnota | Správanie modelu | Vhodné pre |  
| :--- | :--- | :--- |  
| **0,0** | Deterministický – vždy rovnaká odpoveď | Kód, faktické otázky, JSON |  
| **0,3–0,7** | Vyvážený – konzistentný, no variabilný | Sumarizácia, preklad |  
| **1,0** | Štandardná kreativita (default) | Všeobecný chat, texty |  
| **1,5–2,0** | Veľmi kreatívny, experimentálny | Brainstorming, poézia, fikcia |  

> ⚠️ **Pozor:** Príliš vysoká teplota (> 1.5) môže spôsobiť, že model  
> bude generovať nesúvislé alebo fakticky nesprávne texty. Pri práci  
> s citlivými informáciami používajte nízku teplotu.  

**Technické vysvetlenie:**  
Pred výberom každého tokenu model vypočíta pravdepodobnostnú distribúciu  
možných nasledujúcich tokenov. Temperature túto distribúciu škáluje:  
nízka teplota ju „zostruje" (hlavný kandidát dominuje), vysoká teplota  
ju „sploštuje" (všetky tokeny majú podobnú pravdepodobnosť).  



**Úloha: „Vysvetli cloud computing pre tri rôzne publikum“**

Tvoja úloha pre model:

```
temperature = X

Vysvetli pojem „cloud computing“ trom rôznym publikám:
1. dieťaťu (8 rokov)
2. stredoškolákovi
3. seniorovi bez technického zázemia

Každé vysvetlenie musí byť:
- krátke (3–4 vety)
- prispôsobené publiku
- s jedným príkladom z reálneho života

Dodrž pravidlá temperature-sensitive promptu.
```

🔥 Prečo je táto úloha dobrá

- **Temperature 0.1** → model bude extrémne presný, jednoduchý, bez metafor.  
- **Temperature 0.5** → pekne vyvážené, prirodzené vysvetlenia.  
- **Temperature 0.9** → kreatívne, hravé, možno až príbehové.  


---  

### Media resolution – Rozlíšenie médií  

Parameter **Media resolution** je zobrazený ako rozbaľovací zoznam  
(dropdown). Týka sa spôsobu, akým model spracúva vstupné obrázky  
a videá.  

Dostupné hodnoty sú zvyčajne:  
- **Low** – obrázky sa zmenšia pred odoslaním; rýchlejšie, lacnejšie,  
  vhodné pre jednoduché otázky o obsahu obrázka  
- **Medium** – štandardné rozlíšenie, vhodné pre väčšinu úloh  
- **High** – plné rozlíšenie; pomalšie, nákladnejšie, ale nevyhnutné  
  pre detailnú analýzu (napr. rozpoznávanie textu v obraze, technické schémy)  

> 💡 **Praktický tip:** Pre analýzu dokumentov naskenovaných ako obrázky  
> (faktúry, zmluvy, technické výkresy) vždy použite High rozlíšenie.  
> Pre bežné otázky ako „čo je na fotografii" postačí Low alebo Medium.  

---  

### Thinking level – Úroveň uvažovania  

Parameter **Thinking level** (Úroveň uvažovania) je jednou z najdôležitejších  
noviniek modelov Gemini 3. Na screenshote je nastavený na **High**.  

Dostupné úrovne:  

| Úroveň | Správanie | Čas odpovede | Spotreba tokenov |  
| :--- | :--- | :--- | :--- |  
| **None** | Model odpovedá priamo bez interného premýšľania | Veľmi rýchlo | Minimálna |  
| **Low** | Krátke interné uvažovanie | Rýchlo | Nízka |  
| **Medium** | Strednodobé uvažovanie | Stredne | Stredná |  
| **High** | Hlboké, viacstupňové uvažovanie | Pomalšie | Vysoká |  

Keď zapnete Thinking, model pred odpoveďou vygeneruje **interný myšlienkový  
reťazec** (chain-of-thought) – podobne ako Extended Thinking v Claude  
alebo Deep Think režim v DeepSeek. Tento proces prebieha „za oponou"  
a výsledkom je výrazne lepšia odpoveď na zložité úlohy:  

- Matematické a logické problémy  
- Viacstupňové uvažovanie  
- Analýza protichodných informácií  
- Plánovanie a strategické rozhodnutia  

> 🎓 **Pre študentov:** Thinking level je trade-off medzi rýchlosťou  
> a kvalitou. Pre jednoduchý chat použite None alebo Low. Pre riešenie  
> komplexných úloh zapnite High – môže trvať 10–30 sekúnd, no odpoveď  
> bude podstatne presnejšia.  

---  

## Sekcia „Tools" – Nástroje  

Pod parametrami generovania sa nachádza sekcia **Tools** (Nástroje).  
Každý nástroj sa dá zapnúť/vypnúť prepínačom. Na screenshote sú  
všetky vypnuté. Niektoré majú aj tlačidlo **Edit** pre podrobnejšiu  
konfiguráciu.  

### Structured outputs – Štruktúrované výstupy  

**Structured outputs** zaručuje, že model vráti odpoveď vždy v presne  
definovanom formáte – typicky **JSON** podľa zadanej schémy.  

Kliknite na **Edit** pre definovanie JSON schémy:  

```json  
{  
  "type": "object",  
  "properties": {  
    "meno": {"type": "string"},  
    "vek": {"type": "integer"},  
    "email": {"type": "string", "format": "email"}  
  },  
  "required": ["meno", "vek"]  
}  
```  

Keď je Structured outputs zapnutý, model **zaručene vráti JSON** podľa  
tejto schémy – žiadny úvodný text, žiadne vysvetlivky, čistý JSON.  

**Kedy použiť:**  
- Extrakcia dát z textu (mená, dátumy, sumy)  
- Generovanie konfiguračných súborov  
- Integrácia s databázami (priame mapovanie na tabuľky)  
- Parsovanie životopisov, faktúr, zmlúv  

---  

### Code execution – Spúšťanie kódu  

**Code execution** umožňuje modelu nielen napísať kód, ale ho aj  
**skutočne spustiť** v sandboxovom prostredí a vrátiť výsledky.  

Keď je zapnutý, model môže:  
- Vykonávať Python kód a vrátiť výstup  
- Testovať algoritmy a matematické výpočty  
- Analyzovať dáta (vrátane grafov pomocou matplotlib)  
- Iteratívne opravovať kód na základe chybových hlásení  

**Príklad:** Opýtate sa „Aký je faktoriál čísla 20?" – s Code execution  
model napíše `print(math.factorial(20))`, spustí ho a vráti presný výsledok  
`2432902008176640000` namiesto toho, aby ho odhadoval z pamäte.  

> ⚠️ **Bezpečnosť:** Kód beží v izolovanom Google sandbox prostredí.  
> Nemá prístup na internet, k vašim súborom ani k externým zdrojom.  

---  

### Function calling – Volanie funkcií  

**Function calling** (Volanie funkcií) je mechanizmus, pomocou ktorého  
model môže zavolať externé nástroje, API alebo funkcie, ktoré mu definiujete.  

Kliknite na **Edit** pre definovanie funkcií:  

```json  
{  
  "name": "get_current_weather",  
  "description": "Získa aktuálne počasie pre zadané mesto",  
  "parameters": {  
    "type": "object",  
    "properties": {  
      "city": {  
        "type": "string",  
        "description": "Názov mesta, napr. Bratislava"  
      }  
    },  
    "required": ["city"]  
  }  
}  
```  

Keď používateľ napíše „Aké je počasie v Košiciach?", model:  
1. Rozpozná, že má zavolať funkciu `get_current_weather`  
2. Vráti štruktúrovanú požiadavku na volanie funkcie (nie text)  
3. Vaša aplikácia zavolá skutočné počasie API  
4. Výsledok pošlete späť modelu, ktorý ho preformuluje do čitateľnej odpovede  

> 🎓 **Pre študentov:** Function calling je základný stavebný kameň  
> **AI agentov** – systémov, kde model riadi vonkajšie nástroje a akcie.  
> Bez tejto funkcie by bol model uzavretý sám v sebe; s ňou môže  
> vyhľadávať, rezervovať, posielať e-maily a interagovať so svetom.  

---  

### Grounding with Google Search – Uzemnenie cez Google vyhľadávanie  

**Grounding with Google Search** prepojí model s **živým internetom**.  
Keď je zapnutý, model môže vyhľadávať aktuálne informácie na Google  
a odpovedať na základe reálnych, čerstvých zdrojov.  

Príklady otázok, kde je Grounding nevyhnutný:  
- „Aký je kurz eura voči doláru dnes?"  
- „Kto vyhral včerajší zápas majstrovskej ligy?"  
- „Aké sú najnovšie správy o Claude Opus 4.6?"  
- „Aká je predpoveď počasia na Slovensku tento víkend?"  

Bez Grounding model odpovedá len z tréningových dát – s cut-off dátumom,  
za ktorým nemá informácie. S Grounding dostane odpovede s **citáciami  
zdrojov** a aktuálnymi dátami.  

> 💡 **Zákulisie:** Keď zapnete Grounding, AI Studio automaticky rozhodne,  
> či je pre danú otázku potrebné vyhľadávanie. Faktické a historické otázky  
> zodpovie z pamäte; otázky vyžadujúce aktuálne dáta spustia vyhľadávanie.  

---  

### Grounding with Google Maps – Uzemnenie cez Google Maps  

**Grounding with Google Maps** prepojí model s Google Maps API.  
Keď je zapnutý, model môže:  

- Vyhľadávať miesta, adresy a podniky  
- Odhadovať vzdialenosti a časy cestovanie  
- Odpovedať na otázky ako „Aké reštaurácie sú otvorené v mojom okolí?"  
- Integrovať geografické kontexty do konverzácie  

Táto funkcia je cennná pre aplikácie v oblasti cestovania, logistiky,  
miestnych odporúčaní a lokálneho vyhľadávania.  

---  

### URL context – Kontext z URL  

**URL context** umožňuje modelu načítať a spracovať obsah webovej stránky  
zadanej cez URL. Namiesto kopírovania celého textu stránky stačí vložiť link.  

**Prípad použitia:**  
```  
Prečítaj si tento článok: https://blog.example.com/ai-trends-2026  
a zhrň hlavné myšlienky v 5 bodoch.  
```  

Model stiahne obsah stránky a spracuje ho ako súčasť kontextu konverzácie.  
Je to rýchly spôsob, ako poskytnúť modelu externé znalosti bez manuálneho  
kopírovania.  

> ⚠️ **Obmedzenie:** URL context funguje len na verejne dostupných stránkach.  
> Stránky za prihlásením, paywallom alebo so zákazom robotov nie sú dostupné.  

---  

## Panel „Advanced settings" – Pokročilé nastavenia  

### Safety settings – Bezpečnostné nastavenia  

**Safety settings** (Bezpečnostné nastavenia) kontrolujú, aký obsah  
model povolí alebo odmietne. Kliknite na **Edit** pre zobrazenie  
a úpravu detailných nastavení.  

Google Gemini štandardne filtruje obsah v štyroch kategóriách:  

| Kategória | Popis |  
| :--- | :--- |  
| **Harassment** | Obťažovanie, šikana, urážlivý obsah |  
| **Hate speech** | Nenávistný prejav, diskriminácia |  
| **Sexually explicit** | Sexuálne explicitný obsah |  
| **Dangerous content** | Nebezpečné inštrukcie (zbrane, drogy...) |  

Pre každú kategóriu môžete nastaviť prah:  
- **Block most** – striktné filtrovanie (odporúčané pre konzumné aplikácie)  
- **Block some** – stredné filtrovanie (default)  
- **Block few** – minimálne filtrovanie (len pre overené výskumné projekty)  

> ⚠️ **Dôležité:** Rozvolniť bezpečnostné nastavenia je možné len  
> pre overené firemné a výskumné účely po schválení Googlom.  
> Bezplatný tier pracuje vždy s prísnym filtrovaním.  

---  

### Add stop sequence – Stop sekvencie  

**Stop sequence** (Stop sekvencia) je reťazec znakov, pri ktorých  
model okamžite zastaví generovanie – aj keby nebol hotový.  

Príklady použitia:  

```  
Stop sequence: "###"  
→ Model prestane generovať, keď napíše "###"  
```  

```  
Stop sequence: "\n\n"  
→ Model sa zastaví po prvom prázdnom riadku (užitočné pre jednoodstavcové odpovede)  
```  

```  
Stop sequence: "END"  
→ Generovanie skončí, keď model napíše slovo "END"  
```  

Stop sekvencie sú užitočné pri:  
- **Parsovaní štruktúrovaného výstupu** – zastaviť generovanie po prvom JSON bloku  
- **Kontrole dĺžky** – zastaviť po prvej odpovedi v dialógu  
- **Template-based génrovaní** – model vyplní šablónu a zastaví pri definovanom značke  

Vyber firs name, last name, email pre employees a exportuj do JSOn

```
# Employees

| ID | First Name | Last Name | Role | Email | Phone |
|----|------------|-----------|------|-------|-------|
| E01 | Martin | Novák | Software Engineer | martin.novak@company.com | +421 901 234 567 |
| E02 | Jana | Kováčová | Product Manager | jana.kovacova@company.com | +421 902 345 678 |
| E03 | Tomáš | Horváth | DevOps Engineer | tomas.horvath@company.com | +421 903 456 789 |
| E04 | Lucia | Šimková | UX Designer | lucia.simkova@company.com | +421 904 567 890 |
| E05 | Michal | Blaho | Data Analyst | michal.blaho@company.com | +421 905 678 901 |
| E06 | Zuzana | Fialová | QA Engineer | zuzana.fialova@company.com | +421 906 789 012 |

# Customers

| ID | First Name | Last Name | City | Email | Registered |
|----|------------|-----------|------|-------|------------|
| C01 | Peter | Mráz | Bratislava | peter.mraz@gmail.com | 2024-01-15 |
| C02 | Anna | Benková | Košice | anna.benkova@email.sk | 2024-02-03 |
| C03 | Róbert | Takáč | Žilina | robert.takac@outlook.com | 2024-02-17 |
| C04 | Monika | Varga | Prešov | monika.varga@gmail.com | 2024-03-05 |
| C05 | Stanislav | Petráš | Banská Bystrica | stanislav.petras@gmail.com | 2024-03-22 |
| C06 | Eva | Kopecká | Nitra | eva.kopecka@email.sk | 2024-04-08 |
| C07 | Juraj | Molnár | Trnava | juraj.molnar@gmail.com | 2024-04-19 |
| C08 | Katarína | Szabó | Trenčín | katarina.szabo@outlook.com | 2024-05-02 |
| C09 | Miroslav | Oravec | Poprad | miroslav.oravec@gmail.com | 2024-05-14 |
| C10 | Veronika | Hudáková | Liptovský Mikuláš | veronika.hudakova@email.sk | 2024-05-28 |
| C11 | Marek | Štefánik | Spišská Nová Ves | marek.stefanik@gmail.com | 2024-06-10 |
| C12 | Barbora | Zemková | Zvolen | barbora.zemkova@outlook.com | 2024-06-23 |
| C13 | Jakub | Rusnák | Michalovce | jakub.rusnak@gmail.com | 2024-07-07 |
| C14 | Petra | Halásová | Martin | petra.halasova@email.sk | 2024-07-19 |
| C15 | Ľubomír | Kováč | Ružomberok | lubomir.kovac@gmail.com | 2024-08-01 |
| C16 | Silvia | Dudová | Piešťany | silvia.dudova@outlook.com | 2024-08-15 |
| C17 | Ondrej | Baláž | Levice | ondrej.balaz@gmail.com | 2024-08-29 |
| C18 | Natália | Čechová | Senica | natalia.cechova@email.sk | 2024-09-12 |
| C19 | Milan | Žák | Detva | milan.zak@gmail.com | 2024-09-25 |
| C20 | Daniela | Papšová | Humenné | daniela.papsova@outlook.com | 2024-10-08 |
| C21 | Radoslav | Horník | Námestovo | radoslav.hornik@gmail.com | 2024-10-21 |
| C22 | Ingrid | Šedivá | Partizánske | ingrid.sediva@email.sk | 2024-11-04 |
| C23 | Vladimír | Balko | Stará Ľubovňa | vladimir.balko@gmail.com | 2024-11-18 |
| C24 | Renáta | Gáborová | Sabinov | renata.gaborova@outlook.com | 2024-12-02 |
| C25 | Boris | Krajčí | Rimavská Sobota | boris.krajci@gmail.com | 2024-12-16 |
| C26 | Iveta | Polláková | Šaľa | iveta.pollakova@email.sk | 2025-01-07 |
| C27 | Dušan | Lukáč | Dolný Kubín | dusan.lukac@gmail.com | 2025-01-20 |
| C28 | Marta | Gregorová | Kysucké Nové Mesto | marta.gregorova@outlook.com | 2025-02-03 |
| C29 | Tibor | Bodnár | Gelnica | tibor.bodnar@gmail.com | 2025-02-17 |
| C30 | Alžbeta | Kušnírová | Revúca | alzbeta.kusnirova@email.sk | 2025-03-01 |
```


---  

### Output length – Dĺžka výstupu  

**Output length** nastavuje **maximálny počet tokenov** v odpovedi modelu.  
Na screenshote je nastavený na **65 536 tokenov**.  

| Nastavenie | Odporúčané použitie |  
| :--- | :--- |  
| **256 – 512** | Krátke odpovede, jednoduché otázky, chatbot |  
| **1 024 – 2 048** | Stredne dlhé odpovede, štandardné úlohy |  
| **4 096 – 8 192** | Dlhšie dokumenty, analýzy, kód |  
| **16 384 – 65 536** | Veľmi dlhé generovanie (celé kapitoly, komplexný kód) |  

> 💡 **Tokenizácia:** Jeden token ≈ 0,75 slova v angličtine / slovenčine.  
> 65 536 tokenov ≈ ~50 000 slovenských slov ≈ kniha o cca 150 stranách.  
> V praxi Gemini 3 Flash zriedkakedy generuje tak dlhé odpovede; maximum  
> je bezpečnostná poistka, nie cieľ.  

> ⚠️ **Náklady:** Výstupné tokeny sú drahšie ako vstupné. Prerušenie  
> generovania pomocou stop sekvencie alebo nižšieho Output length  
> môže výrazne znížiť náklady pri platenom API.  

---  

### Top P – Nucleus sampling  

**Top P** (Nucleus sampling) je parameter, ktorý filtruje tokeny podľa  
kumulatívnej pravdepodobnosti. Na screenshote je nastavený na **0,95**.  

Funguje takto:  
1. Model zoradí všetky možné nasledujúce tokeny podľa pravdepodobnosti  
2. Vyberá len z tých tokenov, ktorých kumulatívna pravdepodobnosť je ≤ Top P  
3. Zvyšné tokeny (tých málo percent) sú vylúčené z výberu  

| Hodnota Top P | Efekt |  
| :--- | :--- |  
| **0,1** | Veľmi konzervatívny – len najpravdepodobnejší token |  
| **0,5** | Mierne obmedzený výber |  
| **0,9** | Štandardné nastavenie pre väčšinu úloh |  
| **0,95** | Takmer celé spektrum (default AI Studio) |  
| **1,0** | Žiadne filtrovanie – všetky tokeny v hre |  

> 🎓 **Temperature vs. Top P:** Oba parametre kontrolujú „kreativitu",  
> ale inak. Temperature škáluje celú distribúciu. Top P odreže dlhý  
> chvost nepravdepodobných tokenov. Väčšina expertov odporúča nastaviť  
> len jeden z nich a druhý nechať na default – kombinácia oboch môže  
> viesť k nepredvídateľným výsledkom.  

---  

## Tlačidlo „Get code" – Export do kódu  

V pravom hornom rohu rozhrania sa nachádza tlačidlo **`<> Get code`**.  
Kliknutím naň AI Studio vygeneruje **hotový kód** v rôznych jazykoch  
pre presne tie nastavenia, ktoré máte aktuálne nakonfigurované:  

- **Python** (Google GenAI SDK)  
- **JavaScript / Node.js**  
- **REST (cURL)**  
- **Android (Kotlin)**  
- **Swift (iOS)**  

**Príklad exportovaného Python kódu:**  
```python  
import google.generativeai as genai  

genai.configure(api_key="AIza...")  

generation_config = {  
    "temperature": 1,  
    "top_p": 0.95,  
    "max_output_tokens": 65536,  
    "thinking_config": {"thinking_budget": -1}  # High thinking  
}  

model = genai.GenerativeModel(  
    model_name="gemini-3-flash-preview",  
    generation_config=generation_config,  
    system_instruction="Vaše systémové inštrukcie tu...",  
)  

chat_session = model.start_chat(history=[])  
response = chat_session.send_message("Váš prompt tu...")  
print(response.text)  
```  

> 💡 **Workflow:** Odporúčaný postup pre vývojárov:  
> 1. Experimentujte a ladíte prompt priamo v AI Studio (bez kódu)  
> 2. Keď ste spokojní s výsledkami, kliknite „Get code"  
> 3. Skopírujte vygenerovaný kód do svojho projektu  
> 4. Nahraďte API kľúč z environment premennej  

---  

## Kompletný príklad workflow v AI Studio  

Predstavte si, že chcete vytvoriť asistenta, ktorý extrahuje štruktúrované  
údaje z faktúr:  

### Krok 1: Nastavenie modelu  
- Model: `Gemini 3 Flash Preview`  
- Temperature: `0.2` (nízka – chceme konzistentné, presné výsledky)  
- Thinking level: `Low` (faktúry sú jednoduché dokumenty)  

### Krok 2: Systémové inštrukcie  
```  
Si asistent na spracovanie faktúr. Z každej faktúry extrahuj:  
dodávateľa, sumu, dátum splatnosti a číslo faktúry.  
Odpovedaj vždy len v JSON formáte, bez ďalšieho textu.  
```  

### Krok 3: Nástroje  
- ✅ Structured outputs zapnutý  
- Schéma:  
```json  
{  
  "type": "object",  
  "properties": {  
    "dodavatel": {"type": "string"},  
    "suma": {"type": "number"},  
    "datum_splatnosti": {"type": "string"},  
    "cislo_faktury": {"type": "string"}  
  }  
}  
```  
- ❌ Grounding vypnutý (faktúry nepotrebujú internet)  
- Media resolution: `High` (dokumenty v obrazovom formáte)  

### Krok 4: Testovanie  
Nahrajte obrázok faktúry a otestujte. Ak výsledky nie sú presné,  
upravte systémové inštrukcie alebo zvýšte rozlíšenie.  

### Krok 5: Export  
Kliknite „Get code" → Python → skopírujte do vašej aplikácie.  

---  

## Limity a kvóty  

| Limit | Bezplatný (bez API kľúča) | Platený (s API kľúčom) |  
| :--- | :--- | :--- |  
| **Požiadavky/minútu (RPM)** | 15 | 1 000+ |  
| **Tokeny/minútu (TPM)** | 1 milión | 4 milióny+ |  
| **Požiadavky/deň** | 1 500 | Prakticky neobmedzené |  
| **Prístup k Preview modelom** | ✅ | ✅ |  
| **Fine-tuning** | ❌ | ✅ |  
| **Batch požiadavky** | ❌ | ✅ |  

---  

## Zhrnutie kapitoly  

- **Google AI Studio** je bezplatné webové prostredie pre experimentovanie  
  s modelmi Gemini – ideálne pred integráciou do vlastnej aplikácie.  
- **Run settings** obsahuje výber modelu, systémové inštrukcie, Temperature,  
  Media resolution, Thinking level a sekciu Tools.  
- **Temperature** (0–2) kontroluje kreativitu; nízka = konzistentná,  
  vysoká = kreatívna odpoveď.  
- **Thinking level** (None/Low/Medium/High) zapína interné chain-of-thought  
  uvažovanie pre zložitejšie úlohy – na úkor rýchlosti.  
- **Tools** rozširujú schopnosti modelu: Structured outputs (JSON),  
  Code execution (spúšťanie kódu), Function calling (externé API),  
  Grounding (internet/mapy), URL context (web stránky).  
- **Advanced settings** ponúka Safety settings, Stop sequences,  
  Output length (max tokenov) a Top P (nucleus sampling).  
- Tlačidlo **Get code** exportuje aktuálnu konfiguráciu do hotového  
  Python, JS alebo cURL kódu – základ pre integráciu do projektu.  

## Otázky a diskusia  


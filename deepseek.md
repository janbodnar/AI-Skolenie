# DeepSeek – Čínske AI, ktoré otriaslo Silicon Valley  

DeepSeek je čínska AI spoločnosť, ktorá v januári 2025 spôsobila jeden  
z najväčších šokov v histórii technologického priemyslu. Jej model  
**DeepSeek-R1** dokázal to, čo mnohí považovali za nemožné: prekonať  
americké špičkové modely pri zlomku ich nákladov – a uvoľniť ho ako  
open-source pre celý svet.  

V tejto kapitole sa pozrieme na pôvod spoločnosti, technické základy  
jej modelov, aj na globálnu kontroverziu, ktorú vyvolala.  

---  

## Vznik a pozadie spoločnosti  

DeepSeek bola založená v roku **2023** ako dcérska spoločnosť čínskeho  
hedžového fondu **High-Flyer Capital Management** so sídlom v Hangzhou.  
Zakladateľom je **Liang Wenfeng** – matematik a podnikateľ, ktorý  
pôvodne budoval High-Flyer ako kvantitatívny fond využívajúci AI  
na obchodovanie s akciami.  

Na rozdiel od väčšiny AI spoločností, ktoré hľadajú externých investorov,  
DeepSeek je **plne súkromná a samofinancovaná** z výnosov hedžového fondu.  
To jej dáva nezvyčajnú slobodu – nemusí reportovať investorom ani  
dosahovať komerčné ciele v krátkom horizonte.  

Spoločnosť zamestnáva relatívne malý tím – odhadom **200–300 výskumníkov**,  
z ktorých väčšina sú čerství absolventi čínskych elitných univerzít  
(Peking University, Tsinghua). Napriek svojej veľkosti vyprodukovala  
výsledky, ktoré zahanbia tímy s tisíckami zamestnancov.  

---  

## Modely DeepSeek – prehľad  

| Model | Vydanie | Kľúčové vlastnosti |  
| :--- | :--- | :--- |  
| **DeepSeek-V1** | 2023 | Prvý verejný model, overenie konceptu |  
| **DeepSeek-Coder** | 2024 | Špecializovaný na programovanie |  
| **DeepSeek-V2** | máj 2024 | MoE architektúra, 236B parametrov (21B aktívnych) |  
| **DeepSeek-V2.5** | sep. 2024 | Vylepšené kódovanie a konverzácia |  
| **DeepSeek-R1** | jan. 2025 | **Prelomový reasoning model, spúšťač globálneho šoku** |  
| **DeepSeek-V3** | mar. 2025 | Vylepšený základný model |  
| **DeepSeek-R2** | jún 2025 | Ďalší generácia reasoning modelu |  
| **DeepSeek-V4** | dec. 2025 | Aktuálny vlajkový model |  

---  

## „Sputnik moment" AI: DeepSeek-R1 (január 2025)  

**20. januára 2025** DeepSeek zverejnil model **DeepSeek-R1** a technickú  
správu, ktorá otriasla celým AI svetom. Udalosť sa okamžite začala  
nazývať **„Sputnik moment" umelej inteligencie** – prirovnanie k roku  
1957, keď ZSSR vypustil prvý satelit a šokoval Západ ukázaním, že  
technologická nadradenosť USA nie je samozrejmá.  

### Čo bol šok?  

DeepSeek-R1 bol **reasoning model** – teda model schopný hlbokého  
uvažovania krok za krokom, podobne ako OpenAI o1. Na kľúčových  
benchmarkoch dosiahol porovnateľné, niekedy lepšie výsledky.  

Ale skutočný šok prišiel, keď DeepSeek zverejnil **náklady na tréning**:  

> *Celkové náklady na natrénovanie DeepSeek-V3 (predchodca R1):*  
> **~5,6 milióna dolárov**  

Pre porovnanie, OpenAI odhaduje náklady na tréning GPT-4 na viac ako  
**100 miliónov dolárov**. Meta uviedla, že tréning Llama 3 stál rádovo  
desiatky miliónov. DeepSeek to zvládol za menej ako cenu luxusného bytu  
v San Franciscu.  

### Ako to bolo technicky možné?  

DeepSeek dosiahol efektivitu kombináciou niekoľkých inovatívnych prístupov:  

#### 1. Mixture of Experts (MoE) architektúra  
Model má celkovo **671 miliárd parametrov**, no pri každom tokene  
aktivuje len **37 miliárd**. Ostatné sú „spiacimi expertmi" čakajúcimi  
na relevantné vstupy. Výsledok: výkon veľkého modelu pri spotrebe  
malého.  

#### 2. Multi-Head Latent Attention (MLA)  
DeepSeek vyvinul vlastný mechanizmus pozornosti, ktorý drasticky  
znižuje pamäťové nároky počas generovania. Toto umožnilo spúšťať  
model na lacnejšom hardvéri.  

#### 3. FP8 tréning  
Namiesto štandardnej FP16 presnosti použili 8-bitovú aritmetiku,  
čím znížili nároky na GPU pamäť a zrýchlili tréning bez výraznej  
straty výkonu.  

#### 4. Obmedzený hardvér – a tvorivosť z núdze  
Kvôli americkým exportným obmedzeniam (pozri nižšie) DeepSeek nemohol  
kupovať najvýkonnejšie NVIDIA čipy (H100). Trénoval na starších  
**H800** a A100 čipoch – čo ich prinútilo inovovať namiesto toho,  
aby jednoducho použili brute-force výkon.  

> 💡 **Paradox sankcií:** Americké exportné obmedzenia, určené na spomalenie  
> čínskeho AI výskumu, de facto prinútili DeepSeek nájsť efektívnejší  
> prístup k trénovaniu. Výsledok bol presný opak zamýšľaného efektu.  

#### 5. Open-source prístup  
DeepSeek-R1 bol uvoľnený pod **licenciou MIT** – teda úplne slobodnou  
licenciou, ktorá dovoľuje komukoľvek model stiahnuť, modifikovať  
a komerčne použiť. Toto bol ďalší šok: kým OpenAI a Anthropic  
svoje modely skrývajú, DeepSeek ich daroval celému svetu.  

---  

## Kontroverzia: „Nvidia deň D"  

### Pád akcií NVIDIA  

**27. januára 2025** – sedem dní po vydaní DeepSeek-R1 – padli akcie  
NVIDIA o **17 %** v priebehu jedného dňa.  

V absolútnych číslach: **trhová kapitalizácia NVIDIA klesla o ~593 miliárd  
dolárov** – čo je historicky najväčší jednodenný pokles hodnoty akejkoľvek  
spoločnosti v dejinách burzových trhov.  

Prečo? Investori si uvedomili priamy dôsledok:  

> Ak je možné trénovať špičkový AI model za 5,6 milióna dolárov  
> na starých čipoch, kto potom potrebuje kupovať tisíce H100 GPU  
> za tens-of-billions dolárov?  

Obchodný model NVIDIA stojí na predpoklade, že tréning AI modelov  
si vyžaduje stále výkonnejší – a drahší – hardvér. DeepSeek tento  
predpoklad spochybnil.  

### Prepady ďalších technologických akcií  

Pád nebol izolovaný – celý „AI hodnotový reťazec" pocítil šok:  

| Spoločnosť | Pokles (27. jan. 2025) | Dôvod |  
| :--- | :--- | :--- |  
| **NVIDIA** | −17 % (−$593 mld) | Spochybnenie potreby drahých GPU |  
| **Broadcom** | −17 % | AI čipový dodávateľ |  
| **TSMC** | −13 % | Výrobca čipov |  
| **Microsoft** | −4 % | Masívne investície do AI infraštruktúry |  
| **Oracle** | −14 % | Cloudová AI infraštruktúra |  
| **Constellation Energy** | −21 % | Dodávateľ energie pre AI dátové centrá |  

Celkový odhadovaný pokles amerických technologických akcií v ten deň:  
**viac ako 1 bilión dolárov**.  

### Reakcia Silicon Valley  

Reakcie z amerického AI priemyslu boli zmiešané – od rešpektu po alarm:  

**Sam Altman (OpenAI CEO):**  
> *„DeepSeek-R1 je impresívny model, najmä čo sa týka toho, čo  
> dokáže za svoju cenu. Sme radi, že open-source modely napredujú."*  
(Interpretovaný ako diplomatická, no znepokojená reakcia.)  

**Marc Andreessen (venture kapitalista):**  
> *„DeepSeek R1 je jeden z najpôsobivejších a najrušivejších  
> prelomov, aké som kedy videl. Hlboký a úplný americký  
> technologický export... Wow."*  

**Elon Musk:**  
> *„Je to skutočné. Americké firmy musia zintenzívniť svoju hru."*  

**Jensen Huang (CEO NVIDIA)** sa snažil investorov upokojiť,  
argumentujúc, že lacnejší tréning povedie k **väčšiemu dopytu**  
po AI celkovo – jav známy ako **Jevonsov paradox** (keď sa niečo  
stane lacnejším, ľudia ho chcú viac, nie menej).  

---  

## Bezpečnostné a politické obavy  

Technická stránka DeepSeeku bola obdivovaná. Politická stránka  
vyvolala vlnu znepokojenia na celom Západe.  

### 1. Dáta na čínskych serveroch  

DeepSeek otvorene uvádza v svojich **podmienkach používania**,  
že ukladá dáta na serveroch v Číne, na ktoré sa vzťahujú  
čínske zákony – vrátane zákona o národnej bezpečnosti (2015),  
ktorý zaväzuje čínske spoločnosti poskytovať dáta vláde na požiadanie.  

### 2. Zákazy a obmedzenia po celom svete  

Reakcia vlád bola rýchla:  

| Krajina / Organizácia | Opatrenie |  
| :--- | :--- |  
| **Taliansko** | Celoplošný zákaz DeepSeek od januára 2025 |  
| **Austrália** | Zákaz na vládnych zariadeniach (február 2025) |  
| **Taiwan** | Zákaz používania vo vládnom sektore |  
| **Južná Kórea** | Vyšetrovanie a dočasné obmedzenia |  
| **USA – Námorníctvo** | Zákaz používania pre personál |  
| **USA – Kongres** | Návrh zákona na zákaz DeepSeek na vládnych zariadeniach |  
| **NASA, Pentagon** | Interné zákazy |  
| **Viaceré firmy** | Samsung, Apple, NASA – zákaz na pracovných zariadeniach |  

### 3. Cenzúra a citlivé témy  

Výskumníci okamžite otestovali DeepSeek na citlivé politické témy.  
Výsledky boli predvídateľné:  

- **Tiananmenské námestie (1989):** Model odmieta diskutovať alebo  
  aktívne dezinformuje v súlade s čínskym štátnym naratívom.  
- **Taiwan:** Model opisuje Taiwan výhradne ako súčasť Číny.  
- **Ujguri a Tibet:** Citlivé témy sú ignorované alebo pokryté  
  štátnym naratívom.  
- **Kritika KSČ:** Odmietnutie alebo vyhýbanie sa.  

Tieto obmedzenia sú zabudované priamo do modelu – nie len do chatovacieho  
rozhrania. Pre bežné úlohy (kód, matematika, písanie) cenzúra nemá  
žiadny vplyv. Pre politicky citlivé témy je model nespoľahlivý.  

### 4. Podozrenia z krádeže dát od OpenAI  

V januári 2025 OpenAI a Microsoft oznámili, že majú dôkazy o tom,  
že **čínski aktéri** (nepriamo spomínaný DeepSeek) **systematicky  
extrahovali výstupy z GPT modelov** pomocou automatizovaných dotazov  
(tzv. model distilation / data distillation) v rozpore s podmienkami  
používania.  

Model distilation je technika, kde sa nový, lacnejší model trénuje  
na výstupoch iného, drahšieho modelu – čím „destiluje" jeho znalosti.  
OpenAI to priamo zakázal vo svojich podmienkach; DeepSeek poprel  
akékoľvek porušenie.  

> Toto obvinenie nebolo nikdy formálne dokázané ani vyvrátené.  

### 5. Skrytý kód a komunikácia s čínskymi servermi  

Bezpečnostní výskumníci z firmy **Feroot Security** objavili  
v kóde webovej verzie DeepSeek zaobfuskovaný JavaScript, ktorý  
komunikoval so servermi spoločnosti **China Mobile** –  
čínskej štátnej telekomunikačnej firmy, ktorú USA zaradili  
na čiernu listinu.  

DeepSeek na tieto zistenia nereagoval. Mnohé organizácie  
to však považujú za dostatočný dôvod na úplný zákaz.  

---  

## Čo DeepSeek zmenil v AI odvetví  

Bez ohľadu na kontroverziu DeepSeek trvale ovplyvnil smer  
vývoja AI:  

### 1. Efektívnosť sa stala prioritou  
Pred DeepSeekom bol dominantný prístup „škáluj za každú cenu" –  
väčší model, viac GPU, viac peňazí. Po DeepSeeku sa celé odvetvie  
začalo pýtať: ako dosiahnuť rovnaký výkon lacnejšie?  

Google, Meta aj Anthropic urýchlili výskum efektívnych architekúr  
a publikácie o MoE a latentnej pozornosti zaznamenali obrovský nárast  
citácií.  

### 2. Open-source zažil renesanciu  
Vydanie R1 pod MIT licenciou ukázalo, že aj špičkové modely môžu byť  
open-source. Meta zrýchlila vydanie Llama 4 a otvorila jeho licenciu.  
Mistral zdvojnásobil úsilie v open-source smerovaní.  

### 3. Prehodnotenie exportných kontrol  
Americký Kongres začal debatu o tom, či exportné obmedzenia  
čipov do Číny naozaj fungujú – alebo či len stimulujú čínsku  
inováciu. Výsledok debaty je k marcu 2026 stále otvorený.  

### 4. „Compute isn't everything"  
Jensen Huang síce má pravdu, že inference (spúšťanie modelu)  
spotrebúva stále viac GPU. No DeepSeek dokázal, že pri tréningu  
nie je výpočtový výkon jedinou premennou – algorithmic cleverness  
môže nahradiť brute force.  

---  

## Ako bezpečne používať DeepSeek  

Napriek kontroverziám je DeepSeek legálny a voľne dostupný nástroj  
vo väčšine krajín vrátane Slovenska. Pre bežné vzdelávacie, tvorivé  
a kódovacie úlohy je výConný asistent.  

**Odporúčané bezpečnostné pravidlá:**  

1. **Nezdieľajte osobné identifikačné údaje** – meno, adresu, rodné číslo.  
2. **Nezdieľajte firemné dôverné informácie** – zmluvy, zákaznícke dáta,  
   interné dokumenty.  
3. **Nepoužívajte ho na prácu s citlivými vládnymi alebo zdravotnými dátami.**  
4. **Pre politicky citlivé témy overte informácie z iných zdrojov.**  
5. **Na pracovných zariadeniach sa riaďte IT politikou organizácie.**  

> 💡 **Kontextuálne pravidlo:** Použite rovnakú opatrnosť, akú by ste  
> uplatnili pri zdieľaní informácií s cudzím človekom na internete.  
> Pre väčšinu denných úloh je DeepSeek bezpečný a užitočný nástroj.  

---  

## Funkcie pre používateľov  

Aktuálne okno kontextu (maximálna pamäť na jednu konverzáciu) v bezplatnej verzii  
DeepSeek Chat je **1 milión tokenov**. V praxi to znamená, že model dokáže naraz  
spracovať text zodpovedajúci približne 750 000 slovám – čo je napríklad objem všetkých  
troch dielov knižnej trilógie *Pán prsteňov* naraz. Vďaka takémuto veľkému kontextu  
môžete do konverzácie nahrať aj rozsiahle dokumenty (celé knihy, dlhé správy, viacero súborov)  
a DeepSeek si udrží prehľad o celom obsahu bez toho, aby zabúdal na úvodné časti rozhovoru.  

> Možnosti AI asistentov sa neustále zlepšujú a ich schopnosti a technické parametre  
> skokovo rastú.  

## 1. Web Search – vyhľadávanie naživo  

**Web Search** umožňuje DeepSeeku pristupovať k aktuálnemu obsahu internetu.  
Bez tejto funkcie model odpovedá na základe svojich trénovacích údajov  
(ktoré majú určitý časový limit). S aktivovaným vyhľadávaním dokáže:  

- priniesť najnovšie správy, výsledky športových zápasov, aktuálne dáta,  
- overiť fakty a poskytnúť zdroje,  
- pracovať s informáciami, ktoré sa rýchlo menia.  

**Ako na to:**  
V chatovacom prostredí nájdete prepínač alebo tlačidlo **„Search“** (prípadne  
ikonu glóbusu). Aktivujte ho pred odoslaním otázky. V odpovedi sa potom  
zobrazia odkazy na navštívené stránky, vďaka čomu si môžete overiť pôvod  
informácií.  

> **Tip:** Web search používajte vždy, keď potrebujete čerstvé alebo overené  
> informácie z externých zdrojov.  

## 2. Deep Think – hlboké uvažovanie  

**Deep Think** je špeciálny režim, pri ktorom model pred finálnou odpoveďou  
vykoná detailný myšlienkový proces (tzv. *chain-of-thought*). Tento režim je  
ideálny pre:  

- zložité matematické úlohy,  
- logické hádanky a analytické problémy,  
- programovanie a algoritmické výzvy,  
- viacvrstvové otázky, kde záleží na postupnosti krokov.  

**Výhody:**  
Uvidíte, ako AI k odpovedi dospieva – to je mimoriadne užitočné na učenie sa  
a rozvoj kritického myslenia. Deep Think totiž zobrazuje uvažovanie krok za  
krokom, takže môžete pochopiť nielen výsledok, ale aj cestu k nemu.  

**Ako na to:**  
Zapnite prepínač **„Deep Think“** (alebo ekvivalentné označenie) a zadajte  
otázku. Odpoveď bude štruktúrovaná – najprv sa zobrazí uvažovanie, potom  
samotný výsledok.  

## 3. File Upload – nahrávanie súborov  

DeepSeek umožňuje nahrať súbory priamo do konverzácie. Podporované sú formáty  
ako **PDF, DOCX, TXT, obrázky s textom (PNG, JPG)** a tabuľky.  

**Použitie:**  

- analýza dlhých dokumentov (zhrnutie, kľúčové body, odpovede na otázky k textu),  
- extrakcia informácií z viacerých súborov naraz (porovnanie, syntéza),  
- prepis textu z obrázkov (napr. fotografie tabuľky, screenshoty).  

Stačí kliknúť na ikonu **„Nahrať“** (často symbol spony alebo šípky) a vybrať  
súbor z počítača. Model ho spracuje a vy sa ho môžete pýtať na jeho obsah.  
Môžete nahrať aj viacero súborov v rámci jednej správy.  

## 4. História konverzácií  

Všetky vaše chaty s DeepSeekom sa automaticky ukladajú do histórie v bočnom  
paneli. Táto funkcia slúži na:  

- pokračovanie v rozpracovaných úlohách,  
- spätné vyhľadanie starších odpovedí,  
- organizáciu podľa tém – konverzácie si môžete premenovať.  

História je prístupná kedykoľvek, čo sa hodí najmä pri dlhodobejších projektoch  
alebo vzdelávacích aktivitách.  

## 5. Prečo je dobré začať novú konverzáciu (a čo je context rot)  

Každý AI model má technický limit nazývaný **kontextové okno** – maximálny počet  
slov (tokenov), ktoré si v rámci jednej konverzácie „pamätá“. Keď konverzácia  
príliš narastie, môže nastať jav známy ako **context rot** (rozpad kontextu).  

**Prejavy context rotu:**  

- model začína zabúdať na to, čo ste mu povedali na začiatku rozhovoru,  
- odpovede sa stávajú menej presné, chaotické,  
- môže dochádzať k miešaniu inštrukcií z rôznych častí konverzácie.  

**Ako sa tomu vyhnúť:**  
Jednoduchým zvykom je **začať novú konverzáciu („New Chat“) vždy, keď prechádzate  
na novú tému alebo po ukončení komplexnej úlohy.** Tým zabezpečíte, že:  

- model začína s čistým kontextom a plnou kapacitou pamäte,  
- odpovede sú presné a nijako neovplyvnené staršími témami,  
- vyhnete sa neprehľadnosti a chybám spôsobeným dlhým rozhovorom.  

> **Pomôcka na zapamätanie:** Predstavte si kontextové okno ako tabuľu. Keď je  
> popísaná celá, treba ju utrieť – začať nový chat – aby ste mohli písať nové  
> a prehľadné poznámky.  

## Príklady  

```  
napíš posledných 3 prezidentov Slovenska  
kedy naposledy porazili Slováci Fínov v hokeji  
how many r letters are in strawberry  
how many years did the 100 years war last  
Autoumyvarka je 100m od mojho domu. Mam tam ist peso alebo autom?  
```  


###  Web Search – príklady  

**Príklad 1: Aktuálne správy**  
Otázka s aktivovaným Web Search: *„Aké je dnešné počasie v Košiciach a aké  
sa očakáva zajtra?“*  
Model vyhľadá aktuálnu meteorologickú predpoveď, uvedie zdroj (napr.  
SHMÚ) a porovná dni.  

**Príklad 2: Overenie faktov**  
*„Kedy vyšiel posledný album od kapely Kabát a ako sa volá?“*  
DeepSeek s web search nájde aktuálnu diskografiu, prípadne novinky,  
ktoré nie sú súčasťou jeho pôvodných trénovacích dát.  

**Príklad 3: Štatistiky**  
*„Aké boli výsledky slovenských hokejistov na posledných MS do 20  
rokov?“*  
Vyhľadávač doplní tabuľky, strelcov a odkazy na oficiálne štatistiky.  


### Deep Think – príklady  

**Príklad 1: Matematický dôkaz**  
Otázka: *„Dokáž, že pre ľubovoľné prirodzené číslo n je výraz n³ – n  
deliteľný šiestimi.“*  
Deep Think rozloží úlohu na kroky: faktorizácia, deliteľnosť dvoma  
a tromi, následne syntéza. Zobrazí sa celý myšlienkový reťazec.  

**Príklad 2: Logická hádanka**  
*„Máme päť domov v rade, každý inej farby, v nich ľudí rôznych  
národností, pijú rôzne nápoje, fajčia rôzne značky a majú rôzne  
domáce zvieratá. Kto má rybičky?“ (Einsteinova hádanka)*  
Režim Deep Think vytvorí tabuľku a systematicky vylučuje možnosti,  
pričom vysvetľuje každý krok.  

**Príklad 3: Algoritmické uvažovanie**  
*„Navrhni algoritmus na triedenie zoznamu mien podľa dĺžky, pričom  
pri rovnakej dĺžke podľa abecedy. Implementuj ho v Pythone.“*  
Model najprv popíše logiku (stabilné triedenie, kľúčové funkcie),  
potom napíše kód a vysvetlí jeho časovú zložitosť.  


### File Upload – príklady  

**Príklad 1: Analýza PDF dokumentu**  
Nahrám študijný materiál vo formáte PDF (20 strán) a spýtam sa:  
*„Zhrň kapitolu 3 do piatich bodov a vysvetli pojmy, ktoré sú  
tam definované.“*  
DeepSeek extrahuje text, vytvorí zhrnutie a zoznam definícií.  

**Príklad 2: Práca s tabuľkou**  
Nahrám súbor *.xlsx s mesačnými výdavkami firmy. Otázka:  
*„Ktorá kategória mala najvyšší nárast oproti minulému roku a  
o koľko percent?“*  
Model načíta dáta, vykoná porovnanie a vypíše výsledok vrátane  
medzivýpočtov.  

**Príklad 3: Prepis textu z obrázku**  
Nahrajem fotku rukou písanej poznámky. Otázka:  
*„Prepíš to do čitateľného textu a vytvor z toho akčné úlohy.“*  
DeepSeek rozpozná text, opraví prípadné nejasnosti a štruktúruje  
ho do zoznamu úloh.  


## Zhrnutie  

DeepSeek je čínska AI spoločnosť, ktorej model **DeepSeek-R1** (január 2025)  
spôsobil globálny šok – prekonaním amerických modelov pri zlomku nákladov  
a vydaním ako open-source. Vyvolal pád akcií NVIDIA o 17 % (−$593 mld),  
debaty o amerických exportných obmedzeniach a vlnu bezpečnostných zákazov.  

Pre každodenné úlohy je DeepSeek výkonný asistent s nástrojmi Web Search,  
Deep Think a File Upload. Správne využívanie histórie a pravidelný štart  
nových konverzácií vám pomôže udržať interakciu s AI prehľadnú a efektívnu.  

Pri práci s citlivými dátami dodržujte odporúčané bezpečnostné pravidlá –  
všetky dáta sa ukladajú na čínskych serveroch podliehajúcich čínskej legislatíve.  


## Otázky & diskusia  






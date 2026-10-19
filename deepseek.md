# DeepSeek a čínska AI  

DeepSeek je čínsky startup, ktorý v januári 2025 otriasol celým  
technologickým svetom. Jeho model **DeepSeek-R1** dosahoval výkon  
porovnateľný s najlepšími americkými modelmi, bol zverejnený s otvorenými  
váhami a podľa firmy jeho vývoj stál zlomok sumy, ktorú míňali americkí  
konkurenti. Za jediný deň po jeho úspechu stratila Nvidia na burze  
takmer 600 miliárd dolárov.  

*Stav k októbru 2026. Údaje o modeloch, cenách a financiách sa rýchlo menia.*  

## Vznik spoločnosti a zakladateľ  

DeepSeek bol založený v júli **2023** v meste **Chang-čou** (Hangzhou)  
ako odnož kvantitatívneho investičného fondu **High-Flyer**. Fond, ktorý  
na obchodovanie s akciami používa algoritmy a strojové učenie, mal  
k dispozícii veľké výpočtové kapacity. Už pred americkými obmedzeniami  
vývozu čipov do Číny nakúpil približne 10 000 grafických kariet  
Nvidia A100.  

*   **Liang Wen-feng (Liang Wenfeng, CEO):** Absolvent Univerzity  
    Če-ťiang, spoluzakladateľ fondu High-Flyer (2015) a zakladateľ  
    DeepSeeku. Ovláda väčšinový podiel spoločnosti. Na verejnosti  
    vystupuje len zriedka; po úspechu R1 sa stretol s premiérom Li  
    Čchiangom aj s prezidentom Si Ťin-pchingom.  

DeepSeek sa od amerických laboratórií líši aj kultúrou. Pracuje v ňom  
len okolo **160 ľudí** – väčšinou mladí absolventi najlepších čínskych  
univerzít, nie hviezdni výskumníci zo zahraničia. Firma dlho  
neprijímala externých investorov, nevenovala sa marketingu a deklaruje,  
že jej cieľom je výskum smerujúci k AGI, nie rýchly zisk.  

## Cesta k prelomu  

Prvé modely DeepSeeku z roku 2023 (DeepSeek Coder, DeepSeek LLM) zaujali  
najmä odborníkov. Situáciu zmenil model **DeepSeek-V2** (máj 2024), ktorý  
priniesol vlastné technické inovácie a extrémne nízku cenu API. Tá  
odštartovala v Číne **cenovú vojnu** – na DeepSeek museli reagovať aj  
giganti ako Alibaba, ByteDance či Baidu.  

### DeepSeek-V3 (december 2024)  

Model **DeepSeek-V3** mal 671 miliárd parametrov, no vďaka architektúre  
**Mixture of Experts** (MoE) pri každom tokene aktivoval iba 37 miliárd  
z nich. Podľa technickej správy stál záverečný tréning približne  
**5,6 milióna dolárov** na 2 048 čipoch Nvidia H800 – oslabenej verzii  
čipov určenej pre čínsky trh.  

Toto číslo sa stalo predmetom sporov. Nezahŕňa totiž cenu hardvéru,  
predchádzajúce experimenty ani mzdy, takže celkové náklady boli  
mnohonásobne vyššie. Aj tak však V3 ukázal, že špičkový model sa dá  
vytrénovať oveľa efektívnejšie, než sa predpokladalo.  

### DeepSeek-R1 (január 2025)  

**20. januára 2025** DeepSeek zverejnil **R1** – uvažovací (reasoning)  
model porovnateľný s modelom o1 od OpenAI. Kľúčové bolo, že:  

*   Váhy modelu boli voľne dostupné pod licenciou **MIT**, ktorá povoľuje  
    aj komerčné použitie.  
*   DeepSeek zverejnil podrobný popis tréningu. Ukázal, že model sa naučil  
    uvažovať krok za krokom takmer výlučne pomocou **učenia  
    posilňovaním** – bez veľkého množstva ľudských príkladov.  
*   API stálo len zlomok ceny modelu o1.  
*   Spolu s R1 vyšli aj menšie **destilované** modely (od 1,5 do 70  
    miliárd parametrov), ktoré sa dajú spustiť aj na bežnom počítači.  

### „Sputnikový moment" AI  

Aplikácia DeepSeek sa **27. januára 2025** stala najsťahovanejšou  
bezplatnou aplikáciou v americkom App Store a predbehla ChatGPT. V ten  
istý deň klesla akcia Nvidie o približne 17 % a firma stratila takmer  
**600 miliárd dolárov** trhovej hodnoty – najväčší jednodňový prepad  
v histórii amerického akciového trhu.  

Investori sa zľakli, že ak sa dá špičková AI vytrénovať lacno, nebude  
treba toľko drahých čipov. Investor Marc Andreessen nazval R1  
**„sputnikovým momentom AI"** – podobne ako sovietsky Sputnik v roku 1957  
šokoval USA v kozmických pretekoch, DeepSeek ukázal, že Čína v AI  
nezaostáva tak výrazne, ako sa myslelo.  

Trh sa však neskôr spamätal. Lacnejší tréning totiž neznamená menší dopyt  
po čipoch – nižšia cena vedie k širšiemu používaniu AI, a teda k ešte  
väčšej spotrebe výpočtového výkonu (tzv. **Jevonsov paradox**).  

## Technické inovácie  

DeepSeek preslávila najmä efektivita. Musel ju hľadať, pretože kvôli  
americkým sankciám nemal prístup k najvýkonnejším čipom:  

*   **Mixture of Experts (MoE):** Model sa skladá z mnohých  
    „expertov" – menších sietí. Pre každý token sa aktivuje len niekoľko  
    z nich, takže model je obrovský, no jeho prevádzka relatívne lacná.  
*   **Multi-head Latent Attention (MLA):** Úsporná forma mechanizmu  
    pozornosti, ktorá výrazne znižuje pamäťové nároky pri dlhom kontexte.  
*   **Tréning v nízkej presnosti (FP8):** Výpočty s 8-bitovými číslami  
    namiesto 16-bitových šetria pamäť aj čas.  
*   **GRPO:** Variant učenia posilňovaním, ktorý nepotrebuje samostatný  
    hodnotiaci model, a preto je lacnejší.  
*   **DeepSeek Sparse Attention (2025):** Model sa pri dlhom texte  
    nesústredí na všetky predchádzajúce tokeny, len na tie dôležité.  

Vo februári 2025 DeepSeek usporiadal **Open Source Week** a zverejnil  
aj nástroje, na ktorých stavia vlastnú infraštruktúru. V septembri 2025  
vyšiel článok o modeli R1 v prestížnom vedeckom časopise **Nature** – ako  
o prvom veľkom jazykovom modeli, ktorý prešiel nezávislým recenzným  
konaním.  

## Modely DeepSeek  

| Verzia | Dátum | Kľúčové vlastnosti |
| :--- | :--- | :--- |
| **DeepSeek Coder, DeepSeek LLM** | nov. 2023 | Prvé modely s otvorenými váhami |
| **DeepSeekMoE** | jan. 2024 | Architektúra Mixture of Experts |
| **DeepSeekMath** | apr. 2024 | Matematika, predstavenie metódy GRPO |
| **DeepSeek-V2** | máj 2024 | MLA, extrémne nízka cena, cenová vojna v Číne |
| **DeepSeek-V3** | dec. 2024 | 671 mld parametrov (37 mld aktívnych), lacný tréning |
| **DeepSeek-R1** | jan. 2025 | Uvažovací model s otvorenými váhami (MIT) |
| **DeepSeek-R1-0528** | máj 2025 | Vylepšený R1 |
| **DeepSeek-V3.1** | aug. 2025 | Hybridný model s režimom uvažovania aj bez neho |
| **DeepSeek-V3.2-Exp** | sep. 2025 | DeepSeek Sparse Attention, polovičná cena API |
| **DeepSeek-V3.2, V3.2-Speciale** | dec. 2025 | Výkon na úrovni najlepších modelov v matematike |
| **DeepSeek-V4 (preview)** | apr. 2026 | V4-Pro (1,6 bil. parametrov) a V4-Flash (284 mld), kontext 1M |
| **DeepSeek-V4-Flash, V4-Pro** | júl/aug. 2026 | Oficiálne verzie |
| **DeepSeek-V4.1-Flash** | sep. 2026 | Nižšie pamäťové nároky |

Za pozornosť stojí, čo sa **nestalo**: očakávaný model **R2** nikdy  
nevyšiel. Podľa Financial Times sa ho DeepSeek v roku 2025 pod tlakom  
úradov pokúšal trénovať na čínskych čipoch **Huawei Ascend**, no narážal  
na technické problémy. Namiesto samostatnej rady R sa uvažovanie stalo  
súčasťou hlavných modelov (od V3.1).  

Modely **V4** už oficiálne podporujú čínske čipy Huawei Ascend  
a Cambricon. Pre Čínu je to strategicky dôležité: krajina sa snaží  
vybudovať AI nezávislú od amerických technológií.  

## Otvorené váhy: čo to znamená?  

DeepSeek patrí k najvýznamnejším tvorcom **modelov s otvorenými váhami**  
(*open-weight*). Váhy – teda naučené parametre modelu – si môže ktokoľvek  
stiahnuť (napr. z Hugging Face), spustiť na vlastnom hardvéri, upravovať  
a dotrénovať.  

Treba rozlišovať dva pojmy:  

*   **Open-weight:** Zverejnené sú váhy, ale nie tréningové dáta ani celý  
    postup. Sem patrí DeepSeek, Llama od Mety či gpt-oss od OpenAI.  
*   **Open source v plnom zmysle:** Zverejnené je všetko potrebné  
    na zopakovanie tréningu vrátane dát. Takých veľkých modelov je málo.  

Výhody otvorených váh:  

*   **Súkromie:** Dáta nemusia opustiť firmu ani počítač používateľa.  
*   **Nezávislosť:** Model nemôže dodávateľ zmeniť ani vypnúť.  
*   **Cena:** Platí sa len za vlastný hardvér.  
*   **Výskum:** Vedci môžu skúmať vnútro modelu.  

Nevýhodou je, že najväčšie modely (V4-Pro má 1,6 bilióna parametrov)  
potrebujú drahý serverový hardvér a že ochranné mechanizmy sa z voľne  
dostupného modelu dajú odstrániť.  

## DeepSeek pre verejnosť a pre vývojárov  

### Aplikácia DeepSeek  

Chatbot DeepSeek je dostupný na webe (chat.deepseek.com) a v mobilných  
aplikáciách. Je **zadarmo**, ponúka režim hlbokého uvažovania (DeepThink)  
aj vyhľadávanie na webe. Platené plány na spôsob ChatGPT Plus neexistujú.  

### DeepSeek API  

API je **kompatibilné s formátom OpenAI**, takže stačí knižnica `openai`  
a iná adresa servera. Ceny za 1 milión tokenov (október 2026, v špičke):  

| Model | Vstup | Výstup | Kontext |
| :--- | ---: | ---: | :--- |
| **deepseek-flash** (V4.1-Flash) | 0,30 $ | 1,20 $ | 1M tokenov |
| **deepseek-v4-pro** (V4-Pro) | 1,32 $ | 3,96 $ | 1M tokenov |

Špička je v pracovné dni ráno a dopoludnia podľa nášho času. Popoludní,  
večer a cez víkend platí polovičná cena a pri opakovanom vstupe  
(*cache hit*) je cena ešte rádovo nižšia.  
Pre porovnanie: GPT-6 Astra stojí 10 $ a 50 $ – DeepSeek V4-Pro je teda  
pri výstupe zhruba **desaťkrát lacnejší**.  

```python
from openai import OpenAI

# DeepSeek používa formát OpenAI API – stačí zmeniť adresu servera
client = OpenAI(
    base_url="https://api.deepseek.com",
    api_key="...",  # kľúč z platform.deepseek.com
)

response = client.chat.completions.create(
    model="deepseek-flash",
    messages=[
        {"role": "system", "content": "Si nápomocný asistent."},
        {"role": "user", "content": "Vysvetli mi, čo je Mixture of Experts."},
    ],
)

print(response.choices[0].message.content)
```

V praxi je lepšie kľúč načítať z premennej prostredia (napr.  
`os.environ["DEEPSEEK_API_KEY"]`) a nepísať ho priamo do kódu.  

### Spustenie na vlastnom počítači  

Menšie destilované modely R1 sa dajú spustiť lokálne napríklad cez  
nástroj **Ollama**. Model s 8 miliardami parametrov zvládne aj bežný  
notebook s 16 GB pamäte:  

```bash
ollama run deepseek-r1:8b
```

Takto spustený model nikam neposiela dáta a funguje aj bez internetu.  

## Kontroverzie a riziká  

### Cenzúra  

Modely DeepSeek sú podriadené čínskym predpisom, ktoré od AI vyžadujú  
súlad so „socialistickými hodnotami". Oficiálny chatbot preto odmieta  
odpovedať o masakri na námestí Tchien-an-men, o postavení Tchaj-wanu či  
o Ujguroch, prípadne ponúka oficiálny postoj Pekingu. Časť cenzúry je  
zabudovaná priamo v aplikácii, časť aj vo váhach modelu – prejavuje sa  
preto čiastočne aj pri lokálnom spustení.  

### Ochrana údajov  

Podľa zásad ochrany súkromia ukladá DeepSeek údaje používateľov  
na serveroch v Číne, kde naň dopadá povinnosť spolupracovať so štátnymi  
orgánmi. V januári 2025 bezpečnostná firma Wiz objavila verejne prístupnú  
databázu DeepSeeku s históriou konverzácií a API kľúčmi.  

Viaceré krajiny preto obmedzili používanie DeepSeeku:  

*   **Taliansko** zablokovalo aplikáciu už v januári 2025.  
*   **Austrália, Taiwan a Južná Kórea** zakázali DeepSeek na vládnych  
    zariadeniach, Južná Kórea dočasne pozastavila aj jeho sťahovanie.  
*   **USA** nariadili odstrániť DeepSeek zo zariadení ministerstva obrany  
    a spravodajských služieb.  
*   **Nemecko** žiadalo Apple a Google o odstránenie aplikácie z obchodov  
    pre porušovanie pravidiel GDPR.  

Tieto riziká sa týkajú najmä oficiálnej aplikácie a API. Model  
s otvorenými váhami spustený na vlastnom hardvéri údaje do Číny  
neposiela.  

### Obvinenia z destilácie  

**Destilácia** je technika, pri ktorej sa menší model učí z odpovedí  
silnejšieho modelu. OpenAI už v januári 2025 tvrdila, že DeepSeek  
mohol takto využiť jej modely. Vo februári 2026 Anthropic obvinila  
DeepSeek a ďalšie čínske firmy, že cez tisíce falošných účtov  
vygenerovali milióny konverzácií s Claude na trénovanie vlastných  
modelov. DeepSeek obvinenia nekomentoval.  

### Čipy a sankcie  

USA obmedzujú vývoz najvýkonnejších čipov do Číny. Americké úrady  
a médiá opakovane skúmali, či sa DeepSeek k zakázaným čipom Nvidia  
nedostal cez sprostredkovateľov v tretích krajinách. Úspech DeepSeeku  
zároveň rozprúdil debatu, či sankcie fungujú – alebo Čínu len  
motivujú k efektívnejším riešeniam a vlastným čipom.  

## Čínsky AI ekosystém  

DeepSeek nie je v Číne sám. Medzi ďalších významných hráčov patria:  

*   **Alibaba (Qwen):** Rodina modelov s otvorenými váhami, ktorá patrí  
    k najpoužívanejším na svete, najmä ako základ pre ďalšie dotrénovanie.  
*   **Moonshot AI (Kimi):** Modely zamerané na dlhý kontext a agentov.  
*   **Zhipu AI (GLM):** Jedna z prvých čínskych AI firiem, spin-off  
    univerzity Cching-chua.  
*   **MiniMax, ByteDance (Doubao), Baidu (Ernie), Tencent (Hunyuan).**  

Typickým znakom čínskej AI je **dôraz na otvorené váhy**. Kým najlepšie  
americké modely sú uzavreté, čínske firmy svoje modely väčšinou  
zverejňujú – čím si získavajú vývojárov po celom svete a vplyv  
na globálny ekosystém.  

## Financie  

DeepSeek dlho fungoval výlučne z peňazí fondu High-Flyer. V roku 2026  
však začal získavať externý kapitál:  

*   **Máj 2026:** Prvé investičné kolo vo výške **7 miliárd dolárov**  
    pri ocenení **52 miliárd**.  
*   **Október 2026:** Podľa čínskych médií sa blíži k uzavretiu kola  
    okolo **100 miliárd jüanov** (približne 14 miliárd dolárov)  
    pri ocenení približne 500 miliárd jüanov (okolo 70 miliárd dolárov).  

Anualizované príjmy DeepSeeku sa podľa médií v roku 2026 dostali  
nad **1 miliardu dolárov**. To je síce rýchly rast, no stále zlomok  
príjmov OpenAI či Anthropic. Médiá informujú aj o príprave vstupu  
na burzu, najskôr v roku 2027.  

## Porovnanie DeepSeek, OpenAI a Anthropic  

| Vlastnosť | DeepSeek | OpenAI | Anthropic |
| :--- | :--- | :--- | :--- |
| **Sídlo** | Chang-čou, Čína | San Francisco, USA | San Francisco, USA |
| **Založenie** | 2023 | 2015 | 2021 |
| **Zamestnanci** | ~160 | tisíce | tisíce |
| **Váhy modelov** | otvorené (MIT) | uzavreté (okrem gpt-oss) | uzavreté |
| **Najsilnejší model** | DeepSeek-V4-Pro | GPT-6 Astra | Claude Fable 5.1 |
| **Cena výstupu top modelu** | ~4 $ / 1M tokenov | 50 $ / 1M tokenov | 50 $ / 1M tokenov |
| **Ocenenie (2026)** | ~70 mld $ | ~850 mld $ | ~965 mld $ |
| **Hlavné riziká** | cenzúra, údaje v Číne | koncentrácia moci | koncentrácia moci |

Rozdiel v cenách aj ocenení ukazuje dva odlišné prístupy: americké  
laboratóriá investujú stovky miliárd do čo najsilnejších modelov,  
DeepSeek ponúka o niečo slabšie, no rádovo lacnejšie a otvorené modely.  

## Zhrnutie kapitoly  

*   **DeepSeek** založil v roku 2023 **Liang Wen-feng** ako odnož  
    kvantitatívneho fondu High-Flyer. Pracuje v ňom len okolo 160 ľudí.  
*   Model **DeepSeek-R1** (január 2025) ponúkol výkon porovnateľný  
    s najlepšími americkými modelmi, s otvorenými váhami a za zlomok ceny.  
    Spôsobil historický prepad akcií Nvidie.  
*   Úspech DeepSeeku stojí na **efektivite**: MoE, MLA, tréning v FP8,  
    učenie posilňovaním s GRPO a riedka pozornosť.  
*   Aktuálna generácia **V4** má kontext 1 milión tokenov a podporuje  
    čínske čipy Huawei Ascend.  
*   **Otvorené váhy** umožňujú spustiť model lokálne, bez posielania dát  
    tretej strane.  
*   Hlavné riziká predstavujú **cenzúra**, **ukladanie údajov v Číne**  
    a obvinenia z **destilácie** amerických modelov. Viaceré krajiny  
    obmedzili používanie DeepSeeku vo verejnej správe.  
*   DeepSeek je súčasťou širšieho čínskeho ekosystému (Qwen, Kimi, GLM),  
    ktorý stavia na otvorených modeloch.  

## Otázky a diskusia  

1.  Prečo trh v januári 2025 zareagoval na DeepSeek takou panikou?  
    Bola táto reakcia opodstatnená?  
2.  Čo všetko by ste museli započítať do skutočných nákladov na vývoj  
    modelu? Prečo je číslo 5,6 milióna dolárov zavádzajúce?  
3.  Fungujú americké sankcie na čipy? Mohli naopak Čínu motivovať  
    k inováciám?  
4.  Aký je rozdiel medzi modelom s otvorenými váhami a open-source  
    modelom? Prečo na tom záleží?  
5.  Použili by ste DeepSeek v škole alebo vo firme? Za akých podmienok  
    (oficiálna aplikácia, API, lokálne spustenie)?  
6.  Ako by ste overili, či je model cenzurovaný? Vyskúšajte rovnakú  
    citlivú otázku v rôznych modeloch a porovnajte odpovede.  
7.  Je destilácia odpovedí iného modelu legitímnou technikou, alebo  
    krádežou duševného vlastníctva?  
8.  Prečo čínske firmy zverejňujú svoje modely, kým americké ich  
    väčšinou držia uzavreté? Aké sú strategické dôvody oboch strán?  

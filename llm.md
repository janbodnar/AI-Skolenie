# Veľké jazykové modely (LLM)  
  
Jazykové modely (angl. *Language Models*, skrátene LM) sú systémy umelej  
inteligencie, ktoré sa učia zo vzorov v texte. Ich základnou úlohou je  
predpovedať ďalší token, teda slovo alebo časť slova, v sekvencii.  
  
**Veľké jazykové modely** (Large Language Models, LLM) využívajú veľké  
množstvo tréningových dát a výpočtový výkon. Dokážu:  
  
* generovať text v prirodzenom jazyku;  
* odpovedať na otázky a vysvetľovať zložité pojmy;  
* sumarizovať dokumenty a prekladať medzi jazykmi;  
* písať, kontrolovať a upravovať počítačový kód;  
* riešiť logické úlohy a analyzovať neštruktúrované dáta.  
  
> **Kľúčová myšlienka:** LLM nie sú databázy faktov, ale generátory  
> pravdepodobných pokračovaní. Nemajú „pravdu“ v ľudskom zmysle a môžu  
> vytvoriť presvedčivú, no nesprávnu odpoveď.  
  
## Ako LLM fungujú? (zjednodušený pohľad)  
  
Ich princíp možno rozdeliť do štyroch krokov:  
  
1. **Tokenizácia:** Vstupný text sa rozdelí na menšie jednotky nazývané  
   *tokeny*. Môžu to byť celé slová, korene slov alebo ich časti.  
2. **Embedding:** Každý token sa prevedie na vektor čísel, ktorý zachytáva  
   jeho význam a vzťah k ostatným tokenom.  
3. **Spracovanie:** Architektúra *Transformer* používa mechanizmus  
   *attention*, ktorý umožňuje modelu sústrediť sa na dôležité časti  
   kontextu bez ohľadu na ich vzdialenosť.  
4. **Predikcia:** Model vypočíta pravdepodobnosti možných nasledujúcich  
   tokenov a vyberie jeden z nich. Proces sa opakuje, kým nevznikne  
   celá odpoveď.  
  
### Slovník základných pojmov  
  
| Pojem | Vysvetlenie |  
|-------|-------------|  
| **Token** | Základná jednotka textu pre model, napríklad slovo alebo jeho časť. |  
| **Parameter** | Interná premenná učená počas tréningu. Modely ich majú milióny až bilióny. |  
| **Kontextové okno** | Maximálne množstvo vstupu a výstupu, ktoré model spracuje naraz. |  
| **Halucinácia** | Presvedčivo znejúci, no fakticky nesprávny alebo vymyslený obsah. |  
  
## Klasifikácia jazykových modelov  
  
LLM možno deliť podľa architektúry, dostupnosti váh a veľkosti.  
  
### A. Podľa architektúry  
  
* **Decoder-only (napr. GPT, Llama):** Autoregresívne modely určené najmä  
  na generovanie textu.  
* **Encoder-decoder (napr. T5, BART):** Vhodné na transformácie, napríklad  
  preklad alebo sumarizáciu.  
* **Mixture-of-Experts (MoE):** Pri každom tokene sa aktivuje iba časť  
  expertov, čo môže znížiť výpočtové náklady pri zachovaní veľkej kapacity.  
  
### B. Podľa otvorenosti prístupu  
  
* **Open weights:** Váhy sú dostupné na stiahnutie, licencia však môže  
  obsahovať obmedzenia. Príklady: Llama, Mistral Large 3, Qwen.  
* **Proprietary:** Model je dostupný najmä cez API alebo webové rozhranie.  
  Príklady: GPT, Claude, Gemini.  
  
Pojmy *open weights* a *open source* nie sú zameniteľné. Dostupné váhy  
neznamenajú, že sú otvorené aj tréningové dáta, kód a licencia.  
  
### C. Podľa veľkosti  
  
* **Small (1B – 8B):** Vhodné na lokálne použitie a jednoduché úlohy.  
* **Medium (8B – 70B):** Kompromis medzi výkonom a nárokmi na hardvér.  
* **Large (70B+):** Výkonnejšie modely s vyššími nárokmi na prevádzku.  
  
## Kľúčový koncept: spôsob „uvažovania“ modelov  
  
### Klasické generatívne LLM  
  
Tieto modely generujú odpoveď token za tokenom bez osobitného režimu  
rozšíreného uvažovania. Sú rýchle a vhodné na konverzáciu, preklady,  
sumarizáciu a tvorivé písanie. Pri dlhom plánovaní, matematike alebo  
zložitom kóde však môžu robiť viac chýb.  
  
Príklady predstavujú rýchle alebo všeobecné varianty rodín GPT, Claude,  
Gemini, Mistral a Llama.  
  
### Uvažujúce (reasoning) LLM  
  
Tieto modely používajú dodatočný výpočtový čas na plánovanie, kontrolu alebo  
rozklad úlohy na podúlohy. Zvyčajne sú lepšie v matematike, programovaní,  
vedeckom uvažovaní a viacstupňových úlohách, ale bývajú pomalšie a drahšie.  
  
Príklady sú GPT-6 Astra, GPT-5.6 Sol, Claude Fable 5.1 a Gemini 3.1 Pro.  
  
Používateľ nemusí od modelu vyžadovať zverejnenie interného chain-of-thought.  
Na kontrolu kvality je vhodnejšie žiadať stručné zdôvodnenie, overiteľné  
medzikroky alebo výsledky testov.  
  
## Prehľad významných modelov (stav k 9. septembru 2026)  
  
Nasledujúci prehľad uvádza aktuálne alebo významné modely. Označenie  
„preview“ znamená, že model sa môže meniť a nemusí mať stabilný životný  
cyklus.  
  
| Model | Vývojár / organizácia | Krajina pôvodu | Typ prístupu |  
| :--- | :--- | :--- | :--- |  
| **GPT-6 Astra** | OpenAI | USA | Closed |  
| **GPT-5.6 Sol / Terra / Luna** | OpenAI | USA | Closed |  
| **Claude Fable 5.1** | Anthropic | USA | Closed |  
| **Claude Opus 5 / Sonnet 5** | Anthropic | USA | Closed |  
| **Claude Haiku 4.5** | Anthropic | USA | Closed |  
| **Gemini 3.8 Flash** | Google DeepMind | USA | Closed |  
| **Gemini 3.1 Pro** | Google DeepMind | USA | Closed, preview |  
| **Grok 4.x** | xAI | USA | Closed |  
| **Llama 4 (Scout / Maverick)** | Meta | USA | Open weights |  
| **Mistral Large 3** | Mistral AI | Francúzsko | Open weights |  
| **Mistral Medium 3.5 / Small 4** | Mistral AI | Francúzsko | API / open weights |  
| **Qwen 3** | Alibaba Cloud | Čína | Open weights / API |  
| **DeepSeek-V4 Flash / Pro** | DeepSeek | Čína | API; dostupné varianty váh |  
| **GLM-5** | Z.ai | Čína | Open weights / API |  
| **Kimi K2** | Moonshot AI | Čína | Open weights / API |  
  
Názvy a dostupnosť modelov sa menia rýchlejšie než učebnicové texty. Pri  
integrácii preto treba overiť aktuálny model ID, dokumentáciu, licenciu,  
cenu, kontextové okno a plánované vyradenie z prevádzky.  
  
## Models.dev: otvorená databáza modelov  
  
[Models.dev](https://models.dev) je otvorená databáza umelej inteligencie  
s prehľadom modelov, laboratórií a poskytovateľov. Zdrojový kód je dostupný  
na GitHube (projekt sst/models.dev).  
  
Každý model má na stránke vlastný záznam s týmito údajmi:  
  
* **Lab** a **Providers:** kto model vyvinul a koľko poskytovateľov ho  
  ponúka;  
* **Context / Output / Input:** veľkosť kontextového okna a maximálna dĺžka  
  výstupu v tokenoch;  
* **Reasoning, Tool Call, Structured, Temperature:** podpora uvažovania,  
  volania nástrojov, štruktúrovaného výstupu a nastavenia teploty;  
* **Weights:** či sú váhy modelu verejne dostupné (*Open*), alebo nie  
  (*Closed*);  
* **Price:** cena za milión vstupných a výstupných tokenov;  
* **Release / Updated:** dátum vydania a poslednej aktualizácie záznamu.  
  
Stránku možno filtrovať a vyhľadávať podľa názvu modelu, laboratória alebo  
poskytovateľa. Je užitočná na porovnanie kontextových okien, cien a  
funkcií pred výberom modelu pre konkrétne použitie.  
  
Údaje na stránke sa menia často a nemusia byť úplné, najmä pri novších  
modeloch a preview verziách. Pri rozhodovaní o nasadení treba overiť  
aktuálne hodnoty u konkrétneho poskytovateľa.  
  
## Najčastejšie označenia modelov  
  
Tieto názvy nie sú univerzálnym štandardom. Ich význam závisí od  
konkrétneho poskytovateľa.  
  
| Označenie | Čo zvyčajne znamená | Typické využitie |  
| :--- | :--- | :--- |  
| **Flash / Mini / Lite** | Rýchlejší alebo úspornejší model | Veľké objemy, chatboty, automatizácia |  
| **Pro / Ultra** | Výkonnejšia alebo prémiová úroveň | Analýza, kódovanie, zložité úlohy |  
| **Thinking / Reasoning** | Viac výpočtového času na riešenie | Matematika, plánovanie, programovanie |  
| **Instruct / Chat** | Doladenie na pokyny alebo konverzáciu | Asistenti a automatizované spracovanie |  
| **Base** | Základný model bez konverzačného doladenia | Ďalšie dolaďovanie a výskum |  
| **Vision / Multimodal** | Práca s obrazom, zvukom alebo videom | Dokumenty, grafy, multimédiá |  
| **Coder / Code** | Optimalizácia na programovanie | Tvorba, kontrola a úprava kódu |  
| **Long context** | Veľké kontextové okno | Dlhé dokumenty a kódové základne |  
| **Embedding** | Prevod dát na vektorové reprezentácie | Vyhľadávanie, RAG, podobnosť |  
| **MoE** | Aktivácia iba časti expertov pri požiadavke | Efektívne veľké modely |  
| **Quantized / Q4 / Q8** | Nižšia numerická presnosť a menšia pamäť | Lokálne spúšťanie modelov |  
  
## Ako sa v označeniach orientovať?  
  
Pri výbere modelu nestačí sledovať marketingový názov. Dôležitejšie je  
posudzovať:  
  
* kvalitu výstupu na vlastnej úlohe;  
* schopnosť uvažovania a používania nástrojov;  
* rýchlosť, cenu a limity služby;  
* veľkosť kontextového okna a maximálnu dĺžku výstupu;  
* multimodálne schopnosti;  
* licenciu, ochranu dát a životný cyklus modelu.  
  
Na jednoduché a objemné úlohy sa často oplatí rýchly model. Na komplexné  
rozhodovanie, analýzu, programovanie alebo plánovanie má zmysel výkonnejší  
model s režimom reasoning.  
  
## Životný cyklus: ako sa LLM trénujú?  
  
Vývoj modelu zvyčajne prebieha v týchto fázach:  
  
1. **Predtrénovanie:** Model sa učí štatistické vzťahy v texte, kóde a  
   ďalších dátach. Výsledkom je *base model*.  
2. **Doladenie (fine-tuning):** Model sa trénuje na príkladoch otázok,  
   odpovedí a pokynov.  
3. **Zosúladenie (alignment):** Pomocou metód ako RLHF, DPO alebo syntetickej  
   spätnej väzby sa zlepšuje užitočnosť, bezpečnosť a dodržiavanie pokynov.  
4. **Vyhodnotenie a nasadenie:** Model sa testuje na benchmarkoch, vlastných  
   úlohách, bezpečnosti a odolnosti voči zneužitiu.  
  
## Praktické využitie a limity  
  
### Kde sa LLM používajú?  
  
* asistenti a chatboty;  
* generovanie, kontrola a vysvetľovanie kódu;  
* extrakcia informácií a sumarizácia dokumentov;  
* vyhľadávanie s RAG a práca s podnikovými dátami;  
* vzdelávanie, preklady a jazykové korektúry;  
* agentické workflow, v ktorých model používa nástroje.  
  
### Na čo si dať pozor?  
  
1. **Halucinácie:** Model môže s istotou tvrdiť nepravdu.  
2. **Kontextové okno:** Staršie informácie môžu byť mimo dostupného kontextu.  
3. **Predpojatosť:** Výstup môže odrážať nedostatky tréningových dát.  
4. **Knowledge cutoff:** Model nemusí poznať najnovšie udalosti bez  
   vyhľadávania.  
5. **Bezpečnosť a súkromie:** Citlivé dáta môžu byť nesprávne spracované  
   alebo odoslané poskytovateľovi služby.  
6. **Nestabilné API:** Alias ako `latest` sa môže zmeniť bez zmeny kódu.  
  
Kritické tvrdenia treba overovať. Pri produkčnej integrácii je vhodné  
používať konkrétne verzie modelov, logovať vstupy a výstupy a mať  
regresné testy.  
  
## Budúcnosť  
  
Vývoj sa uberá tromi hlavnými smermi:  
  
1. **Agentická AI:** Modely plánujú úlohy, používajú nástroje a vykonávajú  
   viac krokov s obmedzeným dohľadom človeka.  
2. **Multimodalita:** Text, obraz, zvuk a video sa spracúvajú v jednom  
   systéme.  
3. **Efektivita a edge AI:** Menšie, kvantizované modely bežia lokálne, čo  
   znižuje latenciu, náklady a potrebu posielať dáta do cloudu.  
  
## Otázky a diskusia  
  
Pri zložitých úlohách má význam vybrať model alebo režim reasoning, ktorý  
venuje problému viac výpočtového času. Samotný názov modelu však nie je  
zárukou správnosti. Výsledok treba posudzovať podľa testov, zdrojov,  
overiteľných krokov a konkrétneho použitia.  

# Deep Search – Hĺbkové vyhľadávanie s podporou umelej inteligencie

**Deep Search** (hĺbkové vyhľadávanie) je pokročilá technológia, ktorá kombinuje veľké jazykové 
modely (LLM) s inteligentným vyhľadávaním informácií. Na rozdiel od tradičného vyhľadávania, ktoré hľadá 
presné zhody kľúčových slov, deep search:

*   **Chápe zámer používateľa** – analyzuje kontext otázky, nie len jednotlivé slová.
*   **Prehľadáva viac zdrojov naraz** – dokáže simultánne skenovať webové stránky, databázy, dokumenty aj odborné články.
*   **Syntetizuje odpoveď** – namiesto zoznamu odkazov poskytuje štruktúrovanú, overenú odpoveď s citáciami.
*   **Plánuje vyhľadávanie** – rozkladá komplexnú otázku na podotázky a postupne ich rieši.

> **Príklad z praxe:**  
> *Tradičné vyhľadávanie:* Zadáte "klíma Slovensko 2024" → dostanete zoznam článkov s týmto výrazom.  
> *Deep Search:* Zadáte rovnakú otázku → systém pochopí, že chcete vedieť o teplotných trendoch, extrémnych
javoch a projekciách → vyhľadá relevantné štúdie, porovná dáta z rôznych zdrojov → vygeneruje súhrnnú odpoveď s odkazmi na zdroje.

Deep search predstavuje prechod od **vyhľadávania informácií** k **získavaniu poznatkov**.

## 2. Ako Deep Search technicky funguje?

Architektúra deep search systémov sa zvyčajne skladá z niekoľkých kľúčových komponentov:

### 2.1 Fázy spracovania dotazu

```
1. ANALÝZA DOTAZU
   ↓
   • Rozpoznanie zámeru (informačný, transakčný, navigačný)
   • Identifikácia entít a kľúčových pojmov
   • Rozklad komplexnej otázky na podotázky

2. PLÁNOVANIE VYHĽADÁVANIA
   ↓
   • Výber vhodných zdrojov (web, databázy, interné dokumenty)
   • Generovanie optimalizovaných vyhľadávacích reťazcov
   • Nastavenie filtrov (jazyk, čas, dôveryhodnosť zdroja)

3. RETRIEVAL (ZÍSKAVANIE DÁT)
   ↓
   • Paralelné vyhľadávanie vo viacerých zdrojoch
   • Použitie vektorových databáz pre sémantickú podobnosť
   • Hybridné vyhľadávanie: keyword + embedding similarity

4. HODNOTENIE A RERANKING
   ↓
   • Skórovanie relevancie nájdených dokumentov
   • Kontrola dôveryhodnosti zdrojov a aktuálnosti
   • Odstránenie duplicit a nekonzistentných informácií

5. SYNTÉZA ODPOVEDE
   ↓
   • Kombinácia informácií z viacerých zdrojov
   • Generovanie koherentnej odpovede pomocou LLM
   • Pridanie citácií a odkazov na overenie

6. OVERENIE A REFLEXIA
   ↓
   • Kontrola konzistencie a faktickej správnosti
   • Identifikácia medzier v odpovedi
   • Možnosť doplnkového vyhľadávania
```

### 2.2 Kľúčové technológie

| Technológia | Úloha v Deep Search |
|-------------|-------------------|
| **Embedding modely** | Prevádzajú text na číselné vektory, umožňujú sémantické vyhľadávanie (napr. "auto" a "vozidlo" sú blízko seba) |
| **Vektorové databázy** | Ukladajú a umožňujú rýchle vyhľadávanie podobných dokumentov (Pinecone, Weaviate, Chroma) |
| **RAG (Retrieval-Augmented Generation)** | Architektúra, ktorá kombinuje získavanie informácií s generovaním odpovedí |
| **Chain-of-Thought prompting** | Umožňuje modelu "myslieť krok za krokom" pri plánovaní vyhľadávania |
| **Re-ranking algoritmy** | Zlepšujú poradie výsledkov podľa komplexnejšej relevancie, nie len keyword match |

---

## 3. Deep Search vs. Tradičné vyhľadávanie

| Kritérium | Tradičné vyhľadávanie | Deep Search |
|-----------|---------------------|-------------|
| **Základný princíp** | Keyword matching, PageRank | Sémantické pochopenie + LLM syntéza |
| **Vstup** | Presné kľúčové slová | Prirodzený jazyk, komplexné otázky |
| **Výstup** | Zoznam odkazov (SERP) | Štruktúrovaná odpoveď s citáciami |
| **Kontext** | Obmedzený na snippet | Celý dokument + cross-referencing |
| **Adaptivita** | Statické algoritmy | Dynamické plánovanie podľa dotazu |
| **Overiteľnosť** | Používateľ overuje sám | Systém poskytuje zdroje a citácie |
| **Rýchlosť** | Milisekundy | Sekundy až desiatky sekúnd |

> **Dôležité:** Deep Search nie je náhrada tradičného vyhľadávania, ale doplnok pre komplexnejšie úlohy, kde je potrebná
> analýza a syntéza informácií.

---

## 4. Architektúra RAG: Srdce moderného Deep Search

**Retrieval-Augmented Generation (RAG)** je kľúčová architektúra, ktorá umožňuje LLM pracovať s aktuálnymi a externými dátami.

### 4.1 Prečo je RAG dôležitý?

LLM majú dva základné obmedzenia:

1.  **Statické vedomosti** – tréningové dáta majú "cut-off" dátum a model nevie o udalostiach po tomto dátume.
2.  **Hallucinácie** – model môže generovať presvedčivo vyzerajúce, ale nesprávne informácie.

RAG tieto obmedzenia rieši tým, že:

*   **Pred generovaním** odpovede vyhľadá relevantné informácie z externých zdrojov.
*   **Vloží tieto informácie** do kontextu promptu pre LLM.
*   **Model generuje odpoveď** na základe kombinácie svojich vedomostí a poskytnutých faktov.

### 4.2 Schéma RAG pipeline

```
[User Query]
      ↓
[Query Understanding & Expansion]
      ↓
[Retriever: Vector DB + Keyword Search]
      ↓
[Re-ranking & Filtering]
      ↓
[Context Assembly: Top-K relevant chunks]
      ↓
[LLM Prompt: "Answer based on: {context}"]
      ↓
[Generated Response + Citations]
      ↓
[Optional: Self-verification step]
```

### 4.3 Výhody RAG

✅ **Aktuálnosť** – odpovede sú založené na najnovších dostupných dátach  
✅ **Špecializácia** – možnosť pracovať s internými firemnými dokumentmi  
✅ **Transparentnosť** – odpovede obsahujú citácie zdrojov  
✅ **Efektivita** – nie je potrebné pretrénovávať model pri zmene dát  
✅ **Zníženie halucinácií** – model je "uzemnený" v reálnych dokumentoch

### 4.4 Výzvy pri implementácii

⚠️ **Kvalita retrievalu** – ak retriever nájde irelevantné dokumenty, LLM vygeneruje zlú odpoveď  
⚠️ **Kontextové okno** – LLM majú limit na dĺžku vstupu, treba strategicky vyberať chunky  
⚠️ **Latencia** – viac krokov = pomalšia odpoveď, dôležité pre UX  
⚠️ **Hodnotenie kvality** – ako objektívne merať, či odpoveď je "dobrá"?

---

## 5. Príklady Deep Search implementácií

### 5.1 Google Deep Search (AI Mode)

*   **Funkcia:** Rozkladá komplexné otázky na podotázky, vykonáva viacnásobné vyhľadávania a syntetizuje odpoveď.
*   **Špecifiká:** Klade doplňujúce otázky na upresnenie zámeru, poskytuje štruktúrované výstupy.
*   **Použitie:** Výskum, porovnávacie analýzy, technické dotazy.

### 5.2 DeepSeek s internetovým vyhľadávaním

*   **Funkcia:** Kombinuje reasoning schopnosti modelu s reálnym časom vyhľadávania na webe.
*   **Špecifiká:** Model najprv "rozmyslí" stratégiu vyhľadávania, potom vyhľadá, potom syntetizuje.
*   **Použitie:** Technické otázky, aktuálne udalosti, fakt-checking.

### 5.3 Perplexity AI
*   **Funkcia:** Špecializovaný "answer engine" s dôrazom na citovanie zdrojov a aktuálnosť.
*   **Špecifiká:** Automaticky vyhľadáva, sumarizuje a uvádza zdroje, podporuje follow-up otázky.
*   **Použitie:** Rýchly výskum, akademické otázky, business intelligence.

### 5.4 IBM Deep Search (pre vedu a podnikanie)
*   **Funkcia:** Špecializovaný na hĺbkovú analýzu technických dokumentov, patentov a výskumných prác.
*   **Špecifiká:** Extrahuje štruktúrované dáta z PDF, vytvára knowledge graphs, podporuje expertné domény.
*   **Použitie:** Výskum a vývoj, patentové analýzy, farmaceutický priemysel.

---

## 6. Praktické použitie Deep Search

### Kedy použiť Deep Search?

| Scenár | Prečo Deep Search? |
|--------|-------------------|
| **Komplexný výskum** | Rozkladá tému na aspekty, hľadá v odborných zdrojoch, syntetizuje závery |
| **Fakt-checking** | Porovnáva viacero zdrojov, identifikuje konzistentné informácie |
| **Technické dotazy** | Hľadá v dokumentácii, fóre, GitHub issues a poskytuje kontextové riešenie |
| **Porovnávacie analýzy** | Získava dáta o viacerých produktoch/službách a vytvára porovnávaciu tabuľku |
| **Aktuálne udalosti** | Prekonáva obmedzenie "knowledge cutoff" LLM vyhľadávaním na webe |

### Kedy stačí tradičné vyhľadávanie?

*   Jednoduché faktografické otázky ("Hlavné mesto Francúzska")
*   Navigačné dotazy ("webová stránka firmy X")
*   Rýchle overenie existencie informácie
*   Úlohy, kde používateľ chce sám preskúmať zdroje

---

## 7. Etické aspekty a limity Deep Search

### 7.1 Riziká a obmedzenia

🔴 **Závislosť na kvalite zdrojov**  
Deep Search môže syntetizovať odpoveď z nekvalitných alebo zavádzajúcich zdrojov. *"Garbage in, garbage out."*

🔴 **Bias vo vyhľadávaní**  
Algoritmy môžu preferovať určité typy zdrojov alebo jazyky, čo skresľuje výsledky.

🔴 **Ilúzia objektivity**  
Štruktúrovaná odpoveď môže pôsobiť autoritatívnejšie, než si zaslúži – používateľ musí stále kriticky hodnotiť.

🔴 **Súkromie a sledovanie**  
Komplexné dotazy môžu odhaliť citlivé informácie o zámeroch používateľa.

🔴 **Energetická náročnosť**  
Viacnásobné vyhľadávania + LLM generovanie = vyššia spotreba výpočtových zdrojov.

### 7.2 Best practices pre používateľov

✅ **Vždy overujte kritické informácie** – citácie sú nápomocné, ale nenahrádzajú vlastný úsudok  
✅ **Buďte špecifickí v dotazoch** – čím presnejší zámer, tým lepšie výsledky  
✅ **Používajte follow-up otázky** – deep search systémy často podporujú iteratívne spresňovanie  
✅ **Kontrolujte dátumy zdrojov** – aktuálnosť je kľúčová pri rýchlo sa meniacich témach  
✅ **Porovnávajte viacero systémov** – rôzne implementácie môžu poskytnúť rôzne perspektívy



## 8. Qwen Chat a inteligentné vyhľadávanie: Web Search vs. Deep Research


Moderné konverzačné modely, ako je Qwen Chat, už nie sú len pasívnymi generátormi textu.  
Vďaka integrácii s externými nástrojmi dokážu **proaktívne vyhľadávať informácie na webe**,  
čím výrazne zvyšujú presnosť a aktuálnosť svojich odpovedí. V tejto sekcii si vysvetlíme  
dva kľúčové módy práce s informáciami: štandardné vyhľadávanie (Web Search) a hĺbkový výskum (Deep Research).

###  Štandardné vyhľadávanie (Web Search)

**Web Search** je funkcia, ktorú model aktivuje **autonómne**, ak vyhodnotí, že na zodpovedanie  
otázky potrebuje externé, aktuálne alebo špecifické dáta.

### Kedy sa spúšťa?

| Situácia | Príklad otázky |
|----------|---------------|
| **Faktografické dotazy** | „Kto získal Nobelovu cenu za fyziku v roku 2025?" |
| **Aktuálne udalosti** | „Aké sú najnovšie výsledky volieb v krajine X?" |
| **Overenie faktov** | „Je pravda, že firma Y vydala nový produkt?" |
| **Špecifické údaje** | „Aká je aktuálna cena elektriny na Slovensku?" |

### Ako to funguje?
1. Model analyzuje otázku a identifikuje potrebu externých dát.
2. V pozadí vykoná jedno alebo viac vyhľadávacích dopytov.
3. Prečíta a vyhodnotí obsah relevantných webových stránok.
4. Syntetizuje stručnú, fakticky podloženú odpoveď s odkazmi na zdroje.

> 💡 **Pedagogická poznámka:** Tento mechanizmus ilustruje princíp **RAG (Retrieval-Augmented Generation)** –
>  model kombinuje svoje vnútorné vedomosti s externými zdrojmi v reálnom čase.

## Režim Deep Research (Hĺbkový výskum)

**Deep Research** je špecializovaný, viacstupňový režim určený pre komplexné tézy, ktoré vyžadujú štruktúrovanú  
analýzu, porovnanie viacerých zdrojov alebo tvorbu rozsiahlejších výstupov.

### Kedy použiť Deep Research?

- Pri otázkach typu: *„Porovnaj vplyv AI na vzdelávacie systémy v EÚ a Ázii."*
- Pri potrebe vytvoriť rešerš, prehľadovú štúdiu alebo analytický materiál.
- Keď potrebujete nielen odpoveď, ale aj **kontext, zdroje a štruktúru**.

### Charakteristické znaky Deep Research

| Vlastnosť | Popis |
|-----------|-------|
| **Plánovanie** | Model si otázku rozloží na podotázky a vytvorí výskumný plán. |
| **Iteratívne vyhľadávanie** | Cyklus: *vyhľadaj → vyhodnoť → doplň → vyhľadaj znova*. |
| **Syntéza viacerých zdrojov** | Porovnáva, overuje a spája informácie z rôznych domén. |
| **Štruktúrovaný výstup** | Generuje prehľadné správy s nadpismi, zhrnutiami a citáciami. |
| **Export možností** | Výsledky je možné exportovať do PDF alebo ako webovú stránku. |


## Prečo model niekedy vyhľadáva aj pri „jednoduchých" otázkach?

Qwen je trénovaný na **adaptívne a proaktívne správanie**. Aj zdanlivo jednoduchá otázka môže spustiť vyhľadávanie, ak:

1. **Otázka obsahuje špecifické entity** (mená, názvy firiem, lokality), ktoré si model chce overiť v aktuálnom kontexte.
2. **Implicitne vyžaduje aktuálnosť** – napr. „Ako sa darí firme X?" môže znamenať požiadavku na najnovšie finančné výsledky.
3. **Model má nízku mieru istoty** – radšej siahne po externom zdroji, než by riskoval nepresnú odpoveď.

> ✅ **Kľúčový poznatok:** Nie každé vyhľadávanie znamená Deep Research. Väčšina „rýchlych" odpovedí s odkazmi
> využíva štandardný Web Search. Deep Research je náročnejší proces, ktorý sa spúšťa manuálne alebo pri
> explicitne komplexných zadaniach.

## Praktické tipy pre prácu s vyhľadávaním v Qwen Chat

| Cieľ | Odporúčaný postup |
|------|------------------|
| **Rýchla odpoveď bez vyhľadávania** | Pridajte inštrukciu: *„Odpovedz iba na základe svojich vnútorných vedomostí."* |
| **Overenie zdroja** | Sledujte ikonku lupy 🔍 alebo odkazy pod odpoveďou – znak použitia Web Search. |
| **Hĺbková analýza** | Použite tlačidlo **Deep Research** alebo napíšte: *„Sprav hĺbkovú rešerš na tému..."* |
| **Práca so študentmi** | Ukážte rozdiel medzi odpoveďou „z pamäte" a odpoveďou „s vyhľadávaním" – ide o názornú ukážku limitov a možností LLM. |

## Zhrnutie 

🔹 **Web Search** = rýchle doplnenie informácií z webu (ako „inteligentný asistent").  
🔹 **Deep Research** = systematický výskum s plánovaním a analýzou (ako „výskumný tím").  
🔹 Model sa **sám rozhoduje**, kedy vyhľadávanie použiť – na základe kontextu, istoty a typu otázky.  
🔹 Používateľ môže tento proces **ovplyvniť** jasnými inštrukciami v prompte.

> 🎓 **Didaktická výzva:** Požiadajte študentov, aby položili rovnakú otázku dvakrát – raz s príkazom
> *„nevyhľadávaj"* a raz s povolením *„použi web search"*. Porovnajte výsledky a diskutujte o rozdieloch
> v presnosti, aktuálnosti a štruktúre odpovedí.


## 9. Budúcnosť Deep Search technológií

### Trendy vo vývoji:

1.  **Agentic Search**  
    Systémy, ktoré nielen vyhľadávajú, ale aj *konajú* – napr. automaticky vyplnia formulár, porovnajú ceny v reálnom čase,
    alebo naplánujú cestu.

3.  **Multimodálny Deep Search**  
    Vyhľadávanie a syntéza naprieč textom, obrázkami, videom a audio – napr. "Nájdi videá, ktoré vysvetľujú tento matematický
    koncept a zhrň kľúčové body."

5.  **Personalizovaný retrieval**  
    Systémy, ktoré sa učia z preferencií používateľa a prispôsobujú zdroje a štýl odpovedí.

6.  **Collaborative Deep Search**  
    Nástroje pre tímový výskum, kde viacero používateľov spoločne plánuje vyhľadávanie a komentuje výsledky.

7.  **On-device Deep Search**  
    Lokálne modely s obmedzeným, ale súkromným vyhľadávaním – dôležité pre citlivé dáta.

> **Predikcia:** Do 5 rokov sa hranica medzi "vyhľadávačom" a "asistentom" úplne rozostrie. Deep Search sa stane
> štandardnou súčasťou interakcie s AI – nie ako samostatný nástroj, ale ako integrovaná schopnosť inteligentných systémov.

---

## 10. Cvičenie pre študentov: Porovnanie prístupov

### 🧪 Laboratórna úloha: "Hĺbkový výskum na tému obnoviteľných zdrojov"

**Cieľ:** Porovnať kvalitu odpovedí z tradičného vyhľadávania a deep search systému.

**Postup:**

1.  **Definujte komplexnú otázku**, napr.:  
    *"Aké sú hlavné technologické a ekonomické prekážky pre masívne nasadenie vodíkových palivových článkov v doprave do
     roku 2035 v EÚ?"*

3.  **Tradičné vyhľadávanie:**  
    *   Použite bežný vyhľadávač (Google, Bing).  
    *   Zaznamenajte: počet relevantných výsledkov, čas potrebný na nájdenie odpovede, kvalitu zdrojov.

4.  **Deep Search:**  
    *   Použite systém s deep search funkciou (napr. Perplexity, DeepSeek s web access, alebo Google AI Mode).  
    *   Zaznamenajte: štruktúru odpovede, počet citovaných zdrojov, hĺbku analýzy.

5.  **Analýza a porovnanie:**  
    *   Ktorý prístup poskytol komplexnejšiu odpoveď?  
    *   Kde boli rozdiely v aktuálnosti informácií?  
    *   Ktorý výstup bol ľahšie overiteľný?  
    *   Aké boli limity každého prístupu?

6.  **Diskusia v skupine:**  
    *   Kedy by ste zvolili ktorý prístup v reálnej praxi?  
    *   Ako by ste navrhli hybridné riešenie pre konkrétny use case?

**Výstup:** Krátka správa (1-2 strany) s porovnaním a odporúčaniami.


## 10. Záver

Deep Search predstavuje významný posun v tom, ako interagujeme s informáciami. Nie je to len "lepšie vyhľadávanie" – je to  
**nový paradigmatický prístup**, kde AI aktívne pomáha nielen nájsť, ale aj pochopiť, syntetizovať a kriticky hodnotiť informácie. 

Pre študentov AI je dôležité pochopiť, že:
*   Deep Search je postavený na kombinácii retrieval technológií a generatívnych modelov.
*   Kvalita výstupu závisí od celej pipeline – nie len od LLM.
*   Etické aspekty, transparentnosť a kritické myslenie používateľa zostávajú kľúčové.

> **Kľúčová myšlienka:** Deep Search nemení len to, *ako* hľadáme, ale aj to, *čo* od vyhľadávania očakávame.
> Budúcnosť patrí systémom, ktoré sú nielen rýchle, ale aj múdre, transparentné a spolupracujúce.



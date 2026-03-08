# Inteligentní agenti v systémech umelej inteligencie

**Inteligentný agent** (AI Agent) je autonómny softvérový systém, ktorý vníma svoje prostredie,  
spracováva informácie a vykonáva akcie s cieľom dosiahnuť stanovené ciele. Na rozdiel od bežného  
chatbota, ktorý len reaguje na vstupy, agent dokáže *samostatne plánovať, rozhodovať sa a iteratívne pracovať* na riešení úlohy.

> *Ak je LLM (jazykový model) „mozog", potom agent je „mozog + ruky + nástroje + pamäť".*

### Kľúčové charakteristiky agenta
| Vlastnosť | Popis | Príklad |
|-----------|-------|---------|
| **Autonómia** | Funguje bez neustáleho zásahu človeka | Agent sám rozhodne, kedy vyhľadá na webe |
| **Reaktivita** | Vníma prostredie a reaguje na zmeny | Ak sa zmení cena letenky, agent upozorní |
| **Proaktivita** | Koná účelovo, sleduje ciele | Agent sám navrhuje termíny stretnutí |
| **Sociálna schopnosť** | Komunikuje s inými agentmi alebo ľuďmi | Viac agentov spolupracuje na projekte |
| **Pamäť a učenie** | Ukladá kontext a zlepšuje sa so skúsenosťami | Agent si pamätá preferencie používateľa |

---

## Kde sa agenti používajú? (Praktické aplikácie)

### Výskum a vzdelávanie
- **Literárne rešerše**: Agenti prehľadávajú akademické databázy, syntetizujú závery a generujú prehľadové štúdie.
- **Tvorba učebných materiálov**: Automatické generovanie kvízov, zhrnutí kapitol alebo vysvetľujúcich príkladov.
- **Overovanie faktov**: Agenti porovnávajú tvrdenia s viacerými zdrojmi a označujú nekonzistencie.

### Biznis a produktivita
- **Customer support**: Pokročilí agenti riešia komplexné požiadavky zákazníkov (vrátenie tovaru, reklamácie) bez eskalácie na človeka.
- **Analýza dát**: Agenti spracúvajú tabuľky, generujú grafy a formulujú business insights.
- **Projektový manažment**: Automatické rozdeľovanie úloh, sledovanie deadlineov a koordinácia tímov.

### Vývoj a technické úlohy
- **Kódovanie a debugging**: Agenti píšu, testujú a opravujú kód (napr. GitHub Copilot Workspace, Devin).
- **Automatizácia workflow**: Spájanie rôznych API, plánovanie úloh, spracovanie dokumentov.
- **Kyberbezpečnosť**: Detekcia anomálií, simulácia útokov, automatická odpoveď na incidenty.

### Osobné použitie
- **Osobní asistenti**: Plánovanie dní, rezervácie, pripomienky, nákupné zoznamy.
- **Zdravie a wellness**: Sledovanie návykov, personalizované odporúčania, motivácia.
- **Kreatívna tvorba**: Spolupráca pri písaní textov, generovaní nápadov, úprave médií.


##  Druhy agentov a architektúry

### Podľa úrovne autonómie

| Typ | Popis | Príklad |
|-----|-------|---------|
| **Reaktívny agent** | Reaguje na vstupy podľa pevných pravidiel, bez pamäte | Jednoduchý chatbot s rozhodovacím stromom |
| **Agent s pamäťou** | Ukladá históriu interakcií a kontext | Osobný asistent, ktorý si pamätá preferencie |
| **Plánujúci agent** | Rozkladá ciele na podúlohy, vytvára stratégie | Deep Research agent, ktorý plánuje rešerš |
| **Učiaci sa agent** | Zlepšuje sa so skúsenosťami (RL, fine-tuning) | Agent na optimalizáciu reklamných kampaní |

### Podľa špecializácie

| Kategória | Funkcia | Typické nástroje |
|-----------|---------|-----------------|
| **Výskumný agent** | Hĺbkové vyhľadávanie, syntéza zdrojov | Qwen Deep Research, Perplexity Pro |
| **Kódovací agent** | Tvorba, testovanie a debugging kódu | GitHub Copilot, Cursor, Devin |
| **Dátový analytik** | Spracovanie tabuliek, vizualizácie, štatistiky | Julius AI, DataBot, NotebookLM |
| **Kreatívny agent** | Generovanie textu, obrázkov, nápadov | Claude Artifacts, Midjourney Bot |
| **Automatizačný agent** | Spájanie aplikácií, workflow automatizácia | Zapier Interfaces, Make AI, n8n |

### Subagenti a multi-agentné systémy

Komplexné úlohy často riešia **tímy špecializovaných subagentov**, ktorí spolupracujú pod vedením hlavného („manažérskeho") agenta.

```
🎯 Hlavný agent (Planner)
   │
   ├── 🔍 Výskumný subagent → vyhľadáva fakty
   ├── ✍️ Pisateľský subagent → tvorí text
   ├── 🔎 Kontrolný subagent → overuje presnosť
   └── 🎨 Formátovací subagent → upravuje výstup
```

**Výhody multi-agentného prístupu:**

- ✅ **Modularita**: Každý subagent sa špecializuje na jednu úlohu
- ✅ **Škálovateľnosť**: Ľahko pridáte nového subagenta bez prepisu celého systému
- ✅ **Robustnosť**: Chyba jedného subagenta nemusí zlyhať celý proces
- ✅ **Transparentnosť**: Jednoduchšie sledovať, ktorý krok kto vykonal

**Príklady frameworkov pre multi-agentné systémy:**

- **LangGraph** (LangChain) – vizuálne plánovanie workflow
- **AutoGen** (Microsoft) – konverzácia medzi agentmi
- **CrewAI** – jednoduchá definícia rolí a cieľov
- **LlamaIndex Agents** – práca s externými dátami

## Architektúra typického inteligentného agenta

```
┌─────────────────────────────────┐
│  🎯 Cieľ / Prompt od používateľa │
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│  🧠 LLM „mozog" (plánovanie)    │
│  • Rozklad úlohy na kroky        │
│  • Rozhodovanie o nástrojoch     │
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│  🛠️ Nástroje (Tools)            │
│  • Web Search / API volania      │
│  • Kódovanie / Exec sandbox      │
│  • Práca so súbormi (PDF, CSV)   │
│  • Pamäť (vektorová DB, cache)   │
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│  🔁 Iterácia a seba-korekcia    │
│  • Vyhodnotenie výsledku kroku   │
│  • Úprava plánu podľa feedbacku  │
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│  📤 Výstup pre používateľa      │
│  • Text / Správa / Kód / Graf   │
│  • Zdroje a citácie              │
└─────────────────────────────────┘
```

> 💡 **Kľúčový koncept**: Agent nie je len „väčší model". Je to **systém**, kde LLM slúži ako „riadiaca jednotka",
> ktorá koordinuje nástroje, pamäť a iteratívne uvažovanie.


## Tabuľka: Odporúčaní agenti na vyskúšanie (pre študentov a pedagógov)

| Agent / Platforma | Typ | Cena | Dostupnosť | Prečo vyskúšať | Odkaz |
|-------------------|-----|------|------------|----------------|-------|
| **Qwen Chat – Deep Research** | Výskumný agent | 🟢 Zadarmo | ✅ Globálne (web) | Plnohodnotný Deep Research zadarmo, export do PDF, slovenský kontext | [chat.qwen.ai](https://chat.qwen.ai) |
| **Perplexity AI – Pro Search** | Výskumný agent | 🟢 Free / 🟡 $20/mes. | ✅ Globálne | Rýchle, presné odpovede so zdrojmi, Focus Mode pre akademické zdroje | [perplexity.ai](https://perplexity.ai) |
| **Google NotebookLM** | Dátový/výskumný agent | 🟢 Zadarmo | ✅ Globálne | Výborná práca s nahranými PDF, automatické citácie, audio overview | [notebooklm.google.com](https://notebooklm.google.com) |
| **Cursor / GitHub Copilot** | Kódovací agent | 🟢 Free tier / 🟡 $10–20/mes. | ✅ Globálne | Interaktívne písanie a debugging kódu, vysvetľovanie chýb | [cursor.com](https://cursor.com) |
| **CrewAI (open-source)** | Multi-agent framework | 🟢 Zadarmo (self-hosted) | ✅ Globálne | Jednoduchá tvorba vlastných tímov agentov, ideálne na výuku architektúr | [crewai.com](https://crewai.com) |
| **Microsoft Copilot** | Všeobecný agent | 🟢 Free / 🟡 ~22 €/mes. | ✅ Globálne | Integrácia s Office, Bing Search, dobrý pomer cena/výkon | [copilot.microsoft.com](https://copilot.microsoft.com) |
| **Julius AI** | Dátový analytik | 🟢 Free tier / 🟡 Od $10/mes. | ✅ Globálne | Upload Excel/CSV → automatická analýza, grafy, insights | [julius.ai](https://julius.ai) |
| **Elicit** | Akademický výskumný agent | 🟢 Free tier / 🟡 ~10 €/mes. | ✅ Globálne | Špecializácia na peer-reviewed štúdie, extrakcia metód a záverov | [elicit.com](https://elicit.com) |
| **Zapier Interfaces + AI** | Automatizačný agent | 🟢 Free tier / 🟡 Od ~20 €/mes. | ✅ Globálne | Spájanie 5000+ appiek s AI logikou, bez kódovania | [zapier.com](https://zapier.com) |
| **LangGraph Playground** | Vývojársky nástroj | 🟢 Zadarmo (demo) | ✅ Globálne | Vizuálne plánovanie agentných workflow, ideálne na výuku | [langgraph.dev](https://langgraph.dev) |

### 🎨 Legenda cien
| Ikona | Význam |
|-------|--------|
| 🟢 | **Zadarmo** alebo veľkorysý free tier vhodný pre študentov |
| 🟡 | **Platená verzia** pre jednotlivcov (do ~25 €/mes.) |
| 🔵 | **Profesionálna/Enterprise** verzia (nad 25 €/mes.) |


## Didaktické tipy pre výuku o agentoch

### Aktivita 1: „Agent vs. Chatbot"
**Cieľ**: Ukázať rozdiel medzi reaktívnym a plánujúcim agentom.  
**Postup**:
1. Položte študentom rovnakú otázku v bežnom chate („Zhrň tému X") a v režime Deep Research.
2. Porovnajte: hĺbku, štruktúru, zdroje, čas odpovede.
3. Diskusia: Kedy stačí chatbot? Kedy potrebujeme agenta?

### Aktivita 2: „Navrhni svojho subagenta"

**Cieľ**: Pochopiť modularitu multi-agentných systémov.  
**Postup**:
1. Zadajte komplexnú úlohu: *„Vytvorte prehľadovú štúdiu o vplyve sociálnych sietí na duševné zdravie tínedžerov."*
2. Študenti v skupinách navrhnú 3–4 špecializovaných subagentov (výskumný, analytický, pisateľský, kontrolný).
3. Nakreslia diagram spolupráce a popíšu, čo ktorý subagent robí.

### Aktivita 3: „Postav jednoduchého agenta"

**Cieľ**: Praktická skúsenosť s agentnými frameworkmi.  
**Nástroje**: CrewAI alebo LangGraph (bez kódovania / low-code).  
**Úloha**: Vytvoriť agenta, ktorý:
- Vygooglí aktuálne správy na zadanú tému
- Zhrnie ich do 3 bodov
- Vygeneruje kvíz pre spolužiakov

> 🎓 **Reflexia na záver**:  
> *„Agenti nie sú budúcnosť – sú prítomnosťou. Ako budúci používatelia aj tvorcovia AI je kľúčové rozumieť  
> nielen tomu, čo agenti robia, ale aj ako rozhodujú, kde berú informácie a ako overovať ich výstupy."*


*Zdroje a inšpirácia: LangChain docs, CrewAI docs, Microsoft AutoGen, Qwen documentation – informácie aktuálne k marcu 2026.*

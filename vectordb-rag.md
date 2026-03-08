# Vektorové databázy a RAG – Ako AI „pamätá" a pracuje s vlastnými dátami


> Predstavte si jazykový model ako geniálneho študenta, ktorý má v hlave všetko, čo sa naučil z kníh
> do určitého dátumu. Ale čo ak potrebujete, aby vedel aj to, čo nie je v jeho „učebniciach" – napríklad
> vašu školskú učebnicu, firemné dokumenty alebo najnovšie správy? Vektorové databázy a RAG sú ako
> „externý mozog", ktorý modelu umožňuje rýchlo nájsť a použiť informácie, ktoré sám nevie.

###  Problém, ktorý RAG rieši

| Limitácia LLM | Ako RAG pomáha |
|---------------|----------------|
| **Dátový cutoff** – model nevie o udalostiach po tréningu | RAG umožňuje pridať aktuálne dokumenty ako zdroj |
| **Halucinácie** – model môže „vymyslieť" fakty | RAG núti model čerpať z overených, externých zdrojov |
| **Kontextové okno** – limit na dĺžku vstupu | RAG vyberie len relevantné časti dokumentov, šetrí kontext |
| **Súkromné dáta** – model nevidí vaše interné dokumenty | RAG umožňuje pracovať s vlastnými, chránenými zdrojmi |
| **Špecializované vedomosti** – model nemusí poznať vašu doménu | RAG pridá doménové dokumenty ako kontext pre odpoveď |

> RAG nie je náhrada za tréning modelu – je to efektívny spôsob, ako rozšíriť jeho schopnosti bez nákladného doškoľovania.


## Čo sú vektorové embedingy? (Text ako čísla)

### Základný princíp

**Vektorový embeding** je číselná reprezentácia textu (slova, vety, dokumentu) v mnohorozmernom  
priestore, kde *podobný význam = blízke vektory*.

```
Príklad (zjednodušený 2D priestor):

"pes"      → [0.8, 0.2]
"mačka"    → [0.7, 0.3]   ← blízko "pes" (domáce zvieratá)
"automobil"→ [0.1, 0.9]   ← ďaleko od "pes" (iné kategórie)
"vlk"      → [0.9, 0.1]   ← veľmi blízko "pes" (podobný význam)
```

### Ako vzniká embeding?

1. Text sa tokenizuje (rozdelí na tokeny)
2. Model (napr. BERT, Sentence Transformers) spracuje tokeny
3. Výstupom je vektor s desiatkami až tisícami čísel (napr. 384, 768, 1024 dimenzií)
4. Tento vektor zachytáva sémantický význam – nie len slová, ale aj kontext

### Prečo sú embedingy užitočné?

| Vlastnosť | Vysvetlenie | Príklad použitia |
|-----------|-------------|-----------------|
| **Sémantická podobnosť** | Vektory zachytávajú význam, nie len zhodu slov | Vyhľadávanie: „zviera" nájde aj „pes", nie len presné zhody |
| **Jazyková nezávislosť** | Podobné koncepty majú blízke vektory aj v rôznych jazykoch | Cross-linguálne vyhľadávanie: SK „pes" ≈ EN „dog" |
| **Efektívne vyhľadávanie** | Matematické operácie s vektormi sú rýchle | Nearest Neighbor search v miliónoch dokumentov |
| **Flexibilita** | Embedovať možno text, obrázky, audio, video | Multimodálne vyhľadávanie: obrázok → podobné texty |

### 🔹 Vizualizácia: „Mapa významov"

```
Predstavte si, že každý dokument je bod na mape:

          [učebnica biológie]
                    •
                    |
   [článok o zvieratách] •——• [encyklopédia zvierat]
                    |
                    •
          [recept na kuracie prsia]

→ Body blízko seba majú podobný význam
→ Vektorová databáza umožňuje rýchlo nájsť „susedov" daného bodu
```

> **Aktivita pre študentov:**  
> *„Použite [Sentence Transformers Demo](https://huggingface.co/sentence-transformers) na vytvorenie embedingov pre 5 slov.
> Vizualizujte ich v 2D (napr. pomocou PCA) a diskutujte: Ktoré slová sú 'blízko' a prečo?"*

## Podobnostné vyhľadávanie: Ako nájsť „najbližších susedov"

### Cosine Similarity – meranie podobnosti vektorov

Najčastejšia metóda na výpočet podobnosti dvoch vektorov.

```
Cosine Similarity = cos(θ) = (A · B) / (||A|| × ||B||)

Kde:
• A · B = skalárny súčin vektorov
• ||A|| = dĺžka (norma) vektora A
• θ = uhol medzi vektormi

Výsledok:
• 1.0 = úplne rovnaký smer (maximálna podobnosť)
• 0.0 = kolmé vektory (žiadna podobnosť)
• -1.0 = opačný smer (maximálna odlišnosť)
```

### Príklad výpočtu (zjednodušený)

```python
from sklearn.metrics.pairwise import cosine_similarity
import numpy as np

# Dva zjednodušené vektory (v skutočnosti majú stovky dimenzií)
vector_a = np.array([[0.8, 0.2, 0.5]])  # "pes"
vector_b = np.array([[0.9, 0.1, 0.4]])  # "vlk"
vector_c = np.array([[0.1, 0.9, 0.2]])  # "automobil"

# Výpočet podobnosti
sim_ab = cosine_similarity(vector_a, vector_b)[0][0]  # 0.97 → veľmi podobné
sim_ac = cosine_similarity(vector_a, vector_c)[0][0]  # 0.31 → málo podobné

print(f"Podobnosť 'pes' a 'vlk': {sim_ab:.2f}")
print(f"Podobnosť 'pes' a 'automobil': {sim_ac:.2f}")
```

### Nearest Neighbor Search – hľadanie najpodobnejších

Po vypočítaní podobnosti potrebujeme nájsť top-N najpodobnejších dokumentov.

| Metóda | Popis | Vhodné pre |
|--------|-------|------------|
| **Brute-force** | Porovná dotaz so všetkými vektormi | Malé datasety (<10k položiek) |
| **ANN (Approximate NN)** | Hľadá približné, ale rýchle výsledky | Veľké datasety (milióny položiek) |
| **HNSW, IVF, PQ** | Pokročilé indexy pre ANN | Produkčné systémy s nízkou latenciou |

> **Kľúčový poznatok:** Vektorové databázy optimalizujú tento proces – namiesto porovnania so všetkými dokumentmi nájdu relevantné výsledky v milisekundách.

## RAG architektúra: Retrieve → Augment → Generate

###  Čo je RAG?

**Retrieval-Augmented Generation (RAG)** je architektúra, ktorá kombinuje:
1. **Retrieval** – vyhľadanie relevantných informácií z externej databázy
2. **Augmentation** – obohatenie promptu o nájdené informácie
3. **Generation** – generovanie odpovede modelom na základe obohateného kontextu

### 🔹 Schéma RAG workflow

```
┌─────────────────────────────────┐
│ 1. 📥 Používateľ položí otázku  │
│    "Aké sú hlavné príčiny        │
│     klimatických zmien?"        │
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│ 2. 🔍 Retrieve: Vyhľadávanie    │
│    • Otázka sa prevedie na vektor│
│    • Vektorová DB nájde top-K    │
│      najpodobnejších dokumentov │
│    • Príklad nájdených chunkov: │
│      - "Skleníkové plyny..."    │
│      - "Odlesňovanie prispieva..."│
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│ 3. 🧩 Augment: Tvorba promptu   │
│    System: "Odpovedaj na základe│
│    poskytnutého kontextu."      │
│    Context: [nájdené chunky]    │
│    Question: [pôvodná otázka]   │
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│ 4. 🤖 Generate: LLM odpovedá    │
│    Model vygeneruje odpoveď     │
│    s citáciami na zdroje:       │
│    "Hlavné príčiny sú: 1) ...   │
│     [Zdroj: dokument A]         │
│     2) ... [Zdroj: dokument B]" │
└─────────┬───────────────────────┘
          ▼
┌─────────────────────────────────┐
│ 5. 📤 Výstup pre používateľa   │
│    • Odpoveď s citáciami        │
│    • Možnosť kliknúť na zdroj   │
│    • Transparentnosť pôvodu    │
└─────────────────────────────────┘
```

### Výhody RAG oproti „čistému" LLM

| Kritérium | LLM bez RAG | LLM s RAG |
|-----------|-------------|-----------|
| **Aktuálnosť** | Obmedzená dátovým cutoff | Môže pracovať s najnovšími dokumentmi |
| **Presnosť** | Riziko halucinácií | Odpovede sú podložené externými zdrojmi |
| **Transparentnosť** | Často bez citácií | Výstup obsahuje odkazy na zdroje |
| **Súkromie** | Dáta musia ísť do modelu | Citlivé dáta môžu zostať lokálne |
| **Náklady** | Drahé fine-tuningy | Lacnejšie: stačí aktualizovať databázu |
| **Údržba** | Tréning modelu je náročný | Pridanie nového dokumentu = minúty |

### Typy RAG architektúr

| Typ | Popis | Vhodné pre |
|-----|-------|------------|
| **Naive RAG** | Jednoduché vyhľadanie + prompt | Rýchle prototypy, malé projekty |
| **Advanced RAG** | Query rewriting, re-ranking, hybrid search | Produkčné systémy, vyššia presnosť |
| **Modular RAG** | Viacero retrieverov, iteratívne vyhľadávanie | Komplexné úlohy, multi-dokumentová syntéza |
| **Agentic RAG** | Agent rozhoduje, kedy a čo vyhľadať | Dynamické, viac-krokové úlohy |

## Praktická implementácia: Krok za krokom

### Krok 1: Príprava dokumentov (Chunking)
Veľké dokumenty treba rozdeliť na menšie časti („chunky"), aby sa dali efektívne indexovať.

```python
from langchain.text_splitter import RecursiveCharacterTextSplitter

# Rozdelenie textu na chunky
text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=500,      # max. 500 znakov na chunk
    chunk_overlap=50,    # 50 znakov prekrytie pre kontext
    separators=["\n\n", "\n", " ", ""]
)

chunks = text_splitter.split_text(dlhy_text_z_pdf)
print(f"Vytvorených {len(chunks)} chunkov")
```

**Tipy pre chunking:**

- Zachovajte celé vety/odseky (nepretrhnite uprostred myšlienky)
- Pridajte metadáta: názov dokumentu, stránka, sekcia
- Pre slovenčinu: dbajte na hranice slov (tokenizácia môže líšiť)

### Krok 2: Vytvorenie embedingov a indexovanie

```python
from sentence_transformers import SentenceTransformer
import chromadb

# Načítanie modelu pre slovenské embedingy
# (použitie multilingválneho modelu pre lepšiu SK podporu)
embed_model = SentenceTransformer('paraphrase-multilingual-MiniLM-L12-v2')

# Vytvorenie chroma DB a pridanie dokumentov
client = chromadb.Client()
collection = client.create_collection("slovenske_dokumenty")

for i, chunk in enumerate(chunks):
    embedding = embed_model.encode(chunk).tolist()
    collection.add(
        embeddings=[embedding],
        documents=[chunk],
        ids=[f"chunk_{i}"],
        metadatas=[{"source": "ucebnica_biol.pdf", "page": 12}]
    )
```

### Krok 3: Vyhľadávanie a generovanie odpovede

```python
from transformers import pipeline

# Vytvorenie embedingu pre otázku
question = "Čo je fotosyntéza?"
question_embedding = embed_model.encode(question).tolist()

# Vyhľadanie top-3 najpodobnejších chunkov
results = collection.query(
    query_embeddings=[question_embedding],
    n_results=3
)

# Príprava kontextu pre LLM
context = "\n\n".join(results['documents'][0])
prompt = f"""Na základe nasledujúceho kontextu odpovedz na otázku.
Ak kontext neobsahuje odpoveď, povedz to.

KONTEXT:
{context}

OTÁZKA: {question}

ODPOVEĎ:"""

# Generovanie odpovede (pomocou lokálneho alebo API modelu)
generator = pipeline("text-generation", model="slovak-nlp/mistral-sk-7b")
answer = generator(prompt, max_new_tokens=200)[0]['generated_text']
print(answer)
```

### Krok 4: Zobrazenie s citáciami

```python
# Pridanie zdrojov k odpovedi
sources = [
    f"{meta['source']}, str. {meta['page']}" 
    for meta in results['metadatas'][0]
]

final_output = f"{answer}\n\n📚 Zdroje: {', '.join(sources)}"
print(final_output)
```

> **Tip pre pedagógov:** Tento kód je možné spustiť v Google Colab bez inštalácie – ideálne pre študentské demo.

## Nástroje a platformy pre vektorové databázy

### Porovnanie populárnych riešení

| Nástroj | Typ | Cena | Slovenská podpora | Vhodné pre | Odkaz |
|---------|-----|------|-------------------|------------|-------|
| **Chroma** | Open-source, lokálny | 🟢 Zadarmo | ✅ Áno (cez multilingválne modely) | Študentské projekty, prototypy | [chromadb.ai](https://chromadb.ai) |
| **FAISS** (Facebook) | Open-source knižnica | 🟢 Zadarmo | ✅ Áno | Výskum, veľké datasety | [github.com/facebookresearch/faiss](https://github.com/facebookresearch/faiss) |
| **Pinecone** | Managed cloud služba | 🟢 Free tier / 🟡 Od $25/mes. | ✅ Áno | Produkčné aplikácie, škálovateľnosť | [pinecone.io](https://pinecone.io) |
| **Weaviate** | Open-source + cloud | 🟢 Self-hosted / 🟡 Cloud od $25/mes. | ✅ Áno | Hybridné vyhľadávanie, GraphQL API | [weaviate.io](https://weaviate.io) |
| **Qdrant** | Open-source, Rust-based | 🟢 Self-hosted / 🟡 Cloud od $15/mes. | ✅ Áno | Vysoký výkon, filtrácia metadát | [qdrant.tech](https://qdrant.tech) |
| **Hugging Face + Spaces** | Platforma s embeding modelmi | 🟢 Zadarmo (s limitmi) | ✅ Áno (multilingválne modely) | Rýchle demo, zdieľanie projektov | [huggingface.co](https://huggingface.co) |

### 🔹 Odporúčané embeding modely pre slovenčinu

| Model | Jazyky | Dimenzie | Licencia | Odkaz |
|-------|--------|----------|----------|-------|
| **paraphrase-multilingual-MiniLM-L12-v2** | 50+ jazykov (vrátane SK) | 384 | Apache 2.0 | [HF link](https://huggingface.co/sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2) |
| **LaBSE** (Google) | 109 jazykov | 768 | Apache 2.0 | [HF link](https://huggingface.co/sentence-transformers/LaBSE) |
| **XLM-RoBERTa** | 100+ jazykov | 768 | MIT | [HF link](https://huggingface.co/FacebookAI/xlm-roberta-base) |
| **slovakbert** (gerulata) | Slovenský | 768 | MIT | [HF link](https://huggingface.co/gerulata/slovakbert) |

> **Poznámka:** Pre najlepšie výsledky v slovenčine odporúčame testovať viacero modelov – niektoré môžu lepšie zachytávať lokálne špecifiká.


## RAG v slovenskom kontexte: Špecifiká a riešenia

### Výzvy pri práci so slovenskými dokumentmi

| Výzva | Vysvetlenie | Odporúčané riešenie |
|-------|-------------|---------------------|
| **Tokenizácia a chunking** | Slovenské slová sa môžu rozdeliť inak ako anglické | Použiť jazykovo-aware tokenizery, testovať hranice chunkov |
| **Menej trénovacích dát pre embedingy** | Multilingválne modely môžu mať horšiu SK presnosť | Fine-tunovať embeding model na slovenských dátach, alebo použiť SlovakBERT |
| **Miešanie s češtinou** | Dokumenty môžu obsahovať CZ/SK mix | Explicitne špecifikovať jazyk v prompte, použiť jazykovú detekciu |
| **Špecializovaná terminológia** | Odborné pojmy môžu byť zle zachytené | Pridať glosár ako metadáta, použiť domain-specific fine-tuning |
| **Formátovanie dokumentov** | PDF so slovenskými znakmi môže mať problémy s OCR | Použiť kvalitné OCR nástroje s UTF-8 podporou, manuálna kontrola |

### Best practices pre slovenské RAG projekty

```
✅ Pred spracovaním:
   • Normalizujte text: odstráňte nepotrebné znaky, zachovajte slovenské diakritiky
   • Detegujte jazyk: ak je dokument zmiešaný SK/CZ, označte to v metadátach
   • Pridajte štruktúru: nadpisy, čísla strán, sekcie ako metadáta pre lepšie filtrovanie

✅ Pri výbere modelu:
   • Testujte multilingválne modely (paraphrase-multilingual) aj slovenské (SlovakBERT)
   • Porovnajte kvalitu vyhľadávania na vzorových otázkach
   • Zvážte fine-tuning embeding modelu na vašich dátach

✅ Pri tvorbe promptu:
   • Explicitne špecifikujte: "Odpovedz po slovensky, spisovným jazykom"
   • Pridajte inštrukciu: "Ak kontext neobsahuje odpoveď, povedz, že nevieš"
   • Požiadajte o citácie: "Uveď zdroj informácie (názov dokumentu, strana)"

✅ Pri evaluácii:
   • Vytvorte testovú množinu slovenských otázok s očakávanými odpoveďami
   • Merajte: presnosť, relevancia, úplnosť, jazyková kvalita
   • Zapojte študentov do hodnotenia výstupov (crowdsourced evaluácia)
```


## Praktické cvičenia pre študentov

### Cvičenie 1: „Embeding Explorer" – Vizuálna analýza podobnosti

**Cieľ**: Pochopiť, ako vektory reprezentujú význam textu.

**Postup**:
1. Študenti vyberú 10 slov z rôznych kategórií (zvieratá, doprava, emócie...)
2. Pomocou [Sentence Transformers Demo](https://huggingface.co/sentence-transformers) získajú embedingy
3. V Google Colab vizualizujú vektory v 2D pomocou PCA/t-SNE
4. Diskutujú: Ktoré slová sú „blízko"? Prečo? Sú výsledky intuitívne?

**Šablóna pre záznam**:
```
Slovo | Kategória | Pozícia v 2D (x, y) | Najbližší sused | Prečo to dáva zmysel?
------|-----------|---------------------|-----------------|------------------------
pes   | zvieratá  | (0.82, 0.15)        | vlk             | Obe sú šelmy, podobný kontext
...
```

### Cvičenie 2: „Build Your First RAG" – Chat s dokumentom

**Cieľ**: Vytvoriť funkčný demo RAG systému.

**Materiál**: 
- Jednoduchý slovenský text (napr. kapitola z Wikipédie)
- Google Colab notebook s pripraveným kódom (učiteľom)

**Postup**:
1. Študenti nahrajú text a rozdelia ho na chunky
2. Vytvoria embedingy pomocou multilingválneho modelu
3. Indexujú chunky v Chroma DB (lokálne)
4. Položia 3 testovacie otázky a porovnajú odpovede s/bez RAG
5. Pridajú citácie a vyhodnotia kvalitu

**Bonus**: Nasadiť ako Gradio appku na Hugging Face Spaces.

### Cvičenie 3: „RAG vs. Pure LLM" – Porovnávacia štúdia

**Cieľ**: Kriticky hodnotiť výhody a limitácie RAG.

**Postup**:
1. Študenti pripravia 5 faktografických otázok na základe dokumentu
2. Položia otázky:
   - a) LLM bez prístupu k dokumentu
   - b) LLM s RAG (s prístupom k dokumentu)
3. Vyhodnotia:
   - Presnosť odpovedí (fact-checking)
   - Prítomnosť citácií
   - Jazykovú kvalitu
4. Diskusia: Kedy použiť RAG? Kedy stačí „čistý" LLM?

**Hodnotiaca rubrika**:

```
Kritérium | LLM bez RAG | LLM s RAG | Komentár
----------|-------------|-----------|----------
Presnosť  | ___/5       | ___/5     | 
Citácie   | ___/5       | ___/5     | 
Jazyk SK  | ___/5       | ___/5     | 
Celkovo   | ___/15      | ___/15    | 
```

### Cvičenie 4: „Ethical RAG" – Bias a transparentnosť

**Cieľ**: Rozvíjať kritické myslenie o etických aspektoch RAG.

**Postup**:
1. Študenti vytvoria RAG systém s dokumentmi obsahujúcimi potenciálny bias (napr. historické texty so stereotypmi)
2. Položia otázky, ktoré môžu aktivovať bias v odpovedi
3. Analyzujú: 
   - Obsahuje odpoveď problematické tvrdenia?
   - Sú zdroje transparentne uvedené?
   - Ako by sa dalo bias mitigovať?
4. Navrhnú úpravy: filtrácia zdrojov, prompt inžinierstvo, ľudský dohľad

> *„RAG nezaručuje 'objektívnu' odpoveď – závisí od kvality a vyváženosti zdrojov. Ako budúci tvorcovia AI
> systémov musíme byť zodpovední za výber a prezentáciu informácií."*

## Časté problémy a riešenia v RAG projektoch

| Problém | Príznak | Možné riešenie |
|---------|---------|----------------|
| **Nízka relevancia výsledkov** | Vyhľadávané chunky nesúvisia s otázkou | • Použiť lepší embeding model<br>• Pridať query rewriting<br>• Implementovať re-ranking |
| **Strata kontextu pri chunkingu** | Odpoveď je neúplná, pretože informácia bola rozdelená | • Zvýšiť chunk_overlap<br>• Použiť hierarchický chunking<br>• Pridať metadáta o susedných chunkoch |
| **Halucinácie napriek RAG** | Model ignoruje kontext a „vymýšľa" | • Posilniť inštrukciu: „Odpovedaj iba na základe kontextu"<br>• Pridať self-check krok<br>• Použiť model s lepším nasledovaním inštrukcií |
| **Pomalé vyhľadávanie** | Odpoveď trvá príliš dlho | • Použiť ANN index namiesto brute-force<br>• Zmenšiť počet dimenzií embedingu<br>• Cache-ovať časté dotazy |
| **Jazyková nekonzistencia** | Odpoveď je v inom jazyku ako otázka | • Explicitne špecifikovať jazyk v prompte<br>• Použiť jazykovo-špecifický embeding model<br>• Post-process: detekcia a preklad |
| **Citácie chýbajú alebo sú nepresné** | Používateľ nevie overiť zdroj | • Povinné pridávať metadáta ku každému chunku<br>• Štruktúrovať output: „Odpoveď + Zdroje"<br>• Implementovať validáciu citácií |


## Zhrnutie a kľúčové poznatky

1. *Vektorové embedingy* = číselná reprezentácia významu; podobný význam = blízke vektory.
2. *Cosine similarity* je štandardná metóda na meranie podobnosti vektorov v RAG systémoch.
3. *RAG architektúra* (Retrieve → Augment → Generate) rieši limitácie LLM: aktuálnosť, halucinácie, súkromie.
4. *Chunking a metadáta* sú kritické pre kvalitu vyhľadávania – nezabúdajte na štruktúru dokumentov.
5. *Výber nástrojov* závisí od projektu: Chroma/FAISS pre študentské demo, Pinecone/Qdrant pre produkciu.
6. *Slovenský kontext vyžaduje špeciálny prístup*: testovať multilingválne aj lokálne modely, explicitne špecifikovať jazyk.
7. *Evaluácia je nevyhnutná*: RAG nie je „zapni a funguje" – potrebuje testovanie, ladenie a ľudský dohľad.

## Ďalšie zdroje a materiály

| Typ zdroja | Názov / Odkaz | Popis |
|------------|---------------|-------|
| 📚 Tutoriál | [LangChain RAG Tutorial](https://python.langchain.com/docs/use_cases/question_answering/) | Komplexný návod na RAG v Pythone (anglicky) |
| 🧪 Demo | [Hugging Face RAG Spaces](https://huggingface.co/spaces?search=rag) | Hotové demo aplikácie na vyskúšanie |
| 📄 Dokumentácia | [Chroma DB Docs](https://docs.trychroma.com) | Praktický sprievodca pre začiatočníkov |
| 🎥 Video | [RAG Explained – YouTube](https://www.youtube.com/results?search_query=rag+retrieval+augmented+generation) | Vizuálne vysvetlenie architektúry |
| 🇸🇰 Lokálny zdroj | [slovak-nlp/resources](https://github.com/slovak-nlp/resources) | Príklady a modely pre slovenské NLP projekty |
| 📋 Pracovný list | [RAG Checklist – printable](https://example.com) *(príprava učiteľa)* | Tlačiteľný checklist pre študentské projekty |
| 🔬 Výskum | [RAG Survey Paper (2024)](https://arxiv.org/abs/2312.10997) | Prehľad stavu RAG výskumu (pre pokročilých) |


## Príloha: RAG Cheat Sheet 

```
🚀 RÝCHLY SPRIEVODCA RAG PROJEKTOM

✅ Základný workflow:
1. 📄 Priprav dokumenty → chunking + metadáta
2. 🔢 Vytvor embedingy → multilingválny model pre SK
3. 🔍 Indexuj vo vektorovej DB → Chroma / FAISS / Pinecone
4. ❓ Prijmi otázku → vytvor jej embeding
5. 🔎 Vyhľadaj top-K chunkov → cosine similarity
6. 🧩 Zostav prompt → kontext + otázka + inštrukcie
7. 🤖 Generuj odpoveď → LLM s citáciami
8. ✅ Vyhodnoť → presnosť, jazyk, zdroje

✅ Prompt šablóna pre RAG:
"""
Na základe nasledujúceho kontextu odpovedz na otázku.
Ak kontext neobsahuje odpoveď, povedz: "Na základe poskytnutých zdrojov neviem odpovedať."

KONTEXT:
{retrieved_chunks}

OTÁZKA: {question}

ODPOVEĎ (po slovensky, s citáciami):
"""

✅ Kontrola pred nasadením:
□ Sú chunky primerane veľké a zachovávajú kontext?
□ Má každý chunk metadáta (zdroj, strana, sekcia)?
□ Bol embeding model testovaný na slovenských otázkach?
□ Obsahuje prompt jasné inštrukcie o jazyku a citáciách?
□ Je výstup overiteľný (fact-checking na vzorke otázok)?

🔁 Pamätaj: RAG je iteratívny proces. Začni jednoducho, testuj, zbieraj feedback a vylepšuj!
```

*Zdroje a inšpirácia: LangChain documentation, Chroma DB docs, Hugging Face Sentence Transformers,  
„Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks" (Lewis et al., 2020) – informácie aktuálne k marcu 2026.*

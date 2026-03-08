# Hugging Face – Open-Source platforma pre umelú inteligenciu

**Hugging Face** je globálna open-source platforma a komunita pre vývoj umelnej inteligencie, ktorú často  
označujú ako **„GitHub pre machine learning"** [[3]]. Vznikla v roku 2016 s cieľom demokratizovať prístup  
k moderným technológiám umelej inteligencie a dnes slúži ako centrálny hub pre výskumníkov, vývojárov aj študentov.


> *Predstavte si Hugging Face ako obrovskú knižnicu, kde namiesto kníh nájdete hotové AI modely,
> datasety a interaktívne aplikácie. Namiesto toho, aby ste písali každý model od nuly, môžete si „požičať" ten,
> ktorý už niekto vytvoril, a prispôsobiť ho svojim potrebám.*

### Základné fakty (2026)

| Ukazovateľ | Hodnota |
|------------|---------|
| **Počet modelov** | Viac ako 2 milióny [[38]] |
| **Počet datasetov** | Viac ako 500 000 [[38]] |
| **Počet Spaces (demo aplikácií)** | Viac ako 1 milión [[1]] |
| **Podporované modalit** | Text, obrázky, audio, video, multimodálne |
| **Licencia** | Prevažne open-source (Apache 2.0, MIT, CC) |


## 2. Kľúčové komponenty ekosystému Hugging Face

### Hugging Face Hub

Centrálny portál ([huggingface.co](https://huggingface.co)), kde komunita zdieľa a objavuje AI zdroje.  
Funguje na báze Git verzií, čo umožňuje sledovať históriu zmien, spolupracovať a jednoducho sťahovať modely [[38]].

### Transformers Library

Flagship open-source knižnica, ktorá štandardizuje prácu s transformerovými modelmi 

```python
# Príklad: Sentiment analýza na 3 riadky kódu
from transformers import pipeline

classifier = pipeline("sentiment-analysis")
result = classifier("Hugging Face je úžasná platforma!")
print(result)  # [{'label': 'POSITIVE', 'score': 0.999}]
```

**Podporované úlohy:**
- 📝 Text: klasifikácia, generovanie, preklad, sumarizácia, QA
- 🖼️ Vízia: detekcia objektov, segmentácia, generovanie obrázkov
- 🔊 Audio: rozpoznávanie reči, text-to-speech, klasifikácia zvuku
- 🔄 Multimodálne: modely spájajúce text + obrázok + audio

### 🔹 Datasets Library
Nástroj na jednoduchý prístup k tisícom verejných datasetov [[13]].

```python
from datasets import load_dataset

# Načítanie datasetu na jednu líniu
dataset = load_dataset("imdb")  # Recenzie filmov
print(dataset["train"][0])  # Prvá ukážka
```

**Výhody:**
- ✅ Streaming veľkých datasetov (nemusia sa zmestiť do RAM)
- ✅ Automatické predspracovanie a tokenizácia
- ✅ Podpora pre viac ako 8 000 jazykov

### 🔹 Spaces – Interaktívne demo aplikácie
Spaces umožňujú hostovať ML demo priamo v prehliadači pomocou **Gradio** alebo **Streamlit** [[33]][[37]].

```python
# Príklad Gradio appky pre sentiment analýzu
import gradio as gr
from transformers import pipeline

classifier = pipeline("sentiment-analysis")

def analyze(text):
    return classifier(text)[0]

demo = gr.Interface(
    fn=analyze,
    inputs=gr.Textbox(label="Váš text"),
    outputs=gr.JSON(label="Výsledok"),
    title="Sentiment Analyzer"
)
demo.launch()
```

> 💡 **Tip:** Každý Space je Git repozitár – môžete ho forkovať, upravovať a zdieľať ako open-source projekt.

### 🔹 Ďalšie užitočné knižnice
| Kniznica | Účel |
|----------|------|
| **Diffusers** | Generovanie obrázkov/videa difúznymi modelmi |
| **PEFT** | Parameter-Efficient Fine-Tuning (LoRA, QLoRA) |
| **Accelerate** | Zjednodušenie distribuovaného tréningu |
| **Tokenizers** | Rýchla tokenizácia v Rust-e |
| **TRL** | Reinforcement Learning pre jazykové modely |
| **Transformers.js** | Spúšťanie modelov priamo v prehliadači |

---

## 3. Kde sa Hugging Face používa? (Praktické aplikácie)

### 🔬 Výskum a vzdelávanie
- **Experimentovanie s modelmi**: Študenti môžu testovať rôzne architektúry bez potreby tréningu od nuly.
- **Reprodukovateľnosť výskumu**: Modely s presnou verziou a metadátami umožňujú overiť výsledky štúdií.
- **Tvorba učebných materiálov**: Generovanie kvízov, príkladov, vysvetlení pomocou LLM.

### 💼 Biznis a produkcia
- **Rýchly prototyping**: Firmy testujú nové AI nápady v priebehu hodín, nie týždňov.
- **Inference API**: Hostované API pre nasadenie modelov bez správy serverov [[4]].
- **Enterprise Hub**: Súkromné repozitáre s RBAC pre regulované odvetvia.

### 🛠️ Vývojárske workflow
```
1. 🔍 Nájdi model na Hube (napr. "bert-base-slovak")
2. 📥 Stiahni a otestuj lokálne pomocou Transformers
3. 🎯 Fine-tune na vlastných dátach (voliteľné)
4. 🚀 Nasad cez Inference API alebo Spaces
5. 🔄 Zdieľaj vylepšený model späť na Hub
```

### 🌍 Komunitné projekty
- **Lokalizácia modelov**: Komunity prekladajú a fine-tunujú modely pre menej zastúpené jazyky.
- **Ethical AI**: Model Cards a Dataset Cards dokumentujú obmedzenia, bias a licenčné podmienky.


## 4. Hugging Face vo vzdelávaní: Classrooms Program

Hugging Face ponúka špeciálny program **[Hugging Face for Classrooms](https://huggingface.co/classrooms)**, 
ktorý poskytuje pedagógom bezplatné nástroje na výučbu ML [[23]][[25]].

### Čo ponúka Classrooms?
| Funkcia | Popis |
|---------|-------|
| **Organizačný priestor** | Centrálne miesto pre všetky študentské projekty, modely a datasety |
| **Verzovanie a spolupráca** | Git-based workflow – študenti sa učia profesionálne praktiky |
| **Prístupové práva** | Admin/Read/Write role pre učiteľa a študentov |
| **Bezplatné zdroje** | Upload modelov, datasetov a Spaces bez obmedzenia |
| **Výukové materiály** | Hotové tutoriály, kurzy a príklady pre rôzne úrovne |

### Ako začať s Classrooms?
1. Vytvorte si účet na [huggingface.co](https://huggingface.co)
2. Prejdite na [Classrooms](https://huggingface.co/classrooms) a založte triedu
3. Pozvite študentov cez e-mail alebo odkaz
4. Vyberte si tutoriál z [Education Toolkit](https://github.com/huggingface/education-toolkit) [[21]]
5. Začnite tvoriť!

> 🎓 **Tip pre pedagógov:** Začnite s jednoduchou úlohou – napr. „Vytvorte sentiment analyzátor pre slovenské recenzie".
> Študenti sa naučia pracovať s modelmi, datasetmi aj Spaces v jednom projekte.


## 5. Typy modelov na Hugging Face Hub

### 🔹 Podľa modality
| Modalita | Príklad úlohy | Príklad modelu |
|----------|--------------|----------------|
| **Text** | Klasifikácia, generovanie, preklad | `bert-base-uncased`, `gpt2`, `t5-base` |
| **Obrázky** | Klasifikácia, detekcia, generovanie | `vit-base-patch16-224`, `stable-diffusion-2` |
| **Audio** | Rozpoznávanie reči, TTS | `wav2vec2-base`, `speecht5_tts` |
| **Multimodálne** | Text + obrázok, video + audio | `clip-vit-base`, `llava-hf` |

### 🔹 Podľa licencie
| Typ licencie | Popis | Vhodné pre |
|--------------|-------|------------|
| **Apache 2.0 / MIT** | Veľmi permissívne, komerčné použitie OK | Študentské projekty, startupy |
| **CC-BY / CC-BY-SA** | Vyžaduje atribúciu, niekedy share-alike | Akademické práce, open-source |
| **Non-commercial** | Iba výskum/vzdelávanie, nie komerčné | Školské projekty, osobné použitie |
| **Gated / Request access** | Vyžaduje schválenie autora | Citlivé modely, regulované dáta |

> ⚠️ **Dôležité:** Vždy skontrolujte licenciu a Model Card pred použitím modelu v projekte!

---

## 6. Tabuľka: Odporúčané modely a zdroje na vyskúšanie

| Názov / Odkaz | Typ | Jazyk / Modalita | Cena | Prečo vyskúšať | Didaktický cieľ |
|---------------|-----|-----------------|------|----------------|-----------------|
| **[bert-base-slovak](https://huggingface.co/deepset/bert-base-cased-squad2)** | Text encoder | Slovenský text | 🟢 Zadarmo | Špecializovaný pre slovenčinu, vhodný na klasifikáciu | Ukázať fine-tuning pre lokálny jazyk |
| **[gpt2](https://huggingface.co/gpt2)** | Text generátor | Angličtina | 🟢 Zadarmo | Jednoduchý, rýchly, dobrý na úvod do generovania | Porovnať output s väčšími LLM |
| **[distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased)** | Ľahký text model | Angličtina | 🟢 Zadarmo | 40% menší ako BERT, podobná presnosť | Ukázať trade-off medzi veľkosťou a výkonom |
| **[stable-diffusion-2](https://huggingface.co/stabilityai/stable-diffusion-2)** | Generovanie obrázkov | Text→Obrázok | 🟢 Zadarmo | Štandard pre open-source image generation | Kreatívne úlohy, etika generovaného obsahu |
| **[wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base)** | Rozpoznávanie reči | Audio→Text | 🟢 Zadarmo | State-of-the-art pre ASR, podpora viacerých jazykov | Práca s multimodálnymi dátami |
| **[clip-vit-base-patch32](https://huggingface.co/openai/clip-vit-base-patch32)** | Multimodálny | Text+Obrázok | 🟢 Zadarmo | Spája vizuálne a textové embedingy | Vyhľadávanie obrázkov podľa popisu |
| **[t5-base](https://huggingface.co/t5-base)** | Seq2seq model | Viacjazyčný | 🟢 Zadarmo | Univerzálny: preklad, sumarizácia, QA | Ukázať flexibilitu jedného modelu |
| **[llava-hf](https://huggingface.co/llava-hf/llava-v1.6-mistral-7b-hf)** | Multimodálny LLM | Text+Obrázok | 🟢 Zadarmo | Odpovedá na otázky o obrázkoch | Moderné multimodálne aplikácie |
| **[Education Toolkit](https://github.com/huggingface/education-toolkit)** | Výukové materiály | Rôzne | 🟢 Zadarmo | Hotové lekcie, príklady, projekty pre školy [[21]] | Štruktúrovaná výuka ML pre začiatočníkov |
| **[Classrooms Demo](https://huggingface.co/classrooms)** | Pedagogická platforma | Všetko | 🟢 Zadarmo | Bezplatný manažment študentských projektov [[23]] | Organizácia skupinovej práce s verzovaním |

### 🎨 Legenda cien
| Ikona | Význam |
|-------|--------|
| 🟢 | **Zadarmo** (open-source, verejný prístup) |
| 🟡 | **Freemium** (základ zadarmo, pokročilé funkcie platené) |
| 🔵 | **Enterprise** (súkromné nasadenie, SLA, podpora) |

---

## 7. Praktický návod: Váš prvý projekt na Hugging Face

### 🎯 Cieľ: Vytvoriť sentiment analyzátor pre slovenské texty

**Krok 1: Príprita prostredia**
```bash
pip install transformers datasets gradio
```

**Krok 2: Načítanie modelu a testovanie**
```python
from transformers import pipeline

# Použijeme multilingválny model
classifier = pipeline("sentiment-analysis", 
                     model="nlptown/bert-base-multilingual-uncased-sentiment")

# Test
print(classifier("Tento produkt je skvelý!"))  
# Output: [{'label': '5 stars', 'score': 0.98}]
```

**Krok 3: Vytvorenie interaktívnej appky (Gradio)**
```python
import gradio as gr

def analyze_sentiment(text):
    result = classifier(text)[0]
    return {result["label"]: result["score"]}

demo = gr.Interface(
    fn=analyze_sentiment,
    inputs=gr.Textbox(label="Napíšte recenziu po slovensky"),
    outputs=gr.Label(label="Sentiment"),
    title="Slovenský Sentiment Analyzátor",
    description="Vyskúšajte, ako AI hodnotí váš text!"
)
demo.launch()
```

**Krok 4: Nasadenie na Hugging Face Spaces**
1. Vytvorte nový Space na [huggingface.co/spaces](https://huggingface.co/spaces)
2. Zvoľte **Gradio** ako SDK
3. Nahrajte `app.py` a `requirements.txt`
4. Kliknite **Deploy** – vaša appka je online! 🎉

> 💡 **Bonus:** Pridajte `README.md` s popisom projektu a `LICENSE` – učíte študentov open-source praktiky!

---

## 8. Didaktické tipy pre výučbu s Hugging Face

### 🧪 Aktivita 1: „Model Scavenger Hunt"

**Cieľ**: Naučiť študentov orientovať sa na Hugging Face Hub.  
**Postup**:
1. Zadajte zoznam úloh: *„Nájdi model pre slovenský text", „Nájdi dataset s obrázkami zvierat", „Nájdi Space, ktorý generuje poéziu"*
2. Študenti hľadajú, screenshotujú a zdôvodnia výber
3. Diskusia: Ako rozlíšiť kvalitný model? (počet downloadov, Model Card, licencia)

### 🧩 Aktivita 2: „Fine-Tuning v praxi"

**Cieľ**: Ukázať, ako sa model prispôsobuje novým dátam.  
**Nástroje**: Google Colab + `transformers` + malý slovenský dataset  
**Úloha**: Fine-tune `bert-base-slovak` na klasifikáciu správ (šport/politika/kultúra)  
**Výstup**: Porovnanie presnosti pred a po fine-tuningu

### 🌐 Aktivita 3: „Ethics & Model Cards"

**Cieľ**: Kritické myslenie o obmedzeniach AI.  
**Postup**:
1. Vyberte model s kontroverznou Model Card (napr. bias v dátach)
2. Študenti analyzujú: *Pre koho môže byť model problematický? Ako by ste to zlepšili?*
3. Napíšte vlastnú „Ethical Use" sekciu pre Model Card

### 💻 Aktivita 4: „Build Your First Space"

**Cieľ**: Praktická skúsenosť s nasadením.  
**Postup**:
1. Študenti vytvoria jednoduchú Gradio appku (napr. prekladateľ, generátor mien)
2. Nasadia ju na Spaces
3. Zdieľajú odkaz v triede a vzájomne testujú


> *„Hugging Face nie je len nástroj – je to filozofia otvorenosti a spolupráce. Učiť sa s ním
> znamená nielen technické zručnosti, ale aj pochopenie zodpovednosti, komunity a zdieľania vedomostí."*


## 9. Časté otázky (FAQ)

**Q: Je Hugging Face naozaj zadarmo?**  
A: Áno, väčšina modelov, datasetov a Spaces je open-source a zadarmo. Platené sú len enterprise funkcie (súkromné Hub, vyššie limity API) [[4]].

**Q: Potrebujem silný počítač?**  
A: Na testovanie malých modelov stačí bežný notebook. Pre veľké modely využite Google Colab (zdarma GPU) alebo Hugging Face Inference API.

**Q: Ako vybrať správny model?**  
A: Použite filtre na Hube (task, jazyk, licencia), skontrolujte Model Card, počet downloadov a recenzie. Začnite s menšími modelmi (DistilBERT) pre rýchle iterácie.

**Q: Môžem použiť model komerčne?**  
A: Závisí od licencie. Apache 2.0 a MIT umožňujú komerčné použitie. Vždy si prečítajte Model Card a LICENSE súbor.

**Q: Ako zapojiť študentov bez programátorských skúseností?**  
A: Začnite s Spaces – študenti môžu upravovať existujúce Gradio appky bez písania kódu, alebo použiť no-code nástroje ako AutoTrain.

---

*Poznámka pre autora kapitoly:*  
Táto sekcia je koncipovaná ako samostatná kapitola do učebného materiálu. V prípade potreby je možné doplniť:  
- 🖼️ Screenshoty z rozhrania Hugging Face Hub  
- 🎥 Odkazy na video tutoriály (napr. oficiálny Hugging Face YouTube kanál)  
- 📋 Pracovné listy pre študentské aktivity  
- 🔗 Zoznam slovenských modelov a datasetov na Hube  

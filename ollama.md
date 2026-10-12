# Ollama – spúšťanie jazykových modelov na vlastnom počítači  

*Verzia 2.0 · stav k októbru 2026 (Ollama 0.40). Názvy modelov, príkazy  
a systémové požiadavky sa menia, vždy ich overte na docs.ollama.com.*  

## 1. Čo je Ollama  

**Ollama** je bezplatný open-source nástroj na sťahovanie, správu  
a spúšťanie veľkých jazykových modelov (LLM) priamo na vašom počítači.  
Model beží lokálne, takže vaše texty neodchádzajú na server cudzej firmy.  

Ollama za vás vyrieši zložité veci: stiahne model v správnom formáte,  
rozhodne, koľko z neho sa zmestí do grafickej karty, a spustí ho. Vy  
napíšete jeden príkaz. Pod kapotou používa projekt **llama.cpp**.  

Ollama ponúka tri spôsoby práce:  

- **aplikáciu s chatovacím oknom** (macOS a Windows),  
- **príkazový riadok** (`ollama run …`),  
- **REST API** na adrese `http://localhost:11434`, ktoré môžu volať vaše  
  programy aj iné aplikácie.  

Modely sťahuje z vlastnej knižnice na **ollama.com/library**. Nájdete tam  
otvorené modely ako Gemma (Google), Llama (Meta), Qwen (Alibaba),  
Mistral, Phi (Microsoft), DeepSeek či gpt-oss (OpenAI). Vie spustiť aj  
modely vo formáte GGUF z Hugging Face (pozri kapitolu 5.3).  

## 2. Prečo spúšťať modely lokálne  

| Výhoda | Popis |  
|--------|-------|  
| **Súkromie** | Dáta neopúšťajú váš počítač. Vhodné pre citlivé dokumenty. |  
| **Bez poplatkov za použitie** | Platíte len za elektrinu a hardvér, nie za tokeny. |  
| **Offline prístup** | Po stiahnutí modelu funguje aj bez internetu. |  
| **Experimentovanie** | Rýchlo vyskúšate desiatky modelov a nastavení. |  
| **Prispôsobenie** | Vlastný systémový prompt a parametre cez Modelfile. |  

Lokálne modely majú aj **nevýhody**, na ktoré treba pamätať:  

- Sú **menšie a slabšie** ako najlepšie cloudové modely (GPT, Claude,  
  Gemini). Častejšie sa mýlia a halucinujú.  
- Malé modely horšie zvládajú **slovenčinu**. Ak výsledok nie je dobrý,  
  skúste otázku po anglicky alebo väčší model.  
- Potrebujú **výkonný počítač**, inak odpovedajú pomaly.  
- Modely zaberajú **veľa miesta na disku** (jednotky až stovky GB).  

> **Kedy čo použiť:** Lokálny model na súkromné dáta, učenie  
> a experimenty. Cloudový model na náročné úlohy, kde potrebujete  
> najvyššiu kvalitu.  

## 3. Aký model zvládne môj počítač  

Najdôležitejší je objem **pamäte**: model sa musí zmestiť do pamäte  
grafickej karty (VRAM) alebo do operačnej pamäte (RAM). Na Macoch  
s čipom Apple M je pamäť spoločná, preto na nich lokálne modely fungujú  
veľmi dobre.  

Veľkosť modelu sa udáva v **miliardách parametrov** (označenie `b`, napr.  
`4b` = 4 miliardy). Ollama sťahuje modely zvyčajne **kvantizované** na  
4 bity (`q4`), čo zmenší ich veľkosť asi štvornásobne za cenu malej straty  
kvality.  

| Pamäť (RAM/VRAM) | Vhodná veľkosť modelu | Príklady (Ollama) |  
|------------------|----------------------|-------------------|  
| 8 GB | do ~4b | `qwen3.5:4b`, `phi4-mini`, `ministral-3:3b`, `llama3.2` |  
| 16 GB | do ~12b | `gemma4`, `qwen3.5:9b`, `gemma4:12b`, `ministral-3:8b` |  
| 32 GB | do ~30b | `gemma4:26b`, `qwen3.5:27b`, `gpt-oss:20b` |  
| 64 GB a viac | väčšie modely | `qwen3.5:122b`, `gpt-oss:120b` |  

Ide o hrubý odhad. Ku samotnému modelu treba pripočítať pamäť pre systém  
a pre **kontextové okno** (kapitola 6.3).  

Veľkosť konkrétnej verzie modelu nájdete na stránke modelu v záložke  
**Tags**. Napríklad `qwen3.5:4b` má asi 3,3 GB a `gemma4` (verzia `e4b`)  
asi 6,6 GB.  

### 3.1 Grafická karta  

Grafická karta (GPU) nie je povinná, ale výrazne zrýchli odpovede.  

| Platforma | Podpora GPU |  
|-----------|-------------|  
| **macOS** | Apple M1 a novšie automaticky. Intel Macy len procesor (CPU). |  
| **NVIDIA** | Stačí aktuálny ovládač (verzia 550 a novšia). CUDA toolkit netreba. |  
| **AMD Radeon** | Cez ROCm v7 alebo Vulkan (podpora závisí od modelu karty). |  

Ak sa model do GPU celý nezmestí, Ollama ho rozdelí medzi GPU a CPU.  
Funguje to, ale pomalšie.  

## 4. Inštalácia  

### 4.1 Systémové požiadavky  

| Systém | Požiadavka |  
|--------|------------|  
| **macOS** | macOS 14 Sonoma alebo novší |  
| **Windows** | Windows 10 22H2 alebo novší (Home aj Pro) |  
| **Linux** | bežné distribúcie (Ubuntu, Debian, Fedora a ďalšie) |  
| **Disk** | asi 4 GB pre program, plus miesto pre modely |  

### 4.2 macOS  

1. Stiahnite `Ollama.dmg` z **ollama.com/download**.  
2. Otvorte ho a presuňte aplikáciu Ollama do priečinka **Applications**.  
3. Spustite Ollamu. Pri prvom štarte ponúkne pridanie príkazu `ollama`  
   do terminálu, potvrďte to.  

### 4.3 Windows  

1. Stiahnite `OllamaSetup.exe` z **ollama.com/download**.  
2. Spustite inštalátor. Nepotrebuje administrátorské práva, inštaluje sa  
   do vášho používateľského priečinka.  
3. Ollama potom beží na pozadí (ikona v systémovej lište) a príkaz  
   `ollama` funguje v PowerShelli aj v príkazovom riadku.  

### 4.4 Linux  

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

Skript nainštaluje Ollamu, vytvorí systémovú službu a spustí ju. Ak by  
služba nebežala, spustíte ju príkazom `sudo systemctl start ollama`.  

> **Pozor:** Príkaz `curl … | sh` spustí skript z internetu s vašimi  
> právami. Robte to len pri dôveryhodných zdrojoch, ako je oficiálna  
> stránka. Skript si môžete pred spustením najprv stiahnuť a prečítať.  

### 4.5 Overenie inštalácie  

```bash
ollama --version
```

Ak príkaz vypíše číslo verzie, Ollama je pripravená.  

## 5. Práca s modelmi  

### 5.1 Aplikácia s chatovacím oknom  

Na macOS a Windows má Ollama vlastné okno podobné ChatGPT. Vyberiete  
model zo zoznamu, napíšete otázku a model sa pri prvom použití sám  
stiahne. Do chatu môžete pretiahnuť aj obrázok alebo dokument. V  
nastaveniach (**Settings**) zmeníte napríklad dĺžku kontextu alebo  
umiestnenie modelov.  

### 5.2 Základné príkazy  

| Príkaz | Popis |  
|--------|-------|  
| `ollama` | Interaktívne menu: spustenie modelu alebo prepojenie s aplikáciou |  
| `ollama run <model>` | Spustí chat s modelom (ak treba, najprv ho stiahne) |  
| `ollama pull <model>` | Stiahne model z knižnice |  
| `ollama ls` | Zoznam stiahnutých modelov (alebo `ollama list`) |  
| `ollama ps` | Modely, ktoré sú práve načítané v pamäti |  
| `ollama stop <model>` | Uvoľní model z pamäte |  
| `ollama rm <model>` | Zmaže model z disku |  
| `ollama show <model>` | Informácie o modeli (veľkosť, kontext, licencia) |  
| `ollama create <meno> -f Modelfile` | Vytvorí vlastný model z Modelfile |  
| `ollama serve` | Spustí server ručne (ak nebeží na pozadí) |  
| `ollama signin` | Prihlásenie k účtu Ollama (potrebné pre cloudové modely) |  

**Prvý rozhovor:**  

```bash
ollama run gemma4
```

Ollama stiahne model (prvýkrát to môže trvať niekoľko minút) a otvorí  
chat. V chate fungujú špeciálne príkazy:  

| Príkaz v chate | Význam |  
|----------------|--------|  
| `/?` | Nápoveda |  
| `/set parameter temperature 0.2` | Zmena parametra |  
| `/set system "Odpovedaj stručne po slovensky."` | Nastavenie systémového promptu |  
| `/clear` | Vymaže históriu rozhovoru |  
| `/bye` | Ukončí chat |  

Viacriadkový text vložíte medzi trojité úvodzovky `"""`.  

**Jednorazová otázka bez chatu:**  

```bash
ollama run gemma4 "Vysvetli v dvoch vetách, čo je token."
```

**Popis obrázka** (pri modeloch, ktoré podporujú obrázky):  

```bash
ollama run gemma4 "Čo je na tomto obrázku? ./foto.jpg"
```

**Údržba modelov:**  

```bash
ollama pull qwen3.5:4b     # stiahnutie konkrétnej veľkosti
ollama ls                  # čo mám stiahnuté
ollama rm qwen3.5:4b       # uvoľnenie miesta na disku
```

### 5.3 Názvy modelov a značky (tags)  

Názov modelu má tvar `meno:značka`. Značka určuje veľkosť alebo variant:  

- `gemma4` je to isté ako `gemma4:latest` (predvolená verzia),  
- `qwen3.5:4b` je verzia so 4 miliardami parametrov,  
- `gpt-oss:120b-cloud` je cloudová verzia (kapitola 7).  

Modely z Hugging Face vo formáte GGUF spustíte priamo:  

```bash
ollama run hf.co/<pouzivatel>/<repozitar>
```

### 5.4 Vlastný model cez Modelfile  

**Modelfile** je krátky textový súbor, ktorý z existujúceho modelu urobí  
„vlastného asistenta“ so systémovým promptom a parametrami:  

```
FROM gemma4
PARAMETER temperature 0.3
SYSTEM """
Si trpezlivý lektor úvodu do AI. Odpovedáš po slovensky,
stručne a zrozumiteľne pre začiatočníkov.
"""
```

```bash
ollama create lektor -f Modelfile
ollama run lektor
```

Model sa nanovo netrénuje, len sa uloží nastavenie. Zaberá preto  
minimum miesta.  

## 6. Ollama v Pythone  

Keď Ollama beží, poskytuje **REST API** na adrese  
`http://localhost:11434`. Vaše programy ho môžu volať tromi spôsobmi:  

1. oficiálnou knižnicou `ollama` (najjednoduchšie),  
2. priamo cez HTTP, napr. knižnicou `requests`,  
3. knižnicou `openai`, lebo Ollama ponúka aj API kompatibilné s OpenAI.  

Potrebné knižnice nainštalujete takto (ideálne vo virtuálnom prostredí):  

```bash
pip install ollama requests openai pydantic
```

V príkladoch používame model `gemma4`. Pred spustením ho stiahnite  
(`ollama pull gemma4`) alebo v kóde nahraďte menším modelom.  

### 6.1 Knižnica ollama  

```python
from ollama import chat

response = chat(
    model="gemma4",
    messages=[
        {"role": "system", "content": "Odpovedaj stručne po slovensky."},
        {"role": "user", "content": "Aké je hlavné mesto Francúzska?"},
    ],
)

print(response.message.content)
```

Správy majú **roly**: `system` (pokyny pre model), `user` (otázka  
používateľa) a `assistant` (predchádzajúce odpovede modelu). Model si  
sám nič nepamätá, preto pri pokračovaní rozhovoru posielate celú  
históriu správ.  

**Streamovanie** (odpoveď sa vypisuje postupne, ako ju model generuje):  

```python
from ollama import chat

stream = chat(
    model="gemma4",
    messages=[{"role": "user", "content": "Napíš krátku báseň o mesiaci."}],
    stream=True,
)

for chunk in stream:
    print(chunk.message.content, end="", flush=True)
print()
```

### 6.2 Priame volanie REST API  

Tento spôsob funguje z ľubovoľného jazyka, nie len z Pythonu.  

```python
import requests

response = requests.post(
    "http://localhost:11434/api/chat",
    json={
        "model": "gemma4",
        "messages": [
            {"role": "user", "content": "Aké je hlavné mesto Francúzska?"}
        ],
        "stream": False,
    },
)

data = response.json()
print(data["message"]["content"])
```

**Streamovanie cez REST API:** Ollama posiela odpoveď po riadkoch, každý  
riadok je samostatný JSON objekt.  

```python
import json
import requests

response = requests.post(
    "http://localhost:11434/api/chat",
    json={
        "model": "gemma4",
        "messages": [
            {"role": "user", "content": "Napíš krátku báseň o mesiaci."}
        ],
    },
    stream=True,
)

for line in response.iter_lines():
    if line:
        data = json.loads(line)
        print(data["message"]["content"], end="", flush=True)
print()
```

**Zoznam stiahnutých modelov:**  

```python
import requests

data = requests.get("http://localhost:11434/api/tags").json()

for model in data["models"]:
    print(f"{model['name']}: {model['size'] / 1e9:.1f} GB")
```

Ďalšie užitočné endpointy:  

| Endpoint | Účel |  
|----------|------|  
| `/api/chat` | Rozhovor so zoznamom správ |  
| `/api/generate` | Jednoduché doplnenie textu z jedného promptu |  
| `/api/embed` | Embeddingy (číselné vektory textu, napr. pre vyhľadávanie) |  
| `/api/tags` | Zoznam stiahnutých modelov |  
| `/api/ps` | Modely načítané v pamäti |  

### 6.3 Parametre modelu  

Parametre sa posielajú v poli `options`:  

```python
from ollama import chat

response = chat(
    model="gemma4",
    messages=[{"role": "user", "content": "Vymysli názov pre kaviareň."}],
    options={"temperature": 0.9, "num_predict": 100, "num_ctx": 8192},
)

print(response.message.content)
```

| Parameter | Popis |  
|-----------|-------|  
| `temperature` | Náhodnosť odpovede. Nízka (0–0,3) = stabilné, vecné odpovede. Vysoká (0,8–1) = kreatívnejšie a rozmanitejšie. |  
| `top_p` | Model vyberá len z najpravdepodobnejších slov, ktorých súčet pravdepodobností je `top_p`. Zvyčajne sa mení buď teplota, alebo `top_p`, nie obe. |  
| `num_predict` | Maximálny počet tokenov odpovede. |  
| `num_ctx` | Dĺžka kontextového okna v tokenoch (koľko textu si model „vidí“). |  
| `seed` | Pevné číslo pre opakovateľné výsledky pri testovaní. |  

> **Pozor na kontextové okno:** Na počítačoch s menej ako 24 GB VRAM  
> používa Ollama predvolene len **4 096 tokenov** kontextu, aj keď model  
> zvláda viac. Pri dlhých dokumentoch model „zabudne“ začiatok textu bez  
> akéhokoľvek upozornenia. Pri práci s dlhým textom preto nastavte  
> `num_ctx` vyššie. Väčší kontext však potrebuje viac pamäte. Aktuálnu  
> hodnotu ukáže príkaz `ollama ps` v stĺpci `CONTEXT`.  

### 6.4 Knižnica OpenAI s Ollamou  

Ollama ponúka API kompatibilné s OpenAI na adrese  
`http://localhost:11434/v1`. Program napísaný pre OpenAI tak prepnete na  
lokálny model len zmenou adresy a názvu modelu:  

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:11434/v1",
    api_key="ollama",  # knižnica kľúč vyžaduje, Ollama ho ignoruje
)

response = client.chat.completions.create(
    model="gemma4",
    messages=[
        {"role": "system", "content": "Odpovedaj stručne po slovensky."},
        {"role": "user", "content": "Aké je hlavné mesto Francúzska?"},
    ],
    temperature=0.2,
    max_tokens=200,
)

print(response.choices[0].message.content)
```

Streamovanie funguje rovnako ako pri OpenAI:  

```python
stream = client.chat.completions.create(
    model="gemma4",
    messages=[{"role": "user", "content": "Povedz mi krátky príbeh."}],
    stream=True,
)

for chunk in stream:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="", flush=True)
print()
```

Vďaka tomu môžete aplikáciu vyvíjať a testovať zadarmo na lokálnom  
modeli a neskôr ju prepnúť na cloudový model.  

### 6.5 Štruktúrovaný výstup  

**Štruktúrovaný výstup** núti model odpovedať v pevnom formáte, typicky  
JSON, namiesto voľného textu. Program potom s odpoveďou pracuje ako  
s dátami, napríklad ju uloží do databázy alebo tabuľky.  

Najspoľahlivejšie je zadať **schému**: presný zoznam polí a ich typov.  
V Pythone sa schéma pohodlne popisuje knižnicou **Pydantic**:  

```python
from ollama import chat
from pydantic import BaseModel


class Osoba(BaseModel):
    meno: str
    vek: int
    mesto: str


class Zoznam(BaseModel):
    osoby: list[Osoba]


text = """
John Doe je softvérový inžinier z New Yorku. Má 30 rokov a rád chodí
na túry. Jane Smith je grafická dizajnérka zo San Francisca. Má 28 rokov
a rada maľuje a cestuje.
"""

response = chat(
    model="gemma4",
    messages=[
        {"role": "user", "content": f"Vypíš osoby z textu ako JSON:\n{text}"}
    ],
    format=Zoznam.model_json_schema(),  # model musí dodržať túto schému
    options={"temperature": 0},
)

data = Zoznam.model_validate_json(response.message.content)
for osoba in data.osoby:
    print(osoba.meno, osoba.vek, osoba.mesto)
```

Jednoduchšia možnosť je `format="json"`. Vtedy model vráti platný JSON,  
no názvy a štruktúru polí si zvolí sám, takže sa môžu pri každom volaní  
líšiť.  

> Schéma zaručí **formát**, nie **správnosť**. Model môže do správneho  
> poľa napísať nesprávny údaj, preto výsledky kontrolujte.  

## 7. Cloudové modely v Ollame  

Najväčšie otvorené modely potrebujú stovky GB pamäte. Ollama ich preto  
ponúka aj ako **cloudové modely** s príponou `:cloud`, napríklad  
`gpt-oss:120b-cloud`. Ovládajú sa rovnako ako lokálne (CLI, Python,  
API), no výpočet beží na serveroch Ollamy.  

```bash
ollama signin
ollama run gpt-oss:120b-cloud
```

- Vyžadujú účet Ollama. Bezplatný účet má obmedzené použitie, vyššie  
  limity sú v platených plánoch (ollama.com/pricing).  
- Prompty **odchádzajú na server**, takže stratíte hlavnú výhodu  
  lokálneho behu: súkromie. Na citlivé dáta ich nepoužívajte.  
- Cloudové funkcie sa dajú v Ollame úplne vypnúť (režim len lokálne).  

## 8. Prepojenie s ďalšími aplikáciami  

Lokálny model môžu využívať aj iné programy:  

- **Programovacie nástroje a agenti** – príkaz `ollama launch` prepojí  
  Ollamu napríklad s Claude Code, Codexom, OpenCode alebo VS Code.  
  Pri agentoch nastavte kontext aspoň na 64 000 tokenov a počítajte s  
  tým, že malé lokálne modely zvládajú agentové úlohy výrazne horšie ako  
  veľké cloudové.  
- **Webové rozhrania** – napríklad Open WebUI (chat podobný ChatGPT vo  
  vlastnom prehliadači, aj pre viacerých používateľov).  
- **Aplikácie na prácu s dokumentmi** – napríklad AnythingLLM  
  (otázky nad vlastnými PDF súbormi).  
- **Knižnice na tvorbu AI aplikácií** – LangChain, LlamaIndex a ďalšie.  

## 9. Bezpečnosť  

- **API Ollamy nemá heslo.** Predvolene počúva len na vašom počítači  
  (`127.0.0.1`), čo je bezpečné. Ak nastavíte `OLLAMA_HOST=0.0.0.0`,  
  sprístupníte ho celej sieti a ktokoľvek v nej môže používať vaše modely.  
  Na internete sú tisíce takto nechránených serverov Ollama.  
  Server preto nikdy nevystavujte priamo do internetu.  
- **Modely sťahujte z dôveryhodných zdrojov** (oficiálna knižnica,  
  overení autori na Hugging Face).  
- **Skontrolujte licenciu modelu** (`ollama show <model> --license`).  
  Niektoré modely obmedzujú komerčné použitie.  
- **Lokálny model nie je automaticky správny.** Platí všetko, čo viete  
  o halucináciách: výstupy overujte.  

## 10. Praktické cvičenie  

1. Nainštalujte Ollamu a overte ju príkazom `ollama --version`.  
2. Podľa tabuľky v kapitole 3 vyberte model pre váš počítač a spustite  
   ho cez `ollama run`.  
3. Položte rovnakú otázku po slovensky a po anglicky. Porovnajte kvalitu  
   odpovedí.  
4. Príkazom `ollama ps` zistite, či model beží na GPU alebo CPU a aký  
   veľký má kontext.  
5. Vytvorte Modelfile s vlastným systémovým promptom (napr. „lektor“  
   alebo „prekladateľ“) a vyskúšajte ho.  
6. Spustite príklad zo sekcie 6.1 v Pythone.  
7. **Bonus:** Upravte príklad štruktúrovaného výstupu tak, aby z textu  
   inzerátu vytiahol názov produktu, cenu a stav (nový/použitý).  
8. **Bonus:** Vypnite internet a overte, že model stále funguje.  

## 11. Zhrnutie  

| Téma | Kľúčové body |  
|------|--------------|  
| **Čo je Ollama** | Bezplatný nástroj na lokálne spúšťanie otvorených LLM |  
| **Výhody** | Súkromie, offline prístup, žiadne poplatky za tokeny |  
| **Nevýhody** | Slabšie modely, nároky na hardvér, horšia slovenčina |  
| **Výber modelu** | Podľa pamäte: 8 GB → do 4b, 16 GB → do 12b |  
| **Ovládanie** | Aplikácia, príkazy `run`, `pull`, `ls`, `ps`, `rm` |  
| **Programovanie** | Knižnica `ollama`, REST API, OpenAI-kompatibilné API |  
| **Pozor na** | Predvolený kontext 4 096 tokenov, nevystavovať API do siete |  
| **Cloudové modely** | Prípona `:cloud`, výkonnejšie, ale dáta idú na server |  

## 12. Užitočné odkazy  

- Oficiálna stránka a sťahovanie: ollama.com  
- Knižnica modelov: ollama.com/library  
- Dokumentácia: docs.ollama.com  
- Zdrojový kód: github.com/ollama/ollama  
- Knižnica pre Python: github.com/ollama/ollama-python  

## Otázky a diskusia  

- Pre aké úlohy vo vašej práci by ste uprednostnili lokálny model pred  
  cloudovým?  
- Je lokálny model automaticky v súlade s GDPR? Čo všetko treba ešte  
  zvážiť?  
- Kedy sa oplatí kúpiť výkonnejší hardvér a kedy platiť za cloudové API?  

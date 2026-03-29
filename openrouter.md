# Kapitola: OpenRouter – Jednotná brána do sveta AI modelov  

V ekosystéme generatívnej AI existujú desiatky poskytovateľov modelov –  
OpenAI, Anthropic, Google, Meta, Mistral, xAI a ďalší. Každý z nich má  
vlastné API, vlastné cenníky, vlastné limity a vlastnú dokumentáciu.  
Pre vývojára to znamená jeden problém: ako pristupovať k rôznym modelom  
bez toho, aby musel spravovať desiatky rôznych integrácií?  

**OpenRouter** je odpoveďou na túto otázku. Je to **jednotná API brána**,  
ktorá za jednotným rozhraním skrýva stovky AI modelov od rôznych  
poskytovateľov. Vývojár si otvorí jeden účet, používa jedno API, a má  
prístup k prakticky celému trhu s AI modelmi.  

> 💡 **Kľúčová metafora:** OpenRouter je ako cestovná agentúra pre AI modely.  
> Namiesto toho, aby ste volali priamo každú leteckú spoločnosť, zavoláte  
> jednej agentúre – a tá vám zarezervuje let kdekoľvek, za najlepšiu cenu.  

## Vznik a zakladatelia  

OpenRouter vznikol v roku **2023** ako startup so sídlom v San Franciscu.  
Zakladatelia sú:  

- **Alex Atallah** – spoluzakladateľ OpenSea (NFT platforma), ktorý po odchode  
  z OpenSea hľadal projekt na pomedzí AI a infraštruktúry  
- **William Galebach** – skúsený softvérový inžinier so záujmom o  
  štandardizáciu AI API  

Projekt rástol organicky – bez masívnej mediálnej kampane. Vývojárska komunita  
ho objavila sama, pretože riešil skutočný problém: **fragmentáciu AI trhu**.  

K marcu 2026 OpenRouter spracúva každý mesiac **miliardy tokenov** pre státisíce  
vývojárov a firiem po celom svete. Stal sa de facto štandardom pre aplikácie,  
ktoré potrebujú pracovať s viacerými modelmi naraz.  

## Čo OpenRouter rieši: Problém fragmentácie  

Aby sme pochopili, prečo OpenRouter vznikol, pozrime sa na situáciu vývojára  
bez neho.  

### Život bez OpenRouteru  

Predstavte si, že budujete aplikáciu, ktorá potrebuje:  
- GPT-5 pre kreatívne úlohy (OpenAI API)  
- Claude Opus 4.6 pre analýzu dokumentov (Anthropic API)  
- Gemini Flash pre rýchle odpovede (Google AI API)  
- Llama 4 pre lacné spracovanie veľkých objemov (Meta / vlastný hosting)  

To znamená:  
1. 4 rôzne účty a 4 rôzne API kľúče  
2. 4 rôzne formáty požiadaviek a odpovedí  
3. 4 rôzne cenníky a faktúry  
4. 4 rôzne limity (rate limits) a chybové kódy  
5. Nutnosť aktualizovať kód pri každej zmene API  

### Život s OpenRouterom  

S OpenRouterom:  
1. **Jeden účet, jeden API kľúč**  
2. **Jeden formát** – kompatibilný s OpenAI API (štandard odvetvia)  
3. **Jedna faktúra** za všetky modely  
4. **Automatické zálohy** – ak jeden model zlyhá, OpenRouter prepne na iný  
5. **Centrálny monitoring** spotreby a nákladov  

## Ako funguje OpenRouter technicky  

### OpenAI-kompatibilné API  

OpenRouter používa rovnaký formát požiadaviek ako OpenAI. To je kľúčové  
rozhodnutie – väčšina AI knižníc a nástrojov už vie pracovať s OpenAI formátom.  
Stačí zmeniť dva parametre:  

```python  
from openai import OpenAI  

# PRED: priamo na OpenAI  
client = OpenAI(api_key="sk-...")  
response = client.chat.completions.create(  
    model="gpt-5",  
    messages=[{"role": "user", "content": "Ahoj!"}]  
)  

# PO: cez OpenRouter – zmena len dvoch riadkov  
client = OpenAI(  
    base_url="https://openrouter.ai/api/v1",  
    api_key="sk-or-..."  # OpenRouter kľúč  
)  
response = client.chat.completions.create(  
    model="anthropic/claude-opus-4-6",  # iný formát názvu modelu  
    messages=[{"role": "user", "content": "Ahoj!"}]  
)  
```  

> Toto je príklad tzv. **drop-in replacement** – náhrady,  
> ktorá nevyžaduje prepísanie celého kódu. Stačí zmeniť `base_url` a `api_key`.  

### Nomenklatúra modelov  

OpenRouter používa jednotný formát pre názvy modelov:  

```  
{poskytovateľ}/{model-name}:{variant}  
```  

Príklady:  
| OpenRouter názov | Popis |  
| :--- | :--- |  
| `openai/gpt-5` | GPT-5 od OpenAI |  
| `anthropic/claude-opus-4-6` | Claude Opus 4.6 od Anthropic |  
| `google/gemini-3-1-pro` | Gemini 3.1 Pro od Google |  
| `meta-llama/llama-4-maverick` | Llama 4 Maverick od Meta |  
| `mistralai/mistral-large` | Mistral Large od Mistral AI |  
| `deepseek/deepseek-v3` | DeepSeek V3 |  
| `x-ai/grok-3` | Grok 3 od xAI |  

### Streaming a pokročilé funkcie  

OpenRouter podporuje všetky štandardné funkcie moderných AI API:  

```python  
# Streaming odpovedí (tokeny sa posielajú postupne)  
stream = client.chat.completions.create(  
    model="anthropic/claude-sonnet-4-6",  
    messages=[{"role": "user", "content": "Napíš báseň o AI."}],  
    stream=True  
)  
for chunk in stream:  
    print(chunk.choices[0].delta.content or "", end="")  

# Function calling (volanie funkcií)  
response = client.chat.completions.create(  
    model="openai/gpt-5",  
    messages=[{"role": "user", "content": "Aké je počasie v Bratislave?"}],  
    tools=[{  
        "type": "function",  
        "function": {  
            "name": "get_weather",  
            "parameters": {"type": "object", "properties": {"city": {"type": "string"}}}  
        }  
    }]  
)  
```  

## Kľúčové funkcie OpenRouteru  

### 1. Model Routing – Inteligentné smerovanie  

OpenRouter umožňuje nastaviť pravidlá, ako sa má vybrať model pre každú  
požiadavku. Toto je jedna z najcennejších funkcií pre produkčné aplikácie.  

**Automatické zálohy (Fallbacks):**  
```python  
response = client.chat.completions.create(  
    model="anthropic/claude-opus-4-6",  
    messages=[...],  
    extra_body={  
        "route": "fallback",  # Ak Opus zlyhá, skús ďalší model  
        "models": [  
            "anthropic/claude-opus-4-6",  
            "openai/gpt-5",  
            "google/gemini-3-1-pro"  
        ]  
    }  
)  
```  

**Smerovanie podľa ceny:**  
```python  
extra_body={  
    "route": "cheapest",  # Vyber najlacnejší dostupný model zo zoznamu  
    "models": ["openai/gpt-5", "anthropic/claude-sonnet-4-6", "google/gemini-3-flash"]  
}  
```  

**Smerovanie podľa latencie:**  
```python  
extra_body={  
    "route": "fastest",  # Vyber model s najrýchlejšou dobou odozvy  
}  
```  

### 2. Porovnávač modelov a cenník  

Na stránke **openrouter.ai/models** nájdete živý prehľad všetkých dostupných  
modelov s kľúčovými parametrami:  

| Parameter | Popis |  
| :--- | :--- |  
| **Cena za vstupný token** | Cena za 1 milión tokenov na vstupe (prompt) |  
| **Cena za výstupný token** | Cena za 1 milión tokenov na výstupe (odpoveď) |  
| **Kontextové okno** | Maximálny počet tokenov v jednej konverzácii |  
| **Maximálny výstup** | Maximálny počet tokenov v jednej odpovedi |  
| **Latencia** | Priemerný čas do prvého tokenu (TTFT) |  
| **Priepustnosť** | Tokeny za sekundu |  
| **Modality** | Text, obrázky, zvuk – čo model zvláda |  

Príklad porovnania cien (orientačné hodnoty, marec 2026):  

| Model | Vstup ($/1M tok.) | Výstup ($/1M tok.) |  
| :--- | ---: | ---: |  
| `openai/gpt-5` | $2,50 | $10,00 |  
| `anthropic/claude-opus-4-6` | $15,00 | $75,00 |  
| `anthropic/claude-sonnet-4-6` | $3,00 | $15,00 |  
| `google/gemini-3-1-pro` | $1,25 | $5,00 |  
| `google/gemini-3-flash` | $0,075 | $0,30 |  
| `meta-llama/llama-4-scout` | $0,08 | $0,30 |  
| `deepseek/deepseek-v3` | $0,27 | $1,10 |  

> 💡 **Praktická rada:** Výstupné tokeny sú vždy drahšie ako vstupné – model  
> „číta" prompt lacno, ale generovanie každého tokenu odpovede je výpočtovo  
> nákladnejšie. Pri optimalizácii nákladov sa sústreďte na skracovanie výstupu.  

### 3. Bezplatné modely  

OpenRouter ponúka aj **bezplatné modely** – väčšinou open-source modely hostované  
zadarmo (s obmedzenými rate limitmi):  

- `meta-llama/llama-4-scout:free`  
- `mistralai/mistral-7b-instruct:free`  
- `google/gemma-3-27b-it:free`  
- `deepseek/deepseek-v3:free`  

Sú ideálne na prototypovanie, testovanie a projekty s malým objemom požiadaviek.  

> ⚠️ **Pozor:** Bezplatné modely majú nižší rate limit a horšiu dostupnosť.  
> Pre produkčné aplikácie vždy používajte platené varianty.  

### 4. Štatistiky a monitoring  

Na dashboarde OpenRouteru vidíte:  
- Celkové výdavky a rozdelenie podľa modelov  
- Počet požiadaviek a tokenov za časové obdobie  
- Chybovosť a latenciu pre každý model  
- Limity použitia a upozornenia  

### 5. Správa API kľúčov  

OpenRouter umožňuje vytvoriť **viacero API kľúčov** s rôznymi obmedzeniami:  

```  
Kľúč pre produkciu: limit $500/mesiac, prístup len ku vybraným modelom  
Kľúč pre vývoj:    limit $20/mesiac, prístup ku všetkým modelom  
Kľúč pre testov:   limit $5/mesiac, len bezplatné modely  
```  

Toto je dôležité z bezpečnostného hľadiska – ak sa kľúč vystaví (napr. omylom  
commitnutím do GitHubu), škodu možno obmedziť nastavenými limitmi.  

## Praktické použitie v Pythone  

### Inštalácia  

```bash  
pip install openai  # OpenRouter využíva rovnakú knižnicu  
```  

### Základný príklad  

```python  
from openai import OpenAI  

client = OpenAI(  
    base_url="https://openrouter.ai/api/v1",  
    api_key="sk-or-v1-...",  # Váš OpenRouter kľúč  
)  

def ask_ai(question: str, model: str = "anthropic/claude-sonnet-4-6") -> str:  
    response = client.chat.completions.create(  
        model=model,  
        messages=[  
            {"role": "system", "content": "Si nápomocný asistent."},  
            {"role": "user", "content": question}  
        ]  
    )  
    return response.choices[0].message.content  

# Použitie  
answer = ask_ai("Čo je to strojové učenie?")  
print(answer)  
```  

### Porovnávanie modelov  

```python  
models = [  
    "openai/gpt-5",  
    "anthropic/claude-sonnet-4-6",  
    "google/gemini-3-1-pro",  
]  

question = "Vysvetli mi kvantové prepletenie v dvoch vetách."  

for model in models:  
    print(f"\n--- {model} ---")  
    print(ask_ai(question, model=model))  
```  

### Sledovanie nákladov  

```python  
response = client.chat.completions.create(  
    model="anthropic/claude-opus-4-6",  
    messages=[{"role": "user", "content": "Analyzuj tento text: ..."}]  
)  

# Informácie o spotrebe tokenov  
usage = response.usage  
print(f"Vstupné tokeny: {usage.prompt_tokens}")  
print(f"Výstupné tokeny: {usage.completion_tokens}")  
print(f"Celkom tokenov: {usage.total_tokens}")  
```  

## Ekosystém a integrácie  

### Podpora knižníc tretích strán  

Keďže OpenRouter je kompatibilný s OpenAI API, funguje automaticky s  
populárnymi knižnicami:  

| Knižnica | Použitie |  
| :--- | :--- |  
| **LangChain** | Framework pre LLM aplikácie a reťazce promptov |  
| **LlamaIndex** | RAG systémy a práca s dokumentmi |  
| **Vercel AI SDK** | AI integrácie vo webových aplikáciách (Next.js) |  
| **AutoGen** | Muti-agentné systémy od Microsoftu |  
| **CrewAI** | Orchestrácia AI agentov |  
| **LiteLLM** | Ďalší API wrapper, kompatibilný s OpenRouter |  

### JavaScript / TypeScript  

```typescript  
import OpenAI from "openai";  

const client = new OpenAI({  
  baseURL: "https://openrouter.ai/api/v1",  
  apiKey: process.env.OPENROUTER_API_KEY,  
});  

const response = await client.chat.completions.create({  
  model: "google/gemini-3-flash",  
  messages: [{ role: "user", content: "Hello!" }],  
});  

console.log(response.choices[0].message.content);  
```  

### Priame HTTP volanie (cURL)  

```bash  
curl https://openrouter.ai/api/v1/chat/completions \  
  -H "Authorization: Bearer $OPENROUTER_API_KEY" \  
  -H "Content-Type: application/json" \  
  -d '{  
    "model": "meta-llama/llama-4-maverick",  
    "messages": [{"role": "user", "content": "Ahoj!"}]  
  }'  
```  

## OpenRouter vs. priame API  

| Aspekt | Priame API | OpenRouter |  
| :--- | :--- | :--- |  
| **Počet účtov** | Jeden na poskytovateľa | Jeden pre všetko |  
| **Formát API** | Rôzny (OpenAI, Anthropic, Google...) | Jednotný (OpenAI-kompatibilný) |  
| **Faktúry** | Viacero faktúr | Jedna faktúra |  
| **Zálohovanie** | Manuálne | Automatické fallbacky |  
| **Nové modely** | Treba aktualizovať integráciu | Dostupné okamžite |  
| **Cena** | Priama cena poskytovateľa | Priama cena + malá prirážka (~5 %) |  
| **Latencia** | Minimálna (priame spojenie) | Mierne vyššia (+10-50 ms) |  
| **Súkromie dát** | 100 % u poskytovateľa | Dáta prechádzajú cez OpenRouter |  

> 🎯 **Kedy použiť priame API:** Keď pracujete výhradne s jedným modelom  
> v produkčnej aplikácii s vysokými nárokmi na latenciu a súkromie.  
>  
> 🎯 **Kedy použiť OpenRouter:** Pri vývoji, prototypovaní, porovnávaní  
> modelov, alebo ak vaša aplikácia vyžaduje flexibilitu výberu modelu.  

## Bezpečnostné aspekty  

Pri práci s OpenRouterom platia štandardné bezpečnostné pravidlá pre API kľúče:  

1. **Nikdy neukladajte kľúč priamo v kóde** – používajte premenné prostredia:  
   ```bash  
   export OPENROUTER_API_KEY="sk-or-v1-..."  
   ```  
   ```python  
   import os  
   api_key = os.environ["OPENROUTER_API_KEY"]  
   ```  

2. **Nastavte limity výdavkov** – v dashboarde môžete nastaviť maximálny  
   mesačný limit, aby nedošlo k neočakávanému predraženiu.  

3. **Rotujte kľúče pravidelne** – a okamžite po podozrení na kompromitáciu.  

4. **Použite samostatné kľúče** pre vývoj, staging a produkciu.  

5. **Sledujte využitie** – neočakávaný nárast spotreby môže signalizovať  
   zneužitie kľúča.  

> ⚠️ **Dôležité:** OpenRouter vidí obsah vašich promptov aj odpovedí.  
> Pre aplikácie s citlivými dátami (zdravotníctvo, právo, financie) zvášte,  
> či je tento kompromis prijateľný, alebo radšej použite priame API.  

## Prístup a cenové plány  

| Prístup | Popis |  
| :--- | :--- |  
| **openrouter.ai** | Webová aplikácia, dashboard, správa kľúčov, chatovanie |  
| **API** | Priamy prístup cez API kľúč, platba podľa spotreby tokenov |  
| **Bezplatný tier** | Prístup k bezplatným modelom bez platobnej karty |  
| **Platený tier** | Platba za skutočnú spotrebu (pay-as-you-go), dobíjanie kreditu |  

Nie je potrebný žiadny mesačný paušál – platíte len to, čo skutočne použijete.  
Minimálne dobíjanie je zvyčajne **5 dolárov**, čo je dostatok pre experimentovanie.  

## Špeciálne funkcie pre vývojárov  

### Online/Offline modely  

OpenRouter rozlišuje medzi:  
- **Online modely** – majú prístup k internetu (napr. Perplexity)  
- **Offline modely** – pracujú len s kontextom konverzácie (väčšina modelov)  

### Multimodálne vstupy  

Modely, ktoré podporujú obrázky, ich prijímajú cez štandardný OpenAI formát:  

```python  
response = client.chat.completions.create(  
    model="google/gemini-3-1-pro",  
    messages=[{  
        "role": "user",  
        "content": [  
            {"type": "text", "text": "Čo vidíš na tomto obrázku?"},  
            {"type": "image_url", "image_url": {"url": "https://..."}}  
        ]  
    }]  
)  
```  

### Parametre generovania  

```python  
response = client.chat.completions.create(  
    model="openai/gpt-5",  
    messages=[...],  
    temperature=0.7,        # Kreativita: 0.0 (deterministický) – 2.0 (veľmi kreatívny)  
    max_tokens=1024,        # Maximálny počet výstupných tokenov  
    top_p=0.9,              # Nucleus sampling  
    frequency_penalty=0.1,  # Penalizácia za opakovanie slov  
    presence_penalty=0.1,   # Penalizácia za opakovanie tém  
)  
```  

## OpenRouter v kontexte AI ekosystému  

OpenRouter nie je jediný takýto nástroj – existujú aj alternatívy:  

| Nástroj | Typ | Špecialita |  
| :--- | :--- | :--- |  
| **OpenRouter** | API Gateway | Najväčší výber modelov, community |  
| **LiteLLM** | Open-source proxy | Self-hosting, enterprise |  
| **Amazon Bedrock** | Cloud platforma | AWS integrácia, bezpečnosť |  
| **Azure AI Foundry** | Cloud platforma | Microsoft ekosystém, enterprise |  
| **Google Vertex AI** | Cloud platforma | Google ekosystém, Gemini modely |  

> 💡 **Záver:** OpenRouter obsadzuje medzeru medzi priamymi API (príliš  
> fragmentované) a cloudovými platformami (príliš drahé a viazané na jedného  
> poskytovateľa). Je ideálny pre indie vývojárov, startupy a výskumníkov.  

## Zhrnutie kapitoly  

- **OpenRouter** je jednotná API brána, ktorá sprístupňuje stovky AI modelov  
  cez jedno rozhranie kompatibilné s OpenAI štandardom.  
- Zakladatelia sú **Alex Atallah** (spoluzakladateľ OpenSea) a  
  **William Galebach**, startup sídli v San Franciscu od roku 2023.  
- Kľúčové výhody: jeden účet, jeden API kľúč, jedna faktúra, automatické  
  zálohy a centrálny monitoring.  
- Technicky funguje ako **proxy** – požiadavky prekladá do formátu  
  príslušného poskytovateľa a vracia štandardizovanú odpoveď.  
- Cena je **pay-as-you-go** s malou prirážkou (~5 %) nad cenou poskytovateľa.  
- Ideálny pre prototypovanie, porovnávanie modelov a aplikácie,  
  ktoré potrebujú pracovať s viacerými modelmi naraz.  
- Nie je vhodný pre aplikácie s prísnymi požiadavkami na **súkromie dát**  
  alebo minimálnu latenciu.  

## Otázky a diskusia  



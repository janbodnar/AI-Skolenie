# Práca s obrázkami – generovanie a úprava  

Doteraz sme s jazykovými modelmi pracovali najmä cez text. Moderné AI  
však obrázky nielen „vidí", ale ich aj **vytvára a upravuje**. Stačí  
napísať, čo chceme – a model nakreslí ilustráciu, odstráni z fotografie  
rušivý predmet, vymení pozadie alebo spojí niekoľko fotiek do jednej  
scény. V tejto kapitole si ukážeme tri cesty k takýmto modelom:  
bezplatnú aplikáciu **Gemini** s modelom **Nano Banana**, modely  
**GPT Image** od OpenAI a modely dostupné cez **OpenRouter**, napríklad  
**FLUX 3** od nemeckej firmy Black Forest Labs.  

*Stav k októbru 2026. Údaje o modeloch, cenách a limitoch sa rýchlo menia.*  

## Ako AI vytvára obrázky  

Prvé známe generátory obrázkov (DALL-E, Midjourney, Stable Diffusion)  
fungovali ako šikovné kresliace stroje. Z promptu si vybrali hlavne  
kľúčové slová – „mačka, klobúk, pláž" – a podľa nich nakreslili obrázok.  
Dlhšie vety, presné pokyny či nápisy im robili problémy.  

Dnešné modely ako **Nano Banana** alebo **GPT Image** sú súčasťou  
veľkého jazykového modelu – rovnakého typu, s akým sa rozprávame v chate.  
Zadanie teda najprv pochopia ako text a až potom kreslia. Vďaka tomu:  

*   rozumejú bežným vetám, nielen kľúčovým slovám,  
*   pamätajú si priebeh rozhovoru, takže obrázok môžeme upravovať  
    po krokoch („teraz pridaj dážď"),  
*   vedia, ako vyzerajú známe miesta a veci – napríklad Bratislavský hrad.  

## Čo dnes s obrázkami zvládneme  

*   **Generovanie z textu** (*text-to-image*) – obrázok podľa popisu.  
*   **Úprava fotografie** (*image editing*) – „odstráň z fotky nožnice",  
    „zmeň farbu auta na červenú", „pridaj na stôl šálku kávy".  
*   **Výmena pozadia** – produkt alebo osoba v novom prostredí.  
*   **Kombinovanie referencií** – model dostane viacero obrázkov  
    (osobu, oblečenie, miestnosť) a spojí ich do jednej scény.  
*   **Zmena štýlu** – fotografia ako akvarel, komiks či 3D render.  
*   **Infografiky a diagramy** – obrázok s textom, číslami a šípkami.  
*   **Rozšírenie záberu** (*outpainting*) – domyslenie okolia obrázka  
    alebo zmena pomeru strán.  

## Prehľad modelov  

| Model | Tvorca | Kde ho nájdeme | Silné stránky |
| :--- | :--- | :--- | :--- |
| **Nano Banana 2** | Google | aplikácia Gemini – **zadarmo** | Úprava fotiek, text, konzistentné postavy |
| **Nano Banana 2.1** | Google | Gemini (platené tarify), Gemini API | Lepšia konzistencia, infografiky, nižšia cena v API |
| **Nano Banana Pro** | Google | Gemini (platené tarify), Gemini API | Najzložitejšie zadania, lokalizácia textu |
| **GPT Image 2.5 Flare** | OpenAI | ChatGPT, OpenAI API, OpenRouter | Rýchle bežné generovanie, až 16 referencií |
| **GPT Image 2.5 Sunburst** | OpenAI | OpenAI API, OpenRouter | Presné úpravy, text, kompozícia |
| **FLUX 3 Image** | Black Forest Labs | BFL API, OpenRouter | Úpravy s pixelovou presnosťou, 4K |
| **FLUX 3 Image Klein** | Black Forest Labs | OpenRouter, otvorené váhy | Lacný, beží aj na hernej grafickej karte |

Okrem nich existuje množstvo ďalších nástrojov – **Midjourney**  
(obľúbený medzi dizajnérmi pre estetiku), **Ideogram** (text v obrázkoch),  
**Seedream** od ByteDance či **Adobe Firefly** (trénovaný na licencovaných  
dátach, integrovaný do Photoshopu).  

## Google Nano Banana – zadarmo v aplikácii Gemini  

### Odkiaľ pochádza zvláštne meno  

V auguste 2025 sa v anonymnom porovnávaní modelov **LMArena** objavil  
neznámy model s označením **nano-banana**. Výborne upravoval fotografie  
a rýchlo sa stal virálnym. Ukázalo sa, že ide o **Gemini 2.5 Flash  
Image** od Googlu. Prezývka sa však ujala natoľko, že ju Google prijal  
ako oficiálny názov celej rodiny obrázkových modelov.  

| Model | Identifikátor v API | Dátum | Poznámka |
| :--- | :--- | :--- | :--- |
| Nano Banana | `gemini-2.5-flash-image` | aug. 2025 | Pôvodný virálny model, dnes zastaraný |
| Nano Banana Pro | `gemini-3-pro-image` | nov. 2025 | Prémiový model na najzložitejšie úlohy |
| Nano Banana 2 | `gemini-3.1-flash-image` | feb. 2026 | Rýchlosť Flash, kvalita blízka Pro |
| Nano Banana 2 Lite | `gemini-3.1-flash-lite-image` | 2026 | Najlacnejší a najrýchlejší |
| Nano Banana 2.1 | `gemini-nano-banana-2.1` | 6. okt. 2026 | Aktuálne odporúčaný model v API |

### Ako začať  

1.  Otvoríme [gemini.google.com](https://gemini.google.com) alebo  
    mobilnú aplikáciu Gemini a prihlásime sa účtom Google.  
2.  V ponuke nástrojov zvolíme **🍌 Vytvoriť obrázky** (*Create images*).  
3.  Napíšeme prompt, prípadne nahráme fotografiu, ktorú chceme upraviť.  
4.  Výsledok môžeme ďalej upravovať v konverzácii: „pozadie nech je  
    tmavšie", „zväčši nápis", „teraz to isté v štýle akvarelu".  

Bezplatná verzia aplikácie Gemini používa model **Nano Banana 2**  
s rozlíšením približne 1K – 2K. Predplatitelia taríf Google AI (Pro, Plus,  
Ultra) majú k dispozícii **Nano Banana 2.1**, vyššie limity a možnosť  
obrázok pregenerovať modelom **Nano Banana Pro**. Google pre bezplatnú  
verziu nezverejňuje presný denný počet obrázkov – limit sa priebežne  
obnovuje.  

### Vodoznaky  

Každý obrázok z Gemini nesie neviditeľný vodoznak **SynthID**.  
Obrázky z bezplatnej verzie majú navyše aj **viditeľný vodoznak**.  
Či obrázok vytvorila AI od Googlu, zistíme tak, že ho nahráme do Gemini  
a opýtame sa.  

## OpenAI – GPT Image 2.5  

OpenAI začala s obrázkami modelom **DALL-E** (2021). V roku 2025 ho  
nahradil **GPT Image**, ktorý je priamo súčasťou ChatGPT aj API.  
**8. septembra 2026** vyšla generácia **GPT Image 2.5**, ktorá prvý raz  
prichádza ako **dva samostatné modely**. Nelíšia sa nastavením kvality,  
ale typom práce, pre ktorú sú určené:  

*   **GPT Image 2.5 Flare** (`gpt-image-2.5-flare`) – predvolená voľba  
    pre väčšinu aplikácií. Je rýchlejšia, vhodná na bežné generovanie  
    a rýchle skúšanie variantov. Pri úpravách zvládne až **16  
    referenčných obrázkov**.  
*   **GPT Image 2.5 Sunburst** (`gpt-image-2.5-sunburst`) – model  
    na generovanie a úpravy, pri ktorých záleží na **presnosti**:  
    odstránenie predmetu, výmena pozadia, presný text. Je pomalší.  

V **ChatGPT** je GPT Image 2.5 dostupný aj v bezplatnej verzii (s limitmi).  
Stačí v konverzácii požiadať o obrázok alebo nahrať fotku a napísať,  
čo s ňou chceme urobiť.  

### Ktorý model si vybrať  

V zozname modelov (napríklad v nástrojoch pre vývojárov) nájdeme celý  
rad obrázkových modelov:  

![Obrázkové modely OpenAI](data/openai-image-modely.png)  

*   **Flare** ako predvolený model; **Sunburst** na úpravy, pri ktorých  
    má zvyšok fotografie zostať nedotknutý.  
*   **Datované verzie** (*snapshots*), napr.  
    `gpt-image-2.5-flare-2026-09-08`, sa nemenia. Model bez dátumu môže  
    OpenAI potichu aktualizovať. Pre kurz, prezentáciu či aplikáciu, kde  
    chceme rovnaké správanie pri skúške aj naostro, použijeme datovanú  
    verziu.  
*   **`chatgpt-image-latest`** je pohyblivý alias – ukazuje na to, čo  
    práve používa ChatGPT, a výsledky sa môžu zo dňa na deň zmeniť.  
*   **`gpt-image-1-mini`, `gpt-image-1.5` a `gpt-image-2`** sú staršie  
    generácie. Fungujú, no pre nový projekt nie je dôvod ich uprednostniť;  
    `gpt-image-2` môže slúžiť ako záloha.  

Najlepšie je oba modely vyskúšať na vlastnej fotografii. Ak je výsledok  
takmer rovnaký, stačí Flare na všetko.  

### Ceny  

Oba modely majú rovnaké **tokenové sadzby**. Cena obrázka preto závisí  
najmä od jeho **veľkosti** a **kvality** (`low`, `medium`, `high`,  
`xhigh`, `max`). Podľa dostupných prehľadov stojí obrázok 1024 × 1024  
od približne jedného centa pri nízkej kvalite po zhruba 0,20 $ pri  
maximálnej. Pred plánovaním rozpočtu je dobré overiť ceny v kalkulačke  
na stránke OpenAI. Používanie obrázkových modelov v API navyše vyžaduje  
**overenie organizácie** (*Organization Verification*).  

## OpenRouter – FLUX 3 a ďalšie modely  

Z kapitoly o OpenRouteri vieme, že ide o bránu k stovkám jazykových  
modelov. OpenRouter však sprístupňuje aj **obrázkové modely** – od  
OpenAI, Googlu, ByteDance aj Black Forest Labs. Výhodou je opäť jeden  
účet a jednoduché porovnanie modelov.  

### Black Forest Labs a FLUX 3  

**Black Forest Labs** (BFL) je nemecká firma z Freiburgu, ktorú v roku  
2024 založili výskumníci stojaci za populárnym open-source modelom  
**Stable Diffusion**. Patrí k najvýznamnejším európskym firmám v oblasti  
generatívnej AI.  

Rodina **FLUX 3** bola predstavená v júli 2026 ako multimodálny model  
trénovaný naraz na obrázkoch, videu a zvuku. Postupne z nej vyšli:  

*   **FLUX 3 Video** – prvý verejný videomodel BFL (klipy so zvukom).  
*   **FLUX 3 Image** (1. októbra 2026) – vlajkový obrázkový model:  
    *   rozlíšenie až **4K** bez dodatočného zväčšovania,  
    *   až **10 referenčných obrázkov** naraz,  
    *   **rozloženie scény v JSON** – každý prvok má svoj popis  
        a súradnice (*bounding box*),  
    *   úpravy, ktoré pixely mimo upravovanej oblasti nechajú  
        **úplne nezmenené**.  
*   **FLUX 3 Image Klein** (15. októbra 2026) – menší model  
    s **otvorenými váhami** (5,6 miliardy parametrov), ktorý sa dá spustiť  
    aj na hernej grafickej karte s 8 GB pamäte.  

| Model na OpenRouteri | Identifikátor | Cena od |
| :--- | :--- | ---: |
| FLUX 3 Image | `black-forest-labs/flux-3-image` | 0,041 $ / obrázok |
| FLUX 3 Image Klein | `black-forest-labs/flux-3-image-klein` | 0,008 $ / obrázok |

Ukážky kódu pre všetky tri služby nájdeme na konci kapitoly  
v časti **Príklady v Pythone**.  

## Ako písať prompty pre obrázky  

Dobrý prompt pre obrázok pripomína zadanie pre fotografa alebo  
ilustrátora. Osvedčená štruktúra:  

1.  **Subjekt** – čo je na obrázku: „starší muž opravuje bicykel".  
2.  **Prostredie** – kde: „v malej dielni plnej náradia".  
3.  **Štýl** – „fotografia", „akvarel", „plochá vektorová grafika".  
4.  **Kompozícia** – „detailný záber", „pohľad zhora", „pomer 16:9".  
5.  **Svetlo a nálada** – „teplé popoludňajšie svetlo", „pokojná atmosféra".  
6.  **Text** – presné znenie dáme do úvodzoviek: nápis „OTVORENÉ".  

Pri **úprave** fotografie je rovnako dôležité povedať, čo sa **meniť  
nemá**: „Odstráň nožnice. Svetlo, tiene a ostatné predmety nechaj bez  
zmeny." Bez toho model niekedy „vylepší" aj časti, na ktoré sme  
nechceli siahať.  

Ďalšie tipy:  

*   Upravujme **po krokoch** – jedna zmena v jednej správe.  
*   Ak výsledok nesedí, je lepšie prompt spresniť než donekonečna  
    generovať nové pokusy.  
*   Pri sérii obrázkov (napr. postava v komikse) posielajme vždy tie  
    isté **referenčné obrázky**.  
*   Modely stále robia chyby v **rukách, počtoch predmetov a dlhších  
    textoch** – výsledok vždy skontrolujme.  

## Etika, právo a bezpečnosť  

*   **Označovanie AI obsahu:** Google vkladá do obrázkov vodoznak  
    **SynthID**, OpenAI pridáva metadáta **C2PA** o pôvode obrázka.  
    Metadáta sa však dajú ľahko odstrániť, preto nie sú zárukou.  
*   **Deepfakes:** Realistické úpravy fotografií skutočných ľudí môžu  
    poškodiť ich povesť alebo slúžiť na podvody. Európsky **AI Act**  
    vyžaduje, aby bol umelo vytvorený alebo zmanipulovaný obsah  
    (tzv. deepfake) zreteľne označený.  
*   **Súkromie:** Fotografie iných ľudí (najmä detí) nenahrávajme  
    do AI nástrojov bez ich súhlasu.  
*   **Autorské práva:** Napodobňovanie štýlu konkrétneho žijúceho  
    umelca alebo chránených postáv je právne aj eticky sporné.  
    Pri komerčnom použití si overme licenčné podmienky služby.  
*   **Pravdivosť:** AI obrázok nie je dôkaz. Pri fotografiách  
    zo správ a sociálnych sietí je dnes potrebná zvýšená opatrnosť.  

## Zhrnutie kapitoly  

*   Dnešné obrázkové modely sú súčasťou **jazykových modelov** – rozumejú  
    bežným vetám, upravujú fotky a píšu čitateľný text.  
*   **Nano Banana 2** je k dispozícii **zadarmo v aplikácii Gemini**;  
    v API je aktuálny **Nano Banana 2.1**.  
*   OpenAI ponúka **GPT Image 2.5** v dvoch modeloch: **Flare** na  
    rýchle bežné generovanie a **Sunburst** na presné úpravy. Pre  
    opakovateľné výsledky používame **datované verzie**.  
*   Cez **OpenRouter** máme jedným kľúčom prístup k modelom viacerých  
    tvorcov, napríklad k **FLUX 3** od európskej firmy Black Forest Labs.  
*   Dobrý prompt opisuje subjekt, prostredie, štýl, kompozíciu a svetlo;  
    pri úpravách aj to, čo sa **meniť nemá**.  
*   Pri práci s obrázkami myslíme na **označovanie AI obsahu**,  
    súkromie a autorské práva.  

## Otázky a diskusia  

1.  Čím sa líšia prvé generátory obrázkov od dnešných modelov ako  
    Nano Banana či GPT Image?  
2.  Prečo OpenAI vydala dva modely (Flare a Sunburst) namiesto jedného  
    s nastavením kvality? Kedy by ste použili ktorý?  
3.  Prečo je pre kurz alebo aplikáciu lepšie použiť datovanú verziu  
    modelu než alias ako `chatgpt-image-latest`?  
4.  Aký význam má, že FLUX 3 Image Klein má otvorené váhy?  
5.  Stačia vodoznaky ako SynthID na rozpoznanie AI obrázkov? Aké majú  
    obmedzenia?  
6.  **Praktická úloha:** V bezplatnej aplikácii Gemini odfoťte svoj stôl  
    a nechajte z fotky odstrániť jeden predmet. Potom vymeňte pozadie.  
    Čo model zachoval a čo nechtiac zmenil?  
7.  **Praktická úloha:** Vytvorte plagát na vymyslené podujatie  
    so slovenským textom v ChatGPT aj v Gemini. Porovnajte, ako si  
    modely poradili s diakritikou.  
8.  **Praktická úloha:** Pomocou kódu z časti Príklady v Pythone pošlite  
    rovnaký prompt trom modelom na OpenRouteri. Porovnajte kvalitu,  
    rýchlosť a cenu (pole `usage` v odpovedi).  

## Príklady v Pythone  

Všetky tri služby môžeme používať aj programovo. Každá odpoveď  
obsahuje obrázok zakódovaný v **base64** – textovom formáte, ktorý  
pred uložením do súboru prevedieme späť na bajty.  

### Gemini API – Nano Banana  

Kľúč ku **Gemini API** získame v Google AI Studio. Upozornenie: API  
**nemá bezplatnú úroveň** pre obrázkové modely – Nano Banana 2.1 stojí  
približne **0,034 $** za obrázok v rozlíšení 1K.  

```bash
pip install google-genai
export GEMINI_API_KEY="..."
```

```python
import base64
from google import genai

client = genai.Client()

interaction = client.interactions.create(
    model="gemini-nano-banana-2.1",
    input="Akvarelová ilustrácia Bratislavského hradu pri západe slnka, "
          "v popredí Dunaj s loďkou",
    response_format={
        "type": "image",
        "aspect_ratio": "16:9",
        "image_size": "2K",
    },
)

with open("hrad.png", "wb") as f:
    f.write(base64.b64decode(interaction.output_image.data))
```

Pri úprave fotografie pošleme okrem textu aj obrázok zakódovaný  
v base64:  

```python
with open("stol.png", "rb") as f:
    image_bytes = f.read()

interaction = client.interactions.create(
    model="gemini-nano-banana-2.1",
    input=[
        {"type": "text", "text": "Odstráň zo stola nožnice. Všetko ostatné "
                                 "nechaj presne tak, ako je."},
        {
            "type": "image",
            "data": base64.b64encode(image_bytes).decode("utf-8"),
            "mime_type": "image/png",
        },
    ],
)

with open("stol-bez-noznic.png", "wb") as f:
    f.write(base64.b64decode(interaction.output_image.data))
```
### OpenAI API – GPT Image  

Používame knižnicu `openai`, ktorú poznáme z predchádzajúcich kapitol.  

```python
import base64
from openai import OpenAI

client = OpenAI()

result = client.images.generate(
    model="gpt-image-2.5-flare-2026-09-08",
    prompt="Plagát na školský deň otvorených dverí, nápis "
           "\"Deň otvorených dverí 2026\", moderný plochý dizajn",
    size="1024x1536",
    quality="medium",
)

with open("plagat.png", "wb") as f:
    f.write(base64.b64decode(result.data[0].b64_json))
```

Na úpravu existujúcej fotografie slúži metóda `images.edit`:  

```python
result = client.images.edit(
    model="gpt-image-2.5-sunburst-2026-09-08",
    image=[open("stol.png", "rb")],
    prompt="Odstráň zo stola nožnice. Všetko ostatné nechaj bez zmeny.",
    quality="high",
)

with open("stol-bez-noznic.png", "wb") as f:
    f.write(base64.b64decode(result.data[0].b64_json))
```

Parameter `size` prijíma aj vlastné rozmery (strany musia byť násobkom  
16, najviac 3840 pixelov). Zložité zadania môžu trvať aj dve minúty.  
### OpenRouter – FLUX 3  

Pre obrázky má OpenRouter samostatný endpoint `/api/v1/images`.  
Odpoveď obsahuje obrázky zakódované v base64.  

```python
import base64
import os
import requests

response = requests.post(
    "https://openrouter.ai/api/v1/images",
    headers={"Authorization": f"Bearer {os.environ['OPENROUTER_API_KEY']}"},
    json={
        "model": "black-forest-labs/flux-3-image",
        "prompt": "Útulná kaviareň v starom meste, ranné svetlo, "
                  "fotorealistický štýl",
        "aspect_ratio": "16:9",
        "resolution": "1K",
    },
)
response.raise_for_status()
result = response.json()

for i, image in enumerate(result["data"]):
    ext = image.get("media_type", "image/png").split("/")[1]
    with open(f"kaviaren-{i}.{ext}", "wb") as f:
        f.write(base64.b64decode(image["b64_json"]))

print(result.get("usage"))  # spotreba a cena
```

Referenčné obrázky na úpravu pošleme v poli `input_references` – ako  
webovú adresu alebo ako base64 *data URL*:  

```python
with open("stol.png", "rb") as f:
    data_url = "data:image/png;base64," + base64.b64encode(f.read()).decode()

payload = {
    "model": "black-forest-labs/flux-3-image",
    "prompt": "Vymeň pozadie za drevenú dielňu, stôl a predmety nemeň.",
    "input_references": [
        {"type": "image_url", "image_url": {"url": data_url}},
    ],
}
```

### Porovnanie modelov  

Podobne ako pri textových modeloch, aj tu môžeme ten istý prompt poslať  
viacerým modelom a výsledky porovnať vedľa seba. Zoznam všetkých  
dostupných obrázkových modelov vráti požiadavka  
`GET https://openrouter.ai/api/v1/images/models`.  

```python
models = [
    "black-forest-labs/flux-3-image",
    "black-forest-labs/flux-3-image-klein",
    "openai/gpt-image-2.5-flare",
]

prompt = "Logo pre školský robotický krúžok, jednoduché, dve farby"

for model in models:
    response = requests.post(
        "https://openrouter.ai/api/v1/images",
        headers={"Authorization": f"Bearer {os.environ['OPENROUTER_API_KEY']}"},
        json={"model": model, "prompt": prompt},
    )
    response.raise_for_status()
    image = response.json()["data"][0]
    name = model.split("/")[1]
    with open(f"logo-{name}.png", "wb") as f:
        f.write(base64.b64decode(image["b64_json"]))
```

Pred spustením je dobré skontrolovať na openrouter.ai, či je daný model  
práve dostupný a pod akým identifikátorom.  

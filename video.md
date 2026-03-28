# Kapitola: Generovanie videa pomocou umelej inteligencie


## 1. Úvod: Čo je to generatívne video?

**Generatívne video** je technologický odbor, ktorý využíva neurónové siete
na vytváranie pohybujúcich sa obrazových sekvencií z textu, obrázkov alebo
iných vstupných dát. Na rozdiel od tradičnej animácie, ktorá vyžaduje
manuálnu prácu animátorov, AI video generuje obsah automaticky.

Táto technológia rýchlo napreduje a mení mediálny priemysel.

*   **Text-to-Video (T2V)** – Generovanie videa na základe textového popisu.
*   **Image-to-Video (I2V)** – Animácia statického obrázku do pohybu.
*   **Video-to-Video (V2V)** – Štylizácia alebo úprava existujúceho videa.

> **Príklad z praxe:**
> *Tradičná tvorba:* Tím animátorov pracuje týždne na 10-sekundovej scéne.
> *AI generovanie:* Používateľ zadá prompt "drak letiaci nad horami" → systém
> vygeneruje niekoľko variantov videa v priebehu niekoľkých minút.

Generatívne video predstavuje prechod od **nástrojov na editáciu** k
**nástrojom na syntézu** celých scén od nuly.

> **Dôležitá poznámka (Marec 2026):** OpenAI oficiálne ukončilo službu Sora
> dňa 24. marca 2026. Táto kapitola reflektuje aktuálny stav trhu.


## 2. Ako technicky funguje generovanie videa?

Architektúra modelov pre generovanie videa je komplexná a vyžaduje veľký
výpočtový výkon. Zvyčajne kombinuje niekoľko kľúčových komponentov.

### 2.1 Fázy generovania videa

```
1. KÓDOVANIE VSTUPU
   ↓
   • Textový prompt sa prevedie na textové embedingy
   • Obrázok sa zakóduje do latentného priestoru (VAE Encoder)

2. ČASOVÁ MODELÁCIA
   ↓
   • Model predpovedá zmeny medzi jednotlivými snímkami (framami)
   • Zachováva konzistenciu objektov v čase (temporal consistency)

3. DENÓIZING (ODŠUMOVANIE)
   ↓
   • Difúzne modely postupne odstraňujú šum z náhodného tensora
   • Proces prebieha v latentnom priestore pre úsporu výkonu

4. DEKÓDOVANIE VÝSTUPU
   ↓
   • VAE Decoder prevedie latentné dáta späť na pixely
   • Výsledkom je hotové video v formáte MP4 alebo podobnom
```

### 2.2 Kľúčové technológie

| Technológia | Úloha vo Video AI |
|-------------|-------------------|
| **Diffusion Models** | Generujú video postupným odstraňovaním šumu z náhodného signálu |
| **Transformers (DiT)** | Spracovávajú priestorové a časové závislosti v dátach |
| **VAE (Variational Autoencoder)** | Komprimuje video do latentného priestoru a späť |
| **Temporal Attention** | Ensuruje, že objekty sa nemenia náhodne medzi snímkami |
| **Motion Buckets** | Parametre riadiace množstvo pohybu v generovanom videu |

---

## 3. Typy generovania videa

| Kritérium | Text-to-Video | Image-to-Video | Video-to-Video |
|-----------|---------------|----------------|----------------|
| **Vstup** | Textový popis (prompt) | Statický obrázok + prompt | Existujúce video + prompt |
| **Kontrola** | Nízka (náhodná kompozícia) | Stredná (zachováva subjekt) | Vysoká (zachováva štruktúru) |
| **Použitie** | Kreatívne koncepty, B-roll | Animácia logiem, fotiek | Štylizácia, filter, upscale |
| **Náročnosť** | Veľmi vysoká | Vysoká | Stredná |
| **Konzistencia** | Často kolíše medzi snímkami | Lepšia na začiatku videa | Najlepšia celková konzistencia |

> **Dôležité:** Image-to-Video je momentálne stabilnejšie ako Text-to-Video,
> pretože model má pevný vizuálny anchor (vstupný obrázok).

---

## 4. Architektúra modelov: Srdce video AI

**Diffusion Transformers (DiT)** sú aktuálne dominantnou architektúrou.
Nahrádzajú staršie U-Net modely používané v prvých generáciách Stable Diffusion.

### 4.1 Prečo sú DiT dôležité?

Tradičné konvolučné siete (CNN) majú obmedzenia pri modelovaní dlhých
časových sekvencií. Transformery lepšie chápu globálny kontext videa.

DiT architektúra rieši tieto výzvy:
*   **Škálovateľnosť** – ľahšie sa trénujú na veľkých dátových sadách.
*   **Flexibilita** – umožňujú lepšie podmienkovanie (conditioning) textom.
*   **Kvalita** – produkujú ostrejšie detaily a plynulejší pohyb.

### 4.2 Schéma Video Pipeline

```
[Text Prompt]      [Reference Image]
      ↓                   ↓
[Text Encoder]     [Image Encoder (VAE)]
      ↓                   ↓
[Combined Latent Representation]
      ↓
[Diffusion Transformer (Time + Space Attention)]
      ↓
[Latent Video Frames]
      ↓
[Video Decoder (VAE)]
      ↓
[Final MP4 Output]
```

### 4.3 Výhody moderných architektúr

-   **Vyššie rozlíšenie** – modely zvládajú 1080p a viac
-   **Dlhšia durácia** – od 5 sekúnd až po niekoľko minút
-   **Fyzikálna konzistencia** – lepšie chápanie gravitácie a svetla
-   **Zníženie artefaktov** – menej "blikania" a deformácií objektov

### 4.4 Výzvy pri implementácii

-   **Výpočtová náročnosť** – tréning vyžaduje tisíce GPU hodín
-   **Temporal Flickering** – objekty môžu meniť tvar medzi snímkami
-   **Text rendering** – AI stále zápasí s generovaním čitateľného textu vo videu
-   **Logika pohybu** – fyzikálne nesprávne interakcie objektov

---

## 5. Prehľad súčasných SOTA modelov (Marec 2026)

Na trhu existuje niekoľko kľúčových hráčov, ktorí definujú stav techniky.
Nasledujúca tabuľka reflektuje aktuálny stav k marcu 2026.

| Model | Vývojár | Max Dĺžka | Rozlíšenie | Prístup | Špeciálne Funkcie |
|---|---|---|---|---|---|
| Kling 3.0 | Kuaishou | 3 min | 1080p | Public | Motion Capture, Lip-Sync |
| Runway Gen-4.5 | Runway ML | 10s | 4K | Paid | Consistent Worlds |
| Google Veo 3.1 | Google | 1 min | 4K (upscale) | Waitlist | Native Audio, Vertical |
| Luma Dream Machine | Luma AI | 5s | 4K (upscale) | Public | Batch Processing |
| Seedance 2.0 | ByteDance | 30s | 1080p | Public | Character Consistency |
| Minimax 2.3 | Minimax | 1 min | 1080p | Public | Audio Sync |
| Haiper 2.0 | Haiper AI | 10s | 1080p | Freemium | Real-time Preview |

> **Poznámka:** OpenAI Sora bola oficiálne ukončená 24. marca 2026.
> Parametre sa rýchlo menia – vždy si overte aktuálnu dokumentáciu.

### 5.1 Detailný prehľad vedúcich modelov

**Kling 3.0 (Kuaishou)**
Aktuálne jeden z najpokročilejších modelov na trhu. Ponúka až 3-minútové
videá s natívnym audio generovaním a synchronizáciou pier. Verzia 3.0 bola
vydaná 31. januára 2026 s vylepšenou kontrolou pohybu.

**Runway Gen-4.5 (Runway ML)**
Profesionálny nástroj s funkciami ako "Consistent World Environments".
Model si pamätá štýl, osvetlenie a geometriu medzi scénami. Podporuje 4K
export pre Pro tier používateľov.

**Google Veo 3.1 (Google DeepMind)**
Najnovšia verzia z januára 2026 ponúka natívne audio generovanie, vertikálne
video (9:16) a multi-reference image mode. Rozlíšenie 720p s možnosťou 4K
upscale pre produkčné workflow.

**Luma Dream Machine (Luma AI)**
Stále populárny pre batch processing a rýchle generovanie. Januárová 2026
aktualizácia pridala video-to-video editáciu a 4K upscale.

---

## 5.2 Ako vznikajú dlhé AI videá (3+ minút)?

Väčšina "dlhých" AI videí na YouTube nie je výsledkom jedného generovania.
Používajú sa tieto techniky:

### A) Video Extend (Postupné predlžovanie)

Modely ako Kling AI umožňujú **predlžovať videá** pomocou funkcie "Extend":

```
Generácia 1 (5s) → Extend → Generácia 2 (5s) → Extend → Generácia 3 (5s)...
```

Výsledok: Plynulo prepojené video až do 3 minút.

> **Poznámka:** Single generation je limitovaná na 5-10 sekúnd.
> Extend feature je dostupná na platených plánoch.

### B) Stitching (Spájanie klipov)

Tvorcovia generujú viacero kratších klipov a tie následne spájajú:

**Nástroje na stitching:**
-   Kapwing AI Video Stitcher
-   Vidio.ai Multi-clip stitching
-   Tradičné editory (Premiere, DaVinci) s AI klipmi

### C) Hybridný prístup

Najčastejšia metóda pre dlhé formáty:

| Segment | Metóda |
|---------|--------|
| Úvod | AI generované video |
| Hlavná časť | AI klipy + tradičná editácia |
| Prechody | AI generované transition efekty |
| Záver | AI alebo tradičné zábery |

> **Príklad:** 10-minútové AI video = približne 60-120 samostatných generovaní
> spojených v editore s prechodmi a audio stopou.

### Porovnanie: Single vs. Extended

| Parameter | Single Gen | Extended/Stitched |
|-----------|------------|-------------------|
| **Dĺžka** | 5-60 sekúnd | 3+ minút (teoreticky neobmedzené) |
| **Konzistencia** | Vysoká | Klesá s dĺžkou (character drift) |
| **Čas tvorby** | 2-10 minút | Hodiny až dni |
| **Cena** | 1 kredit | 10-100+ kreditov |
| **Kvalita** | Stabilná | Závisí od editácie |

---

## 6. Praktické použitie generatívneho videa

### Kedy použiť AI Video?

| Scenár | Prečo AI Video? |
|--------|-------------------|
| **Reklama a Marketing** | Rýchla tvorba variantov kampaní bez drahého natáčania |
| **Storyboarding** | Vizualizácia scén pred samotným filmovaním |
| **Vzdelávanie** | Tvorba ilustračných videí k nudným témam |
| **Sociálne siete** | Generovanie virálneho obsahu vo veľkom objeme |
| **Prototypovanie** | Testovanie vizuálneho štýlu hry alebo filmu |

### Kedy stačí tradičná tvorba?

-   Vyžaduje sa presný herecký výkon a emócie
-   Potrebujete špecifickú brand identitu a konzistenciu
-   Právne dôvody vyžadujú plné autorské práva na každý záber
-   Komplexné akčné scény s presnou choreografiou

---

## 7. Etické aspekty a limity Video AI

### 7.1 Riziká a obmedzenia

**Deepfakes a dezinformácie**
Možnosť vytvoriť realistické videá politikov alebo celebrít hovoriacich
veci, ktoré nikdy nepovedali. Hrozba pre demokraciu a reputáciu.

**Autorské práva**
Nejasnosť, kto vlastní vygenerované video. Tréningové dáta často obsahujú
diela chránené autorským právom bez súhlasu autorov.

**Bias v dátach**
Modely môžu stereotypne zobrazovať určité etniká alebo povolania.

**Vplyv na trh práce**
Ohrozenie profesií ako animátori, strihači a VFX umelci.

### 7.2 Best practices pre používateľov

-   **Označujte AI obsah** – používajte watermarky alebo metadata
-   **Overujte zdroje** – nenechajte sa oklamať realistickým výstupom
-   **Rešpektujte práva** – nepoužívajte tváre ľudí bez súhlasu
-   **Kontrolujte fakty** – AI môže generovať vizuálne presné, ale fakticky
    nesprávne informácie (napr. historické oblečenie v nesprávnej ére)

---

## 8. Budúcnosť technológií generovania videa

### Trendy vo vývoji:

1.  **Dlhšia konzistencia**
    Modely budú schopné generovať celé scény s rovnakými postavami a
    prostredím bez driftu (zmeny vzhľadu v čase).

2.  **3D a Interaktivita**
    Generovanie nielen 2D videa, ale 3D assetov použiteľných v hrách.

3.  **Real-time Generovanie**
    Video sa bude generovať live počas streamovania alebo v hrách.

4.  **Audio-Video Synchronizácia**
    Perfektné lip-sync a generovanie zvuku priamo spolu s obrazom.

5.  **Personalizácia**
    Modely naučené na štýl konkrétneho umelca alebo brandu.

> **Predikcia:** Do 3 rokov bude kvalita AI videa nerozoznateľná od reality
> pre bežného diváka. Dôraz sa presunie na kontrolu a režisérske nástroje.

---

## 9. Cvičenie pre študentov: Tvorba AI videa

### Laboratórna úloha: "Vizuálny príbeh bez kamery"

**Cieľ:** Vytvoriť krátky príbeh pomocou AI video nástrojov.

**Postup:**

1.  **Napíšte scenár** (max 5 viet), ktorý opisuje jednoduchú dejovú líniu.
    Napr.: "Robot nachádza kvetinu v púšti a stará sa o ňu."

2.  **Vyberte nástroj**
    -   Použite dostupný model (Kling 3.0, Luma, Runway Gen-4.5).
    -   *Poznámka: Sora už nie je dostupná od marca 2026.*

3.  **Generovanie**
    -   Vytvorte aspoň 3 rôzne zábery (široký záber, detail, pohyb).
    -   Skúste použiť Image-to-Video pre zachovanie konzistencie robota.
    -   Pre dlhšie video použite Extend alebo Stitching techniku.

4.  **Analýza**
    -   Kde sa objavili artefakty?
    -   Ako sa správala fyzika (svetlo, tieň, pohyb)?
    -   Koľko iterácií bolo potrebných na získateľný výsledok?
    -   Aké boli výzvy pri spájaní klipov?

5.  **Výstup**
    -   Krátke video (max 30s) + report o skúsenostiach (1 strana).

**Diskusia:**
-   Aké boli najväčšie limity nástroja?
-   Ako by ste vylepšili workflow pre profesionálne použitie?
-   Kedy je vhodné použiť stitching vs. single generation?

---

## 10. Záver

Generovanie videa pomocou umelej inteligencie je jednou z najvplyvnejších
technológií súčasnosti. Nie je to len o zábave – mení spôsob, akým
komunikujeme, učíme sa a tvoríme obsah.

Pre študentov AI je dôležité pochopiť, že:
-   Video AI je založené na difúznych modeloch a transformeroch.
-   Konzistencia a fyzikálna správnosť sú hlavné výzvy.
-   Dlhé videá vyžadujú stitching a ľudskú editáciu.
-   Etické používanie je kritické pre budúcnosť technológie.

> **Kľúčová myšlienka:** AI nenahrádza kreatívneho človeka, ale stáva sa
> jeho najmocnejším štetcom. Budúcnosť patrí tým, ktorí sa naučia s týmto
> nástrojom spolupracovať, nie proti nemu bojovať.


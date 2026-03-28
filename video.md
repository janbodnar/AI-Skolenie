Tu je kompletne prepísaná a aktualizovaná kapitola pre **marec 2026**. Text reflektuje najnovšie posuny v architektúre (prechod k World Models) a zmeny na trhu, vrátane integrácie modelu Sora do ekosystému GPT-5.

---

# Generovanie videa pomocou umelej inteligencie

## 1. Úvod: Čo je to generatívne video?

**Generatívne video** je technologický odbor na prieniku počítačového videnia a hlbokého učenia, ktorý využíva neurónové siete na syntézu pohyblivých obrazových sekvencií. Na rozdiel od tradičnej CGI animácie, AI video nevytvára scény pomocou polygonálnych modelov, ale predpovedá vizuálne dáta na úrovni pixelov alebo latentných reprezentácií.

V roku 2026 už nehovoríme len o "generátoroch klipov", ale o **General World Models** – systémoch, ktoré rozumejú základným fyzikálnym zákonom (gravitácia, odrazy svetla, kolízie).

* **Text-to-Video (T2V)** – Syntéza videa z textového popisu.
* **Image-to-Video (I2V)** – Oživenie statického vizuálu (momentálne najstabilnejšia metóda).
* **Video-to-Video (V2V)** – Kompletný re-styling alebo zmena subjektov v existujúcom videu.

> **Aktualizácia (Marec 2026):** > K 24. marcu 2026 OpenAI oficiálne uzavrela éru "samostatnej" aplikácie Sora. Táto technológia bola plne pohltená multimodálnym jadrom **GPT-5**. Generovanie videa je teraz natívnou súčasťou konverzácie, rovnako ako text alebo hlas.

---

## 2. Ako technicky funguje generovanie videa?

Moderné modely (2025/2026) opustili staršie architektúry typu U-Net a prešli na kombináciu difúzie a transformerov.

### 2.1 Fázy generovania (Pipeline 2026)

```
1. TOKENIZÁCIA A KÓDOVANIE
   ↓
   • Vstup (text/obraz) sa rozloží na časovo-priestorové "patche" (tokeny).

2. LATENTNÝ DIFFUSION TRANSFORMER (DiT)
   ↓
   • Transformer spracováva vzťahy medzi pixelmi v priestore aj čase súčasne.
   • Model predpovedá nasledujúce snímky s ohľadom na kauzalitu (príčina -> následok).

3. NATIVE AUDIO GENERATION
   ↓
   • Súčasne s obrazom sa v latentnom priestore generuje synchrónna zvuková stopa.

4. DEKÓDOVANIE (VAE 2.0)
   ↓
   • Prevod z matematických dát do 4K rozlíšenia s HDR metadátami.
```

### 2.2 Kľúčové technológie

| Technológia | Úloha v roku 2026 |
|-------------|-------------------|
| **Diffusion Transformers (DiT)** | Škálovateľné jadro pre vysokú kvalitu a dlhé sekvencie. |
| **Autoregressive Modeling** | Umožňuje logickú nadväznosť scén (napr. postava otvorí dvere a za nimi je stabilná miestnosť). |
| **Latent Keyframe Guidance** | Používateľ určí kľúčové snímky a AI plynule dopočíta pohyb medzi nimi. |
| **World Models** | Schopnosť AI simulovať fyziku (voda tečie dolu kopcom, sklo sa pri náraze rozbije). |

---

## 3. Typy generovania a úroveň kontroly

| Metóda | Vstup | Úroveň kontroly | Hlavná výhoda (2026) |
|-----------|---------------|----------------|----------------|
| **Text-to-Video** | Prompt | Stredná | Úplná kreatívna sloboda. |
| **Image-to-Video** | Obrázok + Prompt | Vysoká | Dokonalá konzistencia postáv a prostredia. |
| **Video-to-Video** | Zdrojové video | Absolútna | Premena hraného filmu na animovaný pri zachovaní pohybu. |
| **Motion Brush 2.0** | Ručné maskovanie | Chirurgická | Možnosť presne určiť, ktorá časť obrazu sa má hýbať a ako. |

---

## 4. Prehľad súčasných SOTA modelov (Marec 2026)

Trh sa stabilizoval a dominujú mu veľké modely s integrovaným zvukom.

| Model | Vývojár | Max. dĺžka (Single Gen) | Rozlíšenie | Kľúčová vlastnosť |
|---|---|---|---|---|
| **Kling 3.0** | Kuaishou | 3 minúty | 4K | Najlepšia fyzika a dlhá kontinuita. |
| **GPT-5 (Sora Engine)** | OpenAI | 1 minúta | 4K | Natívna interaktivita a multimodálny feedback. |
| **Runway Gen-4.5** | Runway ML | 15 sekúnd | 4K | "Director Mode" – úplná kontrola nad kamerou a svetlom. |
| **Google Veo 3.1** | Google | 1 minúta | 4K (native) | Najlepší v spracovaní textu (nápisov) vo vnútri videa. |
| **Luma Dream Machine 2.5** | Luma AI | 10 sekúnd | 4K | Extrémna rýchlosť generovania (pod 60s). |

---

## 5. Tvorba dlhých formátov: Za hranicou jedného klipu

Dnes už netvoríme video po 5-sekundových kúskoch, ktoré sa "lepia" v Premiere Pro. Moderné workflow využívajú inteligentné predlžovanie.

### A) Latent Keyframe Guidance
Namiesto generovania od začiatku do konca definujete: "Tento človek stojí v bode A" a "Tento človek sedí v bode B o minútu neskôr". AI vyplní priestor medzi tým s logickou cestou a pohybom.

### B) Infinite Extend (Kling/Veo)
Funkcia, ktorá berie posledný frame predchádzajúcej generácie a používa ho ako "kotvu" pre ďalších 10-20 sekúnd. Vďaka silnejším transformerom už nedochádza k **Character Driftu** (postava si zachováva tvár aj oblečenie celé minúty).

---

## 6. Etika a právo (Stav 2026)

S masívnym nárastom kvality prišli prísne regulácie:

1.  **C2PA Metadata:** Každé video generované AI povinne obsahuje digitálny podpis v metadátach, ktorý je neodstrániteľný a informuje o pôvode.
2.  **Voice/Face Licensing:** Modely odmietnu generovať známe osobnosti bez autorizačného kľúča (v rámci boja proti deepfakes).
3.  **Copyright:** Väčšina SOTA modelov už prešla na tréning výhradne na licencovaných dátach (napr. Runway s partnermi z Hollywoodu, Google na YouTube dátach so súhlasom tvorcov).

---

## 7. Budúcnosť: Čo nás čaká po roku 2026?

* **Real-time Streaming:** Generovanie videa v reálnom čase pri hraní hier alebo VR (AI ako herný engine).
* **Hmatová odozva:** Integrácia vizuálnych dát so systémami pre haptické obleky.
* **Personalizované filmy:** Film, ktorý sa mení podľa nálady a preferencií diváka počas sledovania.

---

## 8. Cvičenie pre študentov: "Digitálny režisér"

### Laboratórna úloha: Tvorba 60-sekundového naratívneho klipu.

**Postup:**
1.  **Character Sheet:** Vygenerujte v Midjourney (alebo inom modeli) postavu z troch rôznych uhlov.
2.  **I2V Base:** Použite tieto obrázky ako vstup pre **Kling 3.0** alebo **Veo 3.1** na vytvorenie úvodnej scény.
3.  **Extend & Prompting:** Pomocou funkcie *Extend* pridajte ďalšie dve scény, kde postava vykonáva fyzicky náročnú úlohu (napr. nalievanie vody do pohára – test fyzikálneho enginu).
4.  **Audio Sync:** Overte, či generované zvuky prostredia sedia s pohybom postavy.

**Diskusia:**
* V ktorej sekunde začal model strácať detaily tváre?
* Ako si poradil s "prekrytím" (occlusion) – napr. keď postava prešla za strom?
* Bol zvuk generovaný natívne, alebo ste ho museli pridávať externe?

---

## 9. Záver

Generovanie videa v marci 2026 už nie je technologickým trikom, ale **štandardným produkčným nástrojom**. Rozdiel medzi "amatérom" a "profesionálom" už nie je v tom, kto vie napísať lepší prompt, ale kto lepšie rozumie **réžii, svetlu a strihu**. AI dodáva pixely, človek dodáva víziu a emóciu.

> **Kľúčová myšlienka:** V roku 2026 nie je limitom výkon grafickej karty, ale hĺbka vašej predstavivosti.

---
**Môžem vám pomôcť s niečím ďalším? Napríklad s prípravou konkrétnych promptov pre tieto moderné modely?**

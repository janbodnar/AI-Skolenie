# Úvod do umelej inteligencie (AI)

**Umela inteligencia (AI)** je technológia, ktorá umožňuje strojom „myslieť" a „učiť sa" podobne  
ako ľudia. Namiesto toho, aby sme počítačom presne napísali každý krok, AI sa vie učiť z príkladov 
a sama nachádzať riešenia.

> **Jednoducho povedané:** AI je počítačový program, ktorý sa vie učiť z dát a pomáhať nám riešiť úlohy –
> od písania textov až po rozpoznávanie obrázkov.

**Stručná história:**
- **1950s:** Začiatky – Alan Turing položil teoretické základy
- **1970s:** Expertné systémy – počítače riešiace špecifické úlohy
- **1990s:** Strojové učenie – počítače sa učia z dát
- **2010s+:** Hlboké učenie a veľké jazykové modely – dnešná „chytrá" AI

**Hlavné oblasti AI:**
- 🗣️ **Spracovanie jazyka** – pochopenie a tvorba textu
- 👁️ **Počítačové videnie** – rozpoznávanie obrázkov a videí
- 🤖 **Robotika** – autonómne stroje a vozidlá
- 🎯 **Učenie s posilňovaním** – učenie metódou pokus-omyl

---

## Kde sa AI používa? (Príklady z praxe)

| Oblasť | Ako AI pomáha | Príklad nástroja |
|--------|--------------|------------------|
| ✍️ **Písanie** | Generuje nápady, píše texty, koriguje gramatiku | ChatGPT, Claude |
| 🎨 **Obrázky** | Vytvára grafiku z textového popisu | DALL-E, Midjourney |
| 🎵 **Hudba** | Skladá melódie, generuje hudbu na pozadie | Suno, AIVA |
| 🎬 **Video** | Strihá, generuje scény, vytvára efekty | Runway, Pika |
| 💻 **Programovanie** | Navrhuje kód, hľadá chyby, vysvetľuje funkcie | GitHub Copilot |
| 🤖 **Roboty** | Umožňuje autonómne rozhodovanie | Výrobné roboty, drony |

> 💡 **Tip pre školenie:** Ukážte účastníkom konkrétny príklad – napr. vygenerujte obrázok alebo krátky text naživo.

---

## Ako AI „učí"? (Základy bez matematiky)

### Strojové učenie v skratke:
1. **Dáta** → AI dostane veľa príkladov (napr. fotky mačiek a psov)
2. **Tréning** → Hľadá vzory a rozdiely medzi príkladmi
3. **Predikcia** → Po natrénovaní vie nové fotky zaradiť

**Tri hlavné typy učenia:**
- 🟢 **S učiteľom:** Dáta sú označená (napr. „toto je mačka")
- 🔵 **Bez učiteľa:** AI sama hľadá skupiny a vzory v dátach
- 🟡 **S posilňovaním:** AI sa učí metódou pokus-omyl, dostáva „odmeny" za správne rozhodnutia

### Neurónové siete – inšpirácia mozgom:
```
Vstup (dátum) → Skryté vrstvy (spracovanie) → Výstup (výsledok)
```
- Sieť sa skladá z „neurónov" prepojených váhami
- Počas trénovania sa váhy upravujú, aby sieť lepšie predpovedala
- **Hlboké učenie** = veľa vrstiev → schopnosť pochopiť zložité vzory

> 🎯 **Zjednodušená metafora:** Predstavte si neurónovú sieť ako tím špecialistov, kde každý rieši malú časť úlohy a spoločne dospeli k výsledku.

---

## Veľké jazykové modely (LLM) – čo sú zač?

**LLM** (napr. GPT, Gemini, LLaMA) sú AI trénované na miliardách textov z internetu. Vedia:
- ✅ Rozumieť kontextu a odpovedať na otázky
- ✅ Písať e-maily, články, kód
- ✅ Prekladať a zhrňovať texty
- ✅ Vysvetľovať zložité témy jednoducho

**Ako fungujú?**
- Učia sa štatistické vzory: „Aké slovo najčastejšie nasleduje po...?"
- Čím viac parametrov („veľkosť mozgu"), tým lepšie chápu nuansy
- Nevedia „myslieť" ako ľudia – predpovedajú najpravdepodobnejšiu odpoveď

**Prečo nepoužívať vlastný model?**
```
✅ Výhody hotových modelov:
- Okamžité použitie cez API
- Nevyžadujú tisíce GPU a mesiace trénovania
- Dajú sa „doladiť" na konkrétnu úlohu s malým množstvom dát
```

> 💡 **Praktický tip:** Pre väčšinu firemných úloh stačí použiť existujúci model a prispôsobiť ho promptmi alebo malým doladením.

---

## Chatboty – AI ako váš asistent

| Chatbot | Vývojár | Silné stránky |
|---------|---------|---------------|
| **ChatGPT** | OpenAI | Univerzálny, kreatívny, dobrý na vysvetľovanie |
| **Copilot** | Microsoft | Integrácia s Office a vývojovými nástrojmi |
| **Gemini** | Google | Práca s viacerými formátmi (text, obrázok, audio) |
| **DeepSeek** | Čína | Efektívny, dobrý pomer výkon/cena |

**Čo chatboty vedia:**
- Odpovedať na otázky v prirodzenom jazyku
- Pomáhať s brainstormingom a plánovaním
- Vysvetľovať kód alebo technické pojmy
- Pamätať si kontext konverzácie (v rámci relácie)

**Čo (zatiaľ) nevedia:**
- ❌ Nemajú skutočné „vedomie" ani emócie
- ❌ Môžu sa mýliť alebo „vymýšľať" fakty (halucinácie)
- ❌ Nevedia pristupovať k súkromným dátam bez explicitného povolenia

> ⚠️ **Dôležité pre školenie:** Vždy overte kritické informácie z iného zdroja!

---

## Ako písať dobré prompty? (Návod pre začiatočníkov)

**Prompt** = inštrukcia, ktorú dáte AI, aby vygenerovala odpoveď.

### 5 zlatých pravidiel:

1. **Buďte konkrétni**  
   ❌ „Napíš niečo o marketingu."  
   ✅ „Napíš 3 odrážky o výhodách e-mail marketingu pre malé firmy."

2. **Dajte kontext**  
   ✅ „Vysvetli pojem 'neurónová sieť' tak, aby tomu rozumel žiak 5. triedy."

3. **Priraďte rolu**  
   ✅ „Konaj ako skúsený UX dizajnér a navrhni 5 vylepšení pre túto stránku..."

4. **Špecifikujte formát**  
   ✅ „Odpoveď daj vo forme tabuľky s stĺpcami: Výhoda / Príklad / Riziko."

5. **Ukážte príklad (voliteľné)**  
   ✅ „Formátuj odpoveď takto: [Príklad]"

### Šablóna dobrého promptu:
```
[Rola] + [Úloha] + [Kontext] + [Formát] + [Obmedzenia]

Príklad:
"Konaj ako lektor AI školenia. Vysvetli začiatočníkovi, čo je to prompt engineering. 
Použi jednoduché príklady z bežného života. Odpoveď daj v 5 odrážkach, max. 2 vety na odrážku."
```

> 🔄 **Iterácia je kľúč:** Ak prvá odpoveď nie je ideálna, upravte prompt a skúste znova.

---

## Praktické ukážky pre školenie

### 1️⃣ Zhrnutie textu
```
Prompt: "Zhrň tento článok o klimatických zmenách na 3 hlavné body pre manažérov."
Výstup: Stručný prehľad bez technického žargónu.
```
**Využitie:** Rýchle spracovanie dlhých reportov, e-mailov, článkov.

### 2️⃣ Preklad s kontextom
```
Prompt: "Prelož tento technický popis do slovenčiny. Zachovať odborné termíny, 
ale vysvetliť ich v zátvorke pre začiatočníkov."
```
**Výhoda oproti klasickým prekladačom:** AI chápe kontext a vie prispôsobiť štýl.

### 3️⃣ Extrakcia informácií
```
Prompt: "Z tohto životopisu vytiahni: meno, poslednú pozíciu, 3 kľúčové zručnosti. 
Výstup daj ako JSON."
```
**Využitie:** Automatizácia spracovania CV, faktúr, formulárov.

### 4️⃣ Analýza sentimentu
```
Prompt: "Prečítaj tieto 10 recenzií a zhrň: Čo zákazníkom najviac chýba? 
Aké slová sa opakujú v negatívnych hodnoteniach?"
```
**Využitie:** Rýchly prehľad spätnej väzby bez manuálneho čítania.

---

## Bezpečnosť a etika – na čo myslieť

✅ **Dobré praktiky:**
- Overujte fakty z kritických odpovedí AI
- Nezdieľajte citlivé/firemné dáta s verejnými chatbotmi
- Buďte transparentní, ak obsah vytvorila AI
- Rešpektujte autorské práva pri generovaní obrázkov/textov

❌ **Časté chyby začiatočníkov:**
- Slepo dôverovať odpovediam bez kontroly
- Očakávať, že AI „vie všetko" – má medzery v znalostiach
- Používať AI na úlohy vyžadujúce ľudský úsudok bez dohľadu

> 🎓 **Záver školenia:** AI je mocný nástroj, ale ako každý nástroj – vyžaduje pochopenie,
> zodpovednosť a kritické myslenie.

---

## Rýchly slovník pojmov (pre účastníkov)

| Pojem | Vysvetlenie |
|-------|-------------|
| **AI / Umelá inteligencia** | Systémy, ktoré napodobňujú ľudské myslenie |
| **Strojové učenie** | AI, ktorá sa učí z dát namiesto explicitného programovania |
| **LLM** | Veľký jazykový model – AI trénovaná na texte |
| **Prompt** | Inštrukcia pre AI, čo má urobiť |
| **Tréning** | Proces, pri ktorom sa AI učí z príkladov |
| **Parametre** | „Vedomosti" modelu – čím viac, tým komplexnejšie vzory vie zachytiť |
| **Halucinácia** | Keď AI vygeneruje nesprávnu, ale presvedčivo znejúcu odpoveď |

---

> 📌 **Odporúčanie pre lektora:** Po každej teoretickej časti zaradte 5-minútovú praktickú ukážku s účastníkmi (napr. spoločné vytvorenie promptu). Zapojenie zvyšuje zapamätanie si o 70 %.

* Dokument pripravený pre úvodné školenie AI – jazyk prispôsobený začiatočníkom, technické detaily zjednodušené, dôraz na praktické využitie.*

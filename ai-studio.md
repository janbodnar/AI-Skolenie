# Google AI Studio: Tvorba AI aplikácií bez programovania

**Google AI Studio** je bezplatný webový nástroj od Google, ktorý umožňuje pracovať s najnovšími
AI modelmi Gemini priamo v prehliadači – bez nutnosti inštalácie alebo programovania.

> **Jednoducho povedané:** Google AI Studio je „ihrisko" pre umelú inteligenciu, kde si môžete
> vyskúšať tvorbu promptov, testovať rôzne modely, generovať texty a obrázky, a dokonca
> vytvárať jednoduché AI aplikácie – to všetko cez prehľadné webové rozhranie.

### Prečo je AI Studio zaujímavé pre začiatočníkov?

```
✅ Bezplatný prístup k najnovším modelom Gemini
✅ Jednoduché rozhranie – stačí prehliadač a Google účet
✅ Okamžité výsledky – napíšete prompt, vidíte odpoveď
✅ Nevyžaduje programátorské znalosti na základné použitie
✅ Ideálne na experimentovanie a učenie sa práce s AI
```

---

## 🚀 Ako začať s Google AI Studio

### 1. Prihlásenie
```
1. Otvorte: aistudio.google.com
2. Prihláste sa pomocou Google účtu
3. Súhlaste s podmienkami používania
4. Ste pripravení – žiadna ďalšia inštalácia nie je potrebná
```

### 2. Orientácia v rozhraní

| Časť rozhrania | Popis |
|-----------------|-------|
| 📝 **Prompt editor** | Hlavné pole, kde píšete inštrukcie pre AI |
| ⚙️ **Nastavenia modelu** | Výber modelu (Gemini Pro, Flash), teplota, maximálna dĺžka |
| 📁 **Knižnica promptov** | Uložené a zdieľané prompty na opätovné použitie |
| 🔑 **API kľúče** | Správa kľúčov na integráciu AI do vlastných aplikácií |
| 📊 **Výstupný panel** | Zobrazenie vygenerovanej odpovede od AI |

### 3. Výber typu promptu

```
Google AI Studio ponúka tri základné režimy:

🔹 Freeform prompt    – voľný formát, klasická otázka-odpoveď
🔹 Structured prompt  – šablóna s definovaným vstupom a výstupom
🔹 Chat prompt        – konverzačný režim s históriou správ
```

---

## ✨ Hlavné funkcie Google AI Studio

### 🎯 Tvorba a testovanie promptov

Google AI Studio je predovšetkým nástroj na rýchle prototypovanie promptov. Môžete:

- Písať prompty a okamžite vidieť odpovede modelu
- Meniť parametre (teplota, top-p, maximálny počet tokenov) a porovnávať výsledky
- Ukladať úspešné prompty do knižnice na opätovné použitie
- Testovať ten istý prompt na rôznych modeloch Gemini

```
Príklad nastavení modelu:

Teplota:      0.2 → presné, faktické odpovede
              0.9 → kreatívne, variabilné odpovede

Max tokenov:  256 → krátke odpovede (odstavec)
              2048 → dlhšie texty (článok)

Top-P:        0.8 → vyvážený výber slov
              1.0 → maximálna rozmanitosť
```

### 🖼️ Generovanie textu aj obrázkov

```
AI Studio podporuje multimodálne vstupy a výstupy:

📝 Text → Text:    Otázky, zhrnutia, preklady, analýzy
📸 Obrázok → Text: Popis obrázku, extrakcia textu z fotky
📄 Dokument → Text: Analýza PDF dokumentov
🎧 Audio → Text:   Prepis zvukových nahrávok
🎨 Text → Obrázok: Generovanie obrázkov z textového popisu (Imagen)
```

### 🔑 Správa API kľúčov

```
API kľúč je "heslo", ktoré umožňuje vašej aplikácii komunikovať s AI modelom.

Postup získania:
1. V ľavom menu kliknite na "Get API key"
2. Vyberte "Create API key in new project"
3. Skopírujte vygenerovaný kľúč
4. Použite ho vo svojej aplikácii alebo skripte

⚠️ Nikdy nezdieľajte API kľúč verejne (napr. na GitHub)
⚠️ Pre produkčné nasadenie nastavte limity využitia
```

### 🔗 Integrácia do aplikácií

```
Po vytvorení a otestovaní promptu v AI Studio môžete:

1. Kliknúť na "Get code" (</> ikona)
2. Vybrať programovací jazyk:
   • Python
   • JavaScript
   • Kotlin
   • Swift
   • Dart
3. Skopírovať vygenerovaný kód do svojho projektu
4. Nahradiť placeholder API kľúčom

💡 Aj bez programovania môžete zdieľať prompt ako odkaz
```

---

## 🛠️ Praktické príklady použitia

### Príklad 1: Vytvorenie jednoduchého chatu

```
Režim: Chat prompt

Systémová inštrukcia:
"Si priateľský asistent pre zákaznícku podporu e-shopu s oblečením.
Odpovedáš po slovensky, stručne a zdvorilo.
Ak nepoznáš odpoveď, odporuč zákazníkovi kontaktovať info@eshop.sk."

Ukážka konverzácie:

👤 Používateľ: Aké máte veľkosti pre pánske tričká?
🤖 Asistent: Pánske tričká ponúkame vo veľkostiach S, M, L, XL a XXL.
             Ak si nie ste istý veľkosťou, radi vám poradíme –
             stačí nám napísať vaše miery (výška, obvod hrude).

👤 Používateľ: Môžem vrátiť tovar?
🤖 Asistent: Áno, tovar môžete vrátiť do 30 dní od doručenia.
             Tovar musí byť nepoužitý a v pôvodnom balení.
             Formulár na vrátenie nájdete na našom webe v sekcii "Reklamácie".
```

> 💡 **Tip:** Systémová inštrukcia definuje „osobnosť" a pravidlá chatbota.
> Čím presnejšie ju napíšete, tým lepšie bude chatbot fungovať.

### Príklad 2: Generovanie textu podľa šablóny (Structured prompt)

```
Režim: Structured prompt

Vstupné polia:
  Produkt: [názov produktu]
  Cieľová skupina: [typ zákazníka]
  Tón: [formálny / neformálny / hravý]

Výstup: Marketingový popis produktu (3 vety)

──────────────────────────────────────
Príklad 1:
  Produkt: Bezdrôtové slúchadlá ProSound X3
  Cieľová skupina: mladí ľudia 18-30
  Tón: hravý

Výstup:
  "Zabudni na zamotané káble! ProSound X3 ti dajú dokonalý zvuk
  na celý deň – či už si v MHD alebo na párty. Nabíjanie? Raz za
  týždeň ti úplne stačí. 🎶"

──────────────────────────────────────
Príklad 2:
  Produkt: Účtovný softvér FinControl
  Cieľová skupina: malé firmy a živnostníci
  Tón: formálny

Výstup:
  "FinControl je moderné účtovné riešenie navrhnuté pre malé
  firmy a živnostníkov. Automatizuje fakturáciu, sleduje
  cash-flow a zjednodušuje daňové priznania. Vyskúšajte
  30-dňovú bezplatnú verziu."
```

> 🎯 **Výhoda structured promptov:** Vytvoríte šablónu raz a potom ju používate
> opakovane s rôznymi vstupmi – ideálne pre hromadné generovanie obsahu.

### Príklad 3: Analýza dokumentu

```
Režim: Freeform prompt + nahranie súboru

Postup:
1. Kliknite na ikonu 📎 a nahrajte PDF dokument
2. Napíšte prompt:

Prompt:
"Prečítaj tento dokument a odpovedz:
1. Aký je hlavný cieľ dokumentu?
2. Uveď 5 kľúčových bodov v odrážkach.
3. Sú v dokumente nejaké čísla alebo štatistiky? Ak áno, zhrň ich do tabuľky.
4. Navrhni 3 otázky, ktoré by si mohol položiť autor dokumentu."

──────────────────────────────────────
Ďalšie užitočné prompty pre analýzu dokumentov:

🔹 "Porovnaj tento dokument s predchádzajúcim a uveď hlavné rozdiely."
🔹 "Extrahuj všetky dátumy a termíny z dokumentu a zoraď ich chronologicky."
🔹 "Preformuluj tento dokument do jednoduchšieho jazyka pre laikov."
🔹 "Nájdi v dokumente možné riziká alebo problémy."
```

### Príklad 4: Prototypovanie vlastného AI agenta

```
Režim: Chat prompt so systémovou inštrukciou

Systémová inštrukcia:
"Si AI asistent pre HR oddelenie firmy TechSolutions.
Tvoje úlohy:
- Odpovedať na otázky zamestnancov o firemných benefitoch
- Pomôcť s vyplnením dovolenky
- Vysvetliť firemné pravidlá (pracovná doba, home office, dress code)
- Ak sa otázka netýka HR tém, zdvorilo odmietni a odporuč správne oddelenie

Pravidlá:
- Odpovedaj vždy po slovensky
- Buď stručný, ale úplný
- Pri citlivých témach (mzdy, osobné údaje) odkáž na HR manažéra
- Používaj priateľský, ale profesionálny tón"

──────────────────────────────────────
Ukážka konverzácie:

👤 "Koľko dní dovolenky mi zostáva?"
🤖 "Aktuálny stav dovolenky nájdete v systéme SAP HR pod záložkou
   'Moja dovolenka'. Ak potrebujete pomoc s prístupom, kontaktujte
   HR oddelenie na hr@techsolutions.sk."

👤 "Aké máme pravidlá pre home office?"
🤖 "Podľa aktuálnej smernice môžete pracovať z domu až 3 dni v týždni.
   Je potrebné:
   1. Dohodnúť sa s priamym nadriadeným
   2. Zadať home office do kalendára
   3. Byť dostupný počas core hours (9:00 – 15:00)
   Kompletná smernica je na intranete v sekcii 'HR dokumenty'."
```

> 💡 **Tip pre prototypovanie:** Začnite s jednoduchou systémovou inštrukciou
> a postupne ju rozširujte na základe toho, ako agent odpovedá na testovacie otázky.

---

## 🎨 Tipy pre efektívnu prácu s AI Studio

### Dobré praktiky

```
1. Začnite jednoducho
   ❌ Písať dlhý, komplikovaný prompt hneď na začiatku
   ✅ Začať krátkym promptom a postupne ho vylepšovať

2. Experimentujte s nastaveniami
   • Teplota 0.1-0.3 → pre faktické úlohy (analýza, extrakcia dát)
   • Teplota 0.7-1.0 → pre kreatívne úlohy (texty, nápady)

3. Používajte systémové inštrukcie
   • Definujte rolu, pravidlá a formát odpovede
   • Uveďte príklady želaného výstupu

4. Ukladajte si úspešné prompty
   • Funkcia "Save" uloží prompt na opätovné použitie
   • Pomenovávajte prompty zrozumiteľne

5. Testujte na rôznych vstupoch
   • Skúste rovnaký prompt s rôznymi dátami
   • Overte, že funguje aj pre okrajové prípady
```

### ⚠️ Na čo si dať pozor

```
• AI môže generovať nepresné informácie
  → Vždy overte fakty, najmä čísla a citácie

• Bezplatný tier má limity
  → Počet požiadaviek za minútu je obmedzený
  → Pre intenzívne použitie zvážte platený plán

• API kľúče chráňte ako heslá
  → Nikdy ich neukladajte priamo do kódu
  → Neposielajte ich cez nezabezpečené kanály

• Výstupy modelu nie sú deterministické
  → Rovnaký prompt môže dať mierne odlišné odpovede
  → Pre konzistentné výsledky nastavte nízku teplotu

• Citlivé dáta zadávajte opatrne
  → Nepíšte do promptov osobné údaje alebo firemné tajomstvá
  → Preštudujte si podmienky používania služby
```

---

## 📋 Typické pracovné postupy

### Postup 1: Od nápadu k funkčnému promptu

```
1. Definujte cieľ
   → Čo presne chcete, aby AI urobila?

2. Napíšte prvý prompt
   → Jednoducho, priamo, v prirodzenom jazyku

3. Otestujte a vyhodnoťte
   → Je odpoveď to, čo ste chceli?

4. Vylaďte prompt
   → Pridajte kontext, príklady, obmedzenia

5. Upravte parametre modelu
   → Experimentujte s teplotou a dĺžkou odpovede

6. Uložte finálnu verziu
   → Save → pomenujte → zdieľajte s tímom
```

### Postup 2: Od promptu k aplikácii

```
1. Vytvorte a otestujte prompt v AI Studio
2. Kliknite na "Get code" (</> ikona)
3. Vyberte jazyk (Python, JavaScript...)
4. Vygenerujte API kľúč
5. Vložte kód do svojej aplikácie
6. Testujte a iterujte

💡 Tento postup umožňuje aj neprogramátorom vytvoriť základ
   AI funkcionality, ktorú potom vývojár dokončí.
```

---

## 🧭 Rýchly prehľad: Čo môžem v AI Studio robiť?

| Úloha | Ako na to |
|-------|-----------|
| **Položiť otázku AI** | Freeform prompt → napísať otázku → Run |
| **Vytvoriť chatbota** | Chat prompt → napísať systémovú inštrukciu → testovať |
| **Generovať texty hromadne** | Structured prompt → definovať šablónu → meniť vstupy |
| **Analyzovať dokument** | Freeform prompt → nahrať PDF → napísať otázky |
| **Analyzovať obrázok** | Freeform prompt → nahrať obrázok → opýtať sa |
| **Vytvoriť AI agenta** | Chat prompt → podrobná systémová inštrukcia → iterovať |
| **Získať kód pre aplikáciu** | Vytvoriť prompt → Get code → skopírovať |
| **Spravovať API kľúče** | Ľavé menu → Get API key → vytvoriť / spravovať |

---

## 🎓 Záver: Prečo používať Google AI Studio?

```
Google AI Studio je ideálny štartovací bod pre prácu s AI, pretože:

🔹 Je bezplatný – plný prístup k modelom Gemini bez poplatkov
🔹 Je jednoduchý – intuitívne rozhranie, žiadne technické prekážky
🔹 Je praktický – od nápadu k výsledku za pár minút
🔹 Je flexibilný – od jednoduchých otázok po prototypy aplikácií
🔹 Je prepojený – export do kódu, API integrácia, zdieľanie

🎯 Odporúčanie pre lektora:
Začnite live ukážkou:
1. Otvorte AI Studio v prehliadači
2. Napíšte jednoduchý prompt: "Vysvetli, čo je umelá inteligencia, v 3 vetách."
3. Zmeňte teplotu a ukážte rozdiel vo výstupoch
4. Prepnite na Chat prompt a vytvorte mini-chatbota
5. Nechajte účastníkov experimentovať samostatne
```

> 📌 **Praktická úloha pre účastníkov (15 min):**
> 1. Otvorte aistudio.google.com a prihláste sa  
> 2. Vytvorte Freeform prompt: „Napíš 5 tipov pre efektívny home office"  
> 3. Zmeňte teplotu z 0.2 na 0.9 a porovnajte výsledky  
> 4. Prepnite na Chat prompt a vytvorte jednoduchého asistenta pre váš tím  
> 5. Zdieľajte najlepší výsledok so skupinou

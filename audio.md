# Audio modely v umelej inteligencii

Audio AI patrí medzi najrýchlejšie sa meniace oblasti umelej inteligencie. Modely  
dnes dokážu zvuk generovať, prepisovať, syntetizovať aj upravovať. Táto kapitola  
sa sústreďuje na hudobnú generáciu, najmä na **ACE-Step** a **Lyria**, a zároveň  
ukazuje, ako audio modely rozumne porovnávať a používať v praxi.  

> **Aktualizácia:** 20. august 2026
>
> Funkcie, ceny, licencie a dostupnosť online služieb sa menia. Číselné údaje  
> preto treba pred nasadením overiť v oficiálnej dokumentácii poskytovateľa.  
> Označenie „open source“ navyše neznamená automaticky, že sú voľné aj všetky  
> tréningové dáta alebo výstupy.  

## Čo sú audio AI modely?

Audio model je model strojového učenia, ktorý prijíma alebo vytvára zvuk,  
reč, hudbu, prípadne ich textové a obrazové opisy. Najčastejšie sa stretávame  
s týmito úlohami:

| Oblasť | Čo model robí | Typické použitie |
|---|---|---|
| **Text-to-Speech (TTS)** | Prevedie text na hovorenú reč | Audioknihy, dabing, asistenti |
| **Speech-to-Text (STT)** | Prepíše hovorenú reč na text | Titulky, zápis porád, vyhľadávanie |
| **Text-to-Music** | Vytvorí hudbu podľa textového opisu | Demo nahrávky, soundtrack, reklama |
| **Voice cloning** | Vytvorí hlas podobný referenčnej vzorke | Lokalizácia a personalizovaný obsah |
| **Audio editing** | Zmení, vyčistí alebo rozdelí existujúce audio | Odšumenie, remix, izolácia stôp |

Tieto kategórie sa môžu prekrývať. Napríklad hlasový agent používa STT na  
porozumenie používateľovi, jazykový model na vytvorenie odpovede a TTS na jej  
prečítanie.

## Ako vyberať audio model

Pri porovnávaní nestačí pozerať iba na kvalitu ukážok. Posudzujte najmä:

- **Úlohu:** potrebujete reč, hudbu, prepis alebo úpravu nahrávky?  
- **Kontrolu:** podporuje model tempo, text piesne, štruktúru, referenčné audio  
    alebo jednotlivé stopy?  
- **Kvalitu a stabilitu:** počúvajte viac výstupov s rovnakým promptom, nie iba  
    najlepšiu ukážku z webu.  
- **Rýchlosť a cenu:** rozlišujte čas do prvého zvuku od času potrebného na  
    vytvorenie celého súboru.  
- **Licenciu a súkromie:** overte použitie výstupov, spracovanie vstupných dát,  
    uchovávanie nahrávok a podmienky klonovania hlasu.  
- **Prevádzku:** cloudová služba je pohodlná, lokálny model poskytuje väčšiu  
    kontrolu, ale vyžaduje vhodný hardvér a údržbu.  

## ACE-Step

### Charakteristika

**ACE-Step** je model a ekosystém zameraný na generovanie hudby. Je zaujímavý  
predovšetkým tým, že ponúka lokálne použitie a otvorenejší spôsob práce než  
bežné webové hudobné služby. Konkrétne funkcie, modelové varianty a hardvérové  
požiadavky sa môžu líšiť podľa vydania, preto ich treba kontrolovať v repozitári  
a v licenčných súboroch konkrétnej verzie.  

### Typický pracovný tok

```text
Textový opis alebo referenčné audio
                                 |
                                 v
                Plánovanie hudobného obsahu
                                 |
                                 v
             Syntéza a vytvorenie audio stopy
                                 |
                                 v
                Výber, úprava a export výstupu
```

Zjednodušená schéma neopisuje presnú internú architektúru konkrétneho vydania.  
Jej účelom je ukázať rozdiel medzi zadaním, generovaním a následnou produkčnou  
úpravou.

### Praktické použitie

- rýchle hudobné skice a prototypovanie,
- podkladová hudba pre video alebo prezentáciu,
- variácie motívu a experimentovanie so žánrom,
- lokálne spracovanie tam, kde nie je vhodné nahrávať audio do cloudu.

### Pseudokód

Rozhranie sa medzi verziami líši. Nasledujúci príklad preto nie je príkaz,
ktorý možno bez úprav spustiť, ale ilustrácia procesu:

```python
from acestep import ACEStepModel

model = ACEStepModel.load("model-variant")
audio = model.generate(
        prompt="Energetická elektronická hudba, 120 BPM, výrazná basová linka, bez vokálov",
        duration=30,
)
audio.save("output.wav")
```

### Odkazy

- [ACE-Step na Hugging Face](https://huggingface.co/spaces/ACE-Step/ACE-Step)
- [ACE Music](https://acemusic.ai/)
- [ACE-Step 1.5 na GitHub](https://github.com/ace-step/ACE-Step-1.5)

Pred komerčným použitím skontrolujte licenciu **kódu, modelových váh, vstupnej
referencie aj výsledného diela**. Tieto podmienky nemusia byť totožné.

## Lyria

### Charakteristika

**Lyria** je rodina modelov od Google DeepMind pre hudobnú generáciu. Aktuálna  
oficiálna stránka uvádza okrem iného model **Lyria 3.5** a tvorbu skladieb až do  
troch minút. Dostupné funkcie však závisia od konkrétnej verzie a produktu, v  
ktorom je model sprístupnený. Pri hodnotení preto uvádzajte vždy aj rozhranie,  
región a dátum overenia.  

Lyria podporuje rýchle kreatívne skice, experimentovanie s náladou, vokály,  
obrazové zadanie a tvorbu skladieb s nastaviteľnou dĺžkou. Výstup treba pred  
publikovaním vypočuť a prípadne ďalej upraviť v digitálnej audio pracovnej  
stanici (DAW).

### Príklad zadania

```text
Vytvor krátku popovú hudobnú skicu k narodeninovému videu.
Tempo: približne 120 BPM.
Nálada: veselá a optimistická.
Nástroje: klavír, basgitara a akustické bicie.
Vokály: ženský hlas, jednoduchý slovenský refrén.
```

Pri generovaní hudby pomáha uviesť účel, žáner, náladu, tempo, nástroje,  
hlasový charakter, dĺžku a obmedzenia. Zadanie je lepšie formulovať vlastnosťami  
požadovaného výsledku než odkazom na konkrétneho žijúceho interpreta.  

### Bezpečnostné prvky

Poskytovateľ môže používať filtrovanie, pravidlá proti napodobňovaniu hlasov a  
technológie na označovanie syntetického obsahu, napríklad SynthID. Presný rozsah  
ochrany a podmienky použitia si overte v aktuálnej dokumentácii služby. Ochranný  
mechanizmus nenahrádza ľudskú kontrolu práv k vstupom ani výstupom.  

## Orientačné porovnanie kategórií

Nasledujúci prehľad je rozhodovací rámec, nie rebríček kvality. Názvy služieb a  
ich ceny sa menia rýchlejšie než vzdelávací materiál.  
  
| Potreba | Vhodná kategória | Na čo si dať pozor |
|---|---|---|
| Hovorený komentár | TTS | Výslovnosť, emócia, licencia hlasu |
| Prepis rozhovoru | STT | Slovenčina, časové značky, súkromie |
| Hudobná skica | Text-to-Music | Kontrola štruktúry a komerčné práva |
| Hlasový agent | STT + LLM + TTS | Latencia, prerušenie reči, logovanie |
| Úprava nahrávky | Audio editing | Artefakty, formát a zachovanie originálu |

### Kritériá namiesto pevných rebríčkov

Ak potrebujete vybrať konkrétny model, vytvorte malý testovací súbor:  

1. Pripravte tri až päť rovnakých zadaní.  
2. Použite rovnaký formát, jazyk a požadovanú dĺžku.  
3. Zaznamenajte kvalitu, čas, cenu a počet nepoužiteľných výstupov.  
4. Overte licenciu a podmienky spracovania dát.  
5. Výsledky porovnajte s potrebami projektu, nie s marketingovým poradím.  

Číselné údaje, ako latencia, MOS skóre, cena za minútu či minimálna dĺžka  
vzorky pri klonovaní, uvádzajte iba vtedy, keď poznáte metodiku merania,  
verziu modelu a dátum merania. Bez toho môžu vytvárať falošný dojem presnosti.  

## Praktické odporúčania

### Pre vzdelávanie

- Na komentár k videu vyberte TTS podľa výslovnosti, jazyka a možnosti opravy
    výslovnosti.
- Na hudobný podklad použite text-to-music, ale hlasitosť a dĺžku upravte v DAW.
- Pri práci so študentskými alebo osobnými nahrávkami najprv odstráňte citlivé
    údaje a overte, či ich služba môže ukladať alebo používať na zlepšovanie modelu.

### Pre komerčný projekt

Pred publikovaním si odškrtnite:

- licenciu modelu a výstupu,
- súhlas s použitými hlasmi a referenčnými nahrávkami,
- pravidlá pre syntetické označenie obsahu,
- povolenie na použitie hudby, textu a samplov,
- spôsob archivácie promptov a zdrojových súborov.

## Etika a bezpečnosť

1. **Klonovanie hlasu:** používajte iba hlas s preukázateľným súhlasom. Súhlas  
     má pokrývať účel, rozsah, obdobie a odvolanie povolenia.
2. **Autorské práva:** licencia modelu sama osebe nerieši práva k tréningovým  
     dátam, referenčnému audiu ani k textu vloženému do promptu.
3. **Označovanie:** pri publikovaní syntetického hlasu alebo hudby rešpektujte  
     pravidlá platformy a príslušné právne požiadavky.
4. **Súkromie:** do cloudovej služby neposielajte citlivé nahrávky bez právneho  
     a technického posúdenia.
5. **Kontrola výstupu:** overte výslovnosť, skryté artefakty, podobnosť s cudzou  
     tvorbou a vhodnosť pre cieľové publikum.

## Zhrnutie

- Audio AI zahŕňa viac než generovanie hudby: patrí sem TTS, STT, klonovanie  
    hlasu aj úprava nahrávok.
- ACE-Step je zaujímavý pre lokálne a experimentálne hudobné workflowy; presné  
    vlastnosti treba overovať podľa konkrétnej verzie.
- Lyria je vhodná na rýchle kreatívne návrhy; dostupnosť a licenčné podmienky  
    závisia od produktu a regiónu.
- Pri výbere rozhodujú úloha, kvalita, kontrola, cena, súkromie a licencia.
- Pred komerčným použitím overte aktuálne podmienky a všetky použité zdroje.

## Zdroje a dátum overenia

- [ACE-Step na Hugging Face](https://huggingface.co/spaces/ACE-Step/ACE-Step)
- [ACE Music](https://acemusic.ai/)
- [Google DeepMind: Lyria](https://deepmind.google/technologies/lyria/)
- [Google DeepMind: prompt guide pre Lyria](https://deepmind.google/models/lyria/prompt-guide/)

Posledná redakčná aktualizácia: **20. august 2026**. 

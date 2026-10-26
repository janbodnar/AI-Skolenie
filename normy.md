# Normy a regulácie pre umelú inteligenciu  

## Praktický prehľad pre vývojárov a používateľov  

**Stav informácií: 12. október 2026.** Tento text je vzdelávací prehľad,  
nie právne poradenstvo. Povinnosti závisia od krajiny, odvetvia, úlohy  
organizácie (poskytovateľ, nasadzovateľ alebo dodávateľ) a od konkrétneho  
účelu systému. Pri projekte s osobnými, zdravotnými alebo inými citlivými  
údajmi treba zapojiť právnika a odborníka na compliance.  

## Prečo regulácie a normy existujú?  

AI môže spracúvať osobné údaje, ovplyvňovať prístup k práci alebo službám  
a vytvárať bezpečnostné či spoločenské riziká. Zodpovedné riadenie preto  
rieši nielen presnosť modelu, ale celý životný cyklus: návrh, vývoj,  
testovanie, nasadenie, monitorovanie, aktualizácie a vyradenie.  

Najčastejšie riziká:  

- **súkromie a bezpečnosť** – únik údajov, nevhodné použitie dát alebo  
  prompt injection;  
- **diskriminácia** – nerovnaké výsledky pre rôzne skupiny ľudí;  
- **nepresnosť a halucinácie** – presvedčivo formulované, ale nesprávne  
  výstupy;  
- **nedostatočná transparentnosť** – človek nevie, že komunikuje so  
  systémom, alebo nechápe dôvod rozhodnutia;  
- **dezinformácie a podvody** – syntetické médiá, vydávanie sa za inú  
  osobu;  
- **autorské práva a obchodné tajomstvo** – neoprávnené použitie obsahu  
  alebo vloženie dôverných údajov do verejnej služby.  

> **Základná zásada:** Najprv určte účel a riziko, potom vyberte dáta,  
> model, kontrolné mechanizmy a spôsob ľudského dohľadu. Samotný „AI  
> nástroj“ nie je compliance stratégia.  

## Rýchly postup pre AI projekt  

1. **Popíšte účel a hranice použitia.** Čo systém robí, pre koho a čo  
   nesmie robiť?  
2. **Zmapujte roly a jurisdikcie.** Kto je prevádzkovateľ a spracovateľ  
   podľa GDPR, poskytovateľ alebo nasadzovateľ podľa AI Actu a prípadne  
   business associate podľa HIPAA?  
3. **Urobte posúdenie rizík.** Zahrňte súkromie, diskrimináciu,  
   bezpečnosť, presnosť, ľudské práva, dostupnosť a dopad na životné  
   prostredie.  
4. **Zvoľte primerané dáta.** Zdokumentujte pôvod, právny základ, licencie,  
   kvalitu, lehoty uchovávania a pravidlá prístupu.  
5. **Testujte pred nasadením.** Overte presnosť, robustnosť, zaujatosť,  
   úniky osobných údajov, zneužiteľnosť a správanie v hraničných prípadoch.  
6. **Zaveďte dohľad a nápravu.** Uchovávajte relevantné logy, sledujte  
   zmeny výkonu, umožnite eskaláciu na človeka a majte postup pre incidenty.  
7. **Priebežne kontrolujte zmenu rizika.** Nový model, nové dáta alebo  
   nový účel môžu znamenať nové povinnosti.  

## GDPR – ochrana osobných údajov v EÚ  

GDPR sa uplatňuje najmä na organizácie v EHP, ktoré spracúvajú osobné  
údaje, a na organizácie mimo EHP, ak ponúkajú tovar alebo služby ľuďom  
v EÚ alebo sledujú ich správanie. Neznamená to, že každý AI systém  
automaticky potrebuje DPIA alebo že každé použitie vyžaduje súhlas.  

### Čo je pri AI dôležité  

- **Právny základ a účel:** pred spracovaním určte konkrétny účel a vhodný  
  právny základ. Oprávnený záujem vyžaduje zdokumentovaný balančný test.  
- **Minimalizácia:** používajte iba údaje potrebné na daný účel; osobné  
  alebo dôverné údaje neposielajte do verejného modelu bez posúdenia.  
- **Transparentnosť:** informujte ľudí, kto údaje spracúva, prečo, aké  
  kategórie údajov používa, ako dlho ich uchováva a či sa používa  
  automatizované rozhodovanie.  
- **Kvalita a bezpečnosť:** riešte presnosť, prístupové práva, šifrovanie,  
  pseudonymizáciu, testovanie a riadenie dodávateľov.  
- **Uchovávanie:** nastavte primerané lehoty pre vstupy, výstupy, logy  
  a zálohy. Zásada „uchovávať všetko pre prípad“ nie je v súlade  
  s minimalizáciou.  
- **DPIA:** posúdenie vplyvu na ochranu údajov je povinné vtedy, keď  
  spracovanie pravdepodobne povedie k vysokému riziku pre práva a slobody,  
  napríklad pri rozsiahlom spracovaní citlivých údajov alebo pri  
  systematickom monitorovaní.  

### Práva jednotlivcov  

Jednotlivci môžu mať právo na informácie, prístup, opravu, výmaz,  
obmedzenie spracovania, prenosnosť a námietku. Pri výhradne automatizovanom  
rozhodnutí, ktoré má právny alebo podobne významný účinok, platí osobitný  
režim podľa článku 22 GDPR s výnimkami a požiadavkami na primerané záruky.  
Nie je to všeobecné právo „zakázať každú AI“ ani absolútne právo na zdrojový  
kód či úplné vysvetlenie modelu.  

> **Prakticky:** DPIA, záznamy o spracovateľských činnostiach, zmluvy  
> so spracovateľmi, proces vybavovania žiadostí a pravidlá mazania  
> pripravte pred pilotným nasadením, nie až po incidente.  

### Príklad: 1 222 strán o jednom používateľovi  

V roku 2011 požiadal rakúsky študent práva Max Schrems, dnes známy právnik  
a aktivista za ochranu súkromia, Facebook o všetky osobné údaje, ktoré  
o ňom spoločnosť uchovávala. GDPR vtedy ešte neplatilo. Žiadosť sa opierala  
o írske právo založené na smernici 95/46/ES, pretože európske sídlo  
Facebooku bolo v Írsku.  

- Facebook mu poslal CD so súborom PDF, ktorý mal **1 222 strán**.  
- Archív obsahoval správy, fotografie, komentáre, zoznam priateľov,  
  pozvánky, interakcie s inými používateľmi a záznamy o jeho aktivite.  
- Niektoré položky sa týkali obsahu, ktorý Schrems považoval za vymazaný.  

Schrems podal na írsky dozorný úrad sťažnosti a založil iniciatívu  
*Europe versus Facebook*, ktorá upozornila verejnosť na rozsah zberu údajov.  
Neskôr stál aj za rozsudkami Súdneho dvora EÚ C-362/14 (Schrems I, 2015)  
a C-311/18 (Schrems II, 2020). Tie zrušili rámce Safe Harbor a Privacy  
Shield pre prenos osobných údajov do USA.  

**Čo z toho vyplýva dnes:**  

- Podľa článku 15 GDPR môže každý požiadať prevádzkovateľa, napríklad  
  spoločnosť Meta, o prístup k svojim údajom. Prvá kópia je bezplatná.  
  Odpoveď má prísť do jedného mesiaca, pri zložitých žiadostiach možno  
  lehotu predĺžiť najviac o ďalšie dva mesiace.  
- Facebook a Instagram ponúkajú v Centre účtov nástroj na stiahnutie  
  vašich informácií. Je rýchly, ale archív nemusí obsahovať všetko, čo  
  spoločnosť o používateľovi spracúva. Úplnejšiu odpoveď dostanete  
  formálnou žiadosťou podľa článku 15.  
- Rozsah údajov sa líši podľa používateľa. 1 222 strán nie je pravidlo.  
- „Vymazané“ v aplikácii nemusí znamenať okamžite odstránené zo všetkých  
  systémov a záloh. Ak chcete výmaz, uplatnite právo podľa článku 17  
  a jeho splnenie si overte.  

## AI Act – nariadenie EÚ o umelej inteligencii  

AI Act (nariadenie (EÚ) 2024/1689) zavádza prístup založený na riziku.  
Uplatňuje sa podľa úlohy subjektu a použitia systému, nie iba podľa toho,  
či sa produkt marketingovo označuje ako „AI“.  

| Úroveň | Príklady a hlavná povinnosť |
|---|---|
| **Zakázané praktiky** | Škodlivá manipulácia, sociálne skórovanie, necielené zbieranie tvárí na tvorbu databáz rozpoznávania a niektoré formy biometrie či predikcie kriminality sú zakázané; presné podmienky a výnimky treba overiť v nariadení. |
| **Vysoké riziko** | Vybrané systémy v nábore, vzdelávaní, kritickej infraštruktúre, základných službách, migrácii, presadzovaní práva a súdnictve vyžadujú riadenie rizík, kvalitné dáta, technickú dokumentáciu, logovanie, ľudský dohľad, presnosť, robustnosť a kybernetickú bezpečnosť. |
| **Špecifická transparentnosť** | Ľudia majú byť informovaní, keď komunikujú so systémom AI; syntetický obsah a deepfakes musia byť označené podľa pravidiel AI Actu. |
| **Minimálne alebo žiadne riziko** | Väčšina spamových filtrov a herných funkcií nemá podľa AI Actu dodatočné povinnosti, hoci na ne môžu dopadať GDPR, autorské, spotrebiteľské alebo bezpečnostné pravidlá. |

### Nábor a personálne rozhodnutia  

Náborové systémy patria podľa prílohy III AI Actu (oblasť zamestnanosti)  
medzi vysokorizikové. Patria sem najmä systémy na cielenú inzerciu pracovných  
miest, filtrovanie a analýzu prihlášok, hodnotenie kandidátov a rozhodnutia  
ovplyvňujúce podmienky práce, povýšenie, skončenie pomeru alebo prideľovanie  
úloh na základe správania jednotlivca či hodnotenie výkonu.  

Z toho vyplývajú tieto požiadavky:  

- **Ľudský dohľad (článok 14):** osoby poverené dohľadom musia rozumieť  
  výstupom systému, odhaliť anomálie a mať možnosť výstup ignorovať,  
  prepísať alebo zvrátiť a systém zastaviť. Systém preto nesmie byť  
  nastavený tak, že človek len potvrdzuje jeho odporúčanie.  
- **Automatizované rozhodnutia (článok 22 GDPR):** rozhodnutie výhradne  
  na základe automatizovaného spracovania, ktoré má na uchádzača významný  
  účinok, je v zásade zakázané. Výnimky (zmluva, zákon, výslovný súhlas)  
  vyžadujú primerané záruky vrátane práva na ľudský zásah a na vyjadrenie  
  názoru. Súdny dvor EÚ vo veci C-634/21 (SCHUFA) rozhodol, že skóre, ktoré  
  rozhodujúcim spôsobom ovplyvní výsledok, sa môže považovať za automatizované  
  rozhodnutie.  
- **Zákaz rozpoznávania emócií v práci a vzdelávaní (článok 5 AI Actu):**  
  systémy na odvodzovanie emócií z videorozhovorov sú zakázané, okrem  
  výnimiek pre zdravotné alebo bezpečnostné dôvody.  
- **Informovanie zamestnancov:** zamestnávateľ ako nasadzovateľ musí pred  
  zavedením vysokorizikového systému informovať zamestnancov a ich zástupcov.  
- **Dokumentácia a logy:** nasadzovateľ uchováva logy a musí vedieť vysvetliť,  
  na akom základe bol kandidát vyradený.  

Záver: formálne posledné slovo musí mať človek, ktorý má skutočnú možnosť  
a kompetenciu rozhodnutie preskúmať a zmeniť. Výsledok AI nesmie byť jediným  
podkladom pre vyradenie uchádzača.  

### Označovanie AI obsahu (článok 50)  

Cieľom nie je označiť všetko, na čo siahla AI, ale zabrániť tomu, aby  
ľudia považovali za skutočné niečo, čo skutočné nie je. Povinnosti  
sa uplatňujú od 2. augusta 2026.  

- **Poskytovateľ nástroja**, napríklad generátora obrázkov, musí výstupy  
  označiť strojovo čitateľne, napríklad metadátami alebo neviditeľným  
  vodoznakom.  
- **Nasadzovateľ**, teda firma alebo človek, ktorý obsah zverejní, musí  
  **viditeľne** označiť deepfake. Rovnako musí označiť AI texty o veciach  
  verejného záujmu, ktoré nikto redakčne neskontroloval a za ktoré nikto  
  redakčne nezodpovedá.  
- **Deepfake** je obrázok, zvuk alebo video vytvorené či upravené AI, ktoré  
  sa podobá na existujúce osoby, predmety, miesta, udalosti alebo služby  
  a môže pôsobiť ako pravé. Rozhoduje dojem na publikum, nie úmysel autora.  
  Podľa výkladu v článku ITlearning sem patrí aj fotorealistická fiktívna  
  osoba alebo AI avatar.  

| Situácia | Treba označiť? |
|---|---|
| Fotorealistický AI obrázok osoby, produktu alebo služby, napr. montáže klimatizácie | **Áno**, viditeľne |
| AI avatar, ktorý pôsobí ako skutočný človek | **Áno** |
| Skutočná fotka, ktorú AI „prekreslila“ | **Áno**, ide už o AI verziu fotky |
| Skutočná fotka, ku ktorej AI pridala iba text, logo alebo rámček | Nie |
| Bežná úprava expozície, farieb alebo ostrosti | Spravidla nie |
| Vektorový banner, kreslená alebo zjavne fiktívna postava | Nie |
| Zjavne umelecké, satirické alebo fiktívne dielo | Áno, ale stačí zdržanlivé označenie, napr. v titulkoch; výnimka neplatí pre reklamu |
| AI text, ktorý človek prečítal, upravil a redakčne zaň zodpovedá | Spravidla nie |

**Ako označovať:** jasne, zreteľne, viditeľne bez pomôcok a najneskôr  
pri prvom kontakte s obsahom. Osvedčuje sa ikona, napríklad piktogram  
z Kódexu správnej praxe Európskej komisie, doplnená slovným označením.  
Nestačia metadáta, poznámka v obchodných podmienkach, skrytý odkaz ani  
upozornenie na konci videa. Štítok „AI info“ od platformy, napríklad Meta,  
zákonnú povinnosť nenahrádza a nemusí byť viditeľný hneď na začiatku.  

- Obsah zverejnený pred 2. augustom 2026 netreba spätne označovať. Ak ho  
  však použijete znova, autor článku odporúča brať ho ako nový obsah.  
- Nástroje uvedené na trh pred augustom 2026 majú podľa článku na strojové  
  označovanie čas do 2. decembra 2026.  
- Za porušenie povinností podľa článku 50 hrozí pokuta až 15 miliónov eur  
  alebo 3 % celosvetového ročného obratu (článok 99 ods. 4).  
- Usmernenia Komisie k článku 50 z 20. júla 2026 nie sú právne záväzné.  
  Konečný výklad dá Súdny dvor EÚ a prax dozorných orgánov.  

> **Praktický test:** Mohol by si to niekto pomýliť so skutočnou fotkou,  
> videom alebo nahrávkou? Ak áno, označte to viditeľne a hneď na začiatku.  
> Pri pochybnostiach označte.  

### Stav povinností k 12. 10. 2026  

- Nariadenie nadobudlo účinnosť 1. augusta 2024. Zákaz vybraných praktík  
  a požiadavka na AI gramotnosť sa uplatňujú od 2. februára 2025.  
- Pravidlá pre poskytovateľov modelov všeobecného účelu (GPAI) sa uplatňujú  
  od 2. augusta 2025. Zahŕňajú technickú dokumentáciu, politiku autorských  
  práv a pri modeloch so systémovým rizikom aj hodnotenie a zmierňovanie  
  rizík.  
- Od 2. augusta 2026 sa uplatňujú pravidlá pre vysokorizikové systémy  
  uvedené v prílohe III a transparentnostné povinnosti podľa článku 50  
  (informovanie o interakcii so systémom AI, označovanie syntetického obsahu  
  a deepfakes).  
- Vysokorizikové systémy zabudované do produktov regulovaných podľa  
  harmonizačných predpisov EÚ (príloha I) majú podľa pôvodného harmonogramu  
  platiť od 2. augusta 2027. Prebiehajú legislatívne návrhy na úpravu  
  a odklad niektorých termínov; pred uvedením na trh overte aktuálne znenie  
  nariadenia, harmonogram a usmernenia Európskej komisie.  

AI Act nenahrádza GDPR. Jeden projekt môže súčasne podliehať obom predpisom,  
kybernetickým pravidlám, spotrebiteľskému právu a odvetvovým zákonom.  

## HIPAA – zdravotné údaje v USA  

HIPAA nie je všeobecný zákon o všetkých zdravotných aplikáciách. Privacy Rule  
sa vzťahuje najmä na **covered entities** (zdravotné plány, clearinghouses  
a určitých poskytovateľov zdravotnej starostlivosti) a na ich **business  
associates**. To, či AI dodávateľ spadá do tejto kategórie, závisí od jeho  
činnosti a prístupu k PHI; samotný názov produktu nerozhoduje.  

**PHI** sú individuálne identifikovateľné zdravotné informácie, ktoré drží  
alebo prenáša covered entity alebo business associate. Pri de-identifikácii  
existuje metóda safe harbor, ktorá odstraňuje určené identifikátory, a metóda  
expertného posúdenia. Odstránenie mien samo osebe nestačí.  

Pre AI riešenie sú podstatné:  

- zmluva **Business Associate Agreement**, ak ide o business associate;  
- pravidlo minimálne potrebného rozsahu údajov;  
- primerané administratívne, fyzické a technické záruky, riadenie prístupov,  
  autentifikácia, auditné záznamy a postup pri incidente;  
- pravidlá používania údajov na výskum, tréning a sekundárne účely;  
- posúdenie ďalších federálnych a štátnych zákonov, pretože HIPAA nepokrýva  
  všetky zdravotné údaje a štátne pravidlá môžu byť prísnejšie.  

> **Oprava častej nepresnosti:** neuvádzajte jednu pevnú sumu pokuty „za  
> každý typ porušenia“. Civilné sankcie sa menia, majú ročné limity  
> a závisia od okolností; aktuálne sumy treba overiť v pravidlách HHS/OCR.  

## Dátová suverenita  

Dátová suverenita znamená, že nad údajmi má kontrolu ten, komu patria,  
a že sa na ne vzťahuje právo, ktoré si vedome zvolil. Nejde len o to, kde  
ležia disky so serverom. Rozhoduje aj to, kto má k údajom technický  
prístup, ktorý štát môže vyžiadať ich vydanie a či sa dá od dodávateľa  
odísť bez straty údajov.  

| Pojem | Otázka, na ktorú odpovedá | Príklad |
|---|---|---|
| **Rezidencia údajov** | Kde sú údaje fyzicky uložené? | Cloudový región vo Frankfurte. |
| **Dátová suverenita** | Pod právo ktorého štátu údaje spadajú a kto o nich rozhoduje? | Dodávateľ so sídlom v USA môže podliehať americkým zákonom aj pri dátach v EÚ. |
| **Digitálna (technologická) suverenita** | Dokážeme fungovať bez závislosti od jedného dodávateľa alebo štátu? | Vlastná infraštruktúra, otvorené štandardy, plán na prechod k inému poskytovateľovi. |

> **Pozor:** uloženie dát v EÚ ešte neznamená dátovú suverenitu. Rezidencia  
> je len jedna z podmienok.  

### Prečo je to pri AI také dôležité  

- **Prompty sú tiež údaje.** Všetko, čo vložíte do cloudového AI nástroja,  
  vrátane dokumentov, zdrojového kódu či údajov klientov, odchádza  
  k poskytovateľovi. Tam sa môže logovať, uchovávať alebo za určitých  
  podmienok použiť na tréning.  
- **Väčšina veľkých modelov a cloudov pochádza mimo EÚ.** Americký CLOUD  
  Act z roku 2018 umožňuje úradom USA vyžiadať od amerických poskytovateľov  
  údaje, ktoré majú v držbe alebo pod kontrolou, bez ohľadu na to, kde sú  
  uložené. Zástupca Microsoftu vo Francúzsku v júni 2025 pred francúzskym  
  Senátom priznal, že nevie zaručiť, že údaje európskych zákazníkov nebudú  
  na takúto žiadosť vydané.  
- **Prenos údajov do tretích krajín má právne podmienky.** Kapitola V GDPR  
  vyžaduje rozhodnutie o primeranosti, štandardné zmluvné doložky s posúdením  
  vplyvu prenosu alebo inú zákonnú záruku. Rozsudok Schrems II ukázal, že  
  takýto rámec môže padnúť zo dňa na deň. Súčasný rámec EU-US Data Privacy  
  Framework z júla 2023 potvrdil Všeobecný súd v septembri 2025 (vec  
  T-553/23 Latombe), no jeho stabilita závisí od amerických záruk a môže  
  byť opäť napadnutý.  
- **Závislosť od dodávateľa je prevádzkové riziko.** Zmena cien, podmienok  
  alebo modelu, ukončenie služby, sankcie či exportné obmedzenia môžu  
  zastaviť produkt, ktorý je postavený na jednom API.  
- **Model nesie hodnoty a dáta svojho tvorcu.** Pôvod tréningových dát,  
  jazykové pokrytie a nastavenie filtrov ovplyvňujú, ako dobre model slúži  
  slovenským používateľom a inštitúciám.  

### Súvisiace európske predpisy  

- **GDPR, kapitola V** – pravidlá prenosu osobných údajov mimo EHP.  
- **Data Act** (nariadenie (EÚ) 2023/2854), uplatňuje sa od 12. septembra  
  2025 – uľahčuje prechod medzi cloudovými poskytovateľmi, postupne ruší  
  poplatky za odchod a vyžaduje záruky proti nezákonnému prístupu vlád  
  tretích krajín k neosobným údajom.  
- **Data Governance Act** (nariadenie (EÚ) 2022/868) – pravidlá opätovného  
  použitia údajov verejného sektora a dôveryhodného zdieľania údajov.  
- **NIS2 a DORA** – riadenie rizík dodávateľov a koncentračného rizika  
  pri kritických službách vrátane cloudu.  
- **Európsky priestor pre údaje o zdraví** (nariadenie (EÚ) 2025/327) –  
  pravidlá prístupu k zdravotným údajom a ich sekundárneho použitia.  

### Ako postupovať v praxi  

1. **Klasifikujte údaje.** Verejné, interné, dôverné a osobitné kategórie  
   osobných údajov majú mať odlišné pravidlá pre použitie AI.  
2. **Zmapujte celú cestu dát.** Sledujte nielen hlavné úložisko, ale aj  
   subdodávateľov, zálohy, logy, telemetriu a prístup podpory.  
3. **Zvoľte región a overte zmluvu.** Vyžadujte spracovanie v EÚ, zákaz  
   tréningu na vašich údajoch, krátku retenciu a zoznam subdodávateľov.  
4. **Šifrujte a držte si kľúče.** Pri citlivých dátach používajte vlastné  
   kľúče (BYOK, HYOK) uložené mimo kontroly poskytovateľa.  
5. **Zvážte lokálne alebo európske modely.** Modely s otvorenými váhami  
   spustené na vlastnej infraštruktúre alebo u európskeho poskytovateľa  
   dávajú najvyššiu kontrolu, ale vyžadujú vlastnú prevádzku a bezpečnosť.  
6. **Pripravte si únikovú cestu.** Oddeľte aplikáciu od konkrétneho API,  
   používajte otvorené formáty a pravidelne overte export údajov.  

Dátová suverenita má aj svoju cenu: vyššie náklady, viac práce s prevádzkou  
a niekedy slabší model. Cieľom preto nie je mať všetko doma, ale vedome  
rozhodnúť, ktoré údaje a služby musia zostať pod vlastnou kontrolou.  

## Ďalšie relevantné pravidlá a štandardy  

### Právo a verejné rámce  

- **Autorské právo a licencie:** pri tréningu aj pri výstupoch overte pôvod  
  dát, licencie, výnimky pre text and data mining a podmienky poskytovateľa  
  modelu.  
- **Kybernetická bezpečnosť:** smernica NIS2, nariadenie DORA a odvetvové  
  bezpečnostné pravidlá môžu vyžadovať riadenie rizík, hlásenie incidentov  
  a kontrolu dodávateľov.  
- **Digitálne služby a spotrebiteľské právo:** služby s AI musia riešiť  
  klamlivé praktiky, reklamácie, moderovanie obsahu a ochranu používateľa.  
- **Odvetvové predpisy:** zdravotnícke pomôcky, financie, doprava, pracovné  
  právo a vzdelávanie majú vlastné požiadavky na bezpečnosť a dohľad.  
- **Mimo EÚ:** v USA sa povinnosti skladajú z federálnych, štátnych  
  a odvetvových pravidiel; NIST AI RMF je dobrovoľný rámec, nie zákon.  

### Dobrovoľné normy a rámce  

- **ISO/IEC 42001:2023** – požiadavky na systém riadenia umelej inteligencie  
  (AIMS) pre organizácie, ktoré AI vyvíjajú alebo používajú;  
- **ISO/IEC 23894:2023** – usmernenie na riadenie rizík AI;  
- **ISO/IEC 42005:2025** – posudzovanie vplyvu AI systémov;  
- **NIST AI RMF 1.0** – dobrovoľný rámec so štyrmi funkciami: *Govern, Map,  
  Measure, Manage*; pre generatívnu AI existuje profil NIST AI 600-1;  
- **OECD AI Principles** a odporúčanie UNESCO o etike umelej inteligencie –  
  medzinárodné zásady pre dôveryhodnú, bezpečnú a človekom riadenú AI.  

Norma ISO sama osebe nenahrádza zákon ani automaticky neznamená súlad  
s AI Actom. Môže však poskytnúť auditovateľný systém procesov a dôkazov.  

## Príklad: chatbot e-shopu v EÚ  

Chatbot odpovedá na otázky k objednávkam a pracuje s menom, kontaktnými  
údajmi a históriou nákupov.  

1. Určte účely, roly a právne základy; aktualizujte záznam o spracovateľských  
   činnostiach a zmluvu so spracovateľom.  
2. Zobrazte, že používateľ komunikuje s AI, a poskytnite stručnú informáciu  
   o spracovaní s odkazom na podrobné zásady ochrany osobných údajov.  
3. Do modelu posielajte iba minimum údajov. Citlivé prípady presmerujte  
   na vyškoleného pracovníka.  
4. Nastavte krátku a odôvodnenú lehotu uchovávania konverzácií a oddelene  
   riešte bezpečnostné logy, analytiku a tréning.  
5. Otestujte únik osobných údajov, prompt injection, nesprávne odpovede,  
   diskriminačné správanie a dostupnosť pre používateľov.  
6. Umožnite opravu údajov, vybavenie žiadosti používateľa a jednoduché  
   prepnutie na človeka. Incidenty a zmeny modelu evidujte.  

**Dôležité:** vymazanie záznamu konverzácie nemusí odstrániť informáciu  
z váh modelu. Preto oddeľte tréningové dáta od prevádzkových logov,  
obmedzte ich opätovné použitie a používajte techniky ako filtrovanie,  
pseudonymizáciu a obmedzenie retencie. Namiesto nekontrolovaného  
dotrénovania zvážte vrstvu vyhľadávania (retrieval), ktorej obsah možno  
priebežne upravovať a mazať.  

## Čo by mal vedieť každý: prehľad v tabuľke  

| Čo platí | Čo to znamená v praxi | Predpis |
|---|---|---|
| **Máte právo vedieť, aké údaje o vás firma má** | Môžete žiadať kópiu údajov, účely spracovania, príjemcov, lehotu uchovávania, zdroj údajov a informáciu o automatizovanom rozhodovaní. Prvá kópia je zadarmo, odpoveď do 1 mesiaca (najviac +2 mesiace). | čl. 12 a 15 GDPR |
| **Môžete zistiť, kedy a prečo niekto nahliadol do vašich údajov** | Ak firma vedie záznamy o prístupoch, máte právo na dátumy a účely nahliadnutí. Mená konkrétnych zamestnancov spravidla nie. | čl. 15 GDPR, SDEÚ C-579/21 |
| **Logovanie prístupov závisí od rizika** | GDPR neukladá všeobecnú povinnosť logovať každý náhľad, ale pri citlivých údajoch ho v praxi vyžaduje bezpečnosť a zodpovednosť. Vysokorizikové AI systémy musia udalosti logovať automaticky, HIPAA vyžaduje auditné záznamy. | čl. 5 ods. 2 a 32 GDPR; čl. 12, 19 a 26 AI Actu; HIPAA Security Rule |
| **Údaje môžete opraviť, vymazať alebo preniesť** | Právo na opravu, výmaz, obmedzenie spracovania a prenosnosť. Nie sú absolútne, firma ich môže odmietnuť len z dôvodov, ktoré GDPR pripúšťa. | čl. 16 – 20 GDPR |
| **„Vymazané“ neznamená zabudnuté** | Prípad Schrems ukázal, že firma môže uchovávať aj obsah, ktorý používateľ považuje za vymazaný. Pri AI môže informácia zostať aj vo váhach modelu. | čl. 17 GDPR |
| **Námietka voči priamemu marketingu je bezpodmienečná** | Ak namietnete, firma musí s marketingovým spracovaním a profilovaním na tento účel prestať bez ďalšieho posudzovania. | čl. 21 ods. 2 a 3 GDPR |
| **O vás nesmie rozhodnúť výhradne stroj** | Pri rozhodnutí s právnym alebo podobne významným účinkom máte právo na ľudský zásah, vyjadrenie názoru a napadnutie rozhodnutia. Aj rozhodujúce skóre sa môže považovať za rozhodnutie. | čl. 22 GDPR, SDEÚ C-634/21 |
| **Máte právo na vysvetlenie rozhodnutia vysokorizikovej AI** | Ak rozhodnutie vychádza z výstupu vysokorizikového systému a významne vás ovplyvní, môžete žiadať vysvetlenie úlohy AI a hlavných prvkov rozhodnutia. | čl. 86 AI Actu |
| **Musíte vedieť, že komunikujete s AI** | Chatbot alebo hlasový asistent sa musí predstaviť ako AI, ak to nie je zjavné z okolností. | čl. 50 ods. 1 AI Actu |
| **Deepfake musí byť viditeľne označený** | Realistický AI obrázok, video alebo zvuk treba označiť hneď na začiatku. Metadáta ani poznámka v obchodných podmienkach nestačia. | čl. 50 ods. 4 AI Actu |
| **Rozpoznávanie emócií v práci a v škole je zakázané** | Zamestnávateľ ani škola nesmú z videa či hlasu odvodzovať vaše emócie, okrem zdravotných a bezpečnostných dôvodov. Platí od 2. 2. 2025. | čl. 5 ods. 1 písm. f) AI Actu |
| **Uloženie v EÚ neznamená ochranu pred cudzím právom** | Poskytovateľ so sídlom v USA môže byť povinný vydať údaje americkým úradom, aj keď sú uložené v Európe. Rozhoduje, kto má nad údajmi kontrolu. | CLOUD Act (USA), kapitola V GDPR |
| **Únik údajov sa musí hlásiť** | Firma hlási porušenie ochrany údajov dozornému úradu do 72 hodín. Vás musí informovať bez zbytočného odkladu, ak hrozí vysoké riziko. | čl. 33 a 34 GDPR |
| **Môžete sa sťažovať a žiadať náhradu škody** | Sťažnosť podáte na Úrad na ochranu osobných údajov SR. Náhradu majetkovej aj nemajetkovej ujmy môžete žiadať na súde. | čl. 77, 79 a 82 GDPR |
| **Pokuty sú vysoké** | GDPR: až 20 mil. € alebo 4 % obratu. AI Act: až 35 mil. € alebo 7 % pri zakázaných praktikách, až 15 mil. € alebo 3 % pri ďalších povinnostiach vrátane označovania. | čl. 83 GDPR, čl. 99 AI Actu |

## Zhrnutie  

- Každý môže požiadať o kópiu svojich údajov. Prípad Maxa Schremsa ukázal,  
  že firma o človeku môže vedieť oveľa viac, než by čakal.  
- GDPR chráni osobné údaje a práva ľudí; DPIA sa robí podľa rizika, nie  
  automaticky pri každom AI projekte.  
- AI Act zavádza povinnosti podľa rizika, úlohy subjektu a použitia systému.  
  K 12. októbru 2026 je podstatné sledovať pravidlá transparentnosti,  
  GPAI a harmonogram vysokorizikových systémov.  
- Deepfake a neredigované AI texty vo verejnom záujme treba viditeľne  
  označiť. Rozhoduje, či si ich niekto môže pomýliť so skutočnosťou.  
- HIPAA je sektorový rámec USA s obmedzeným rozsahom, nie univerzálna  
  norma pre všetky zdravotné aplikácie.  
- Dátová suverenita je viac než rezidencia údajov: rozhoduje jurisdikcia  
  dodávateľa, kontrola nad kľúčmi a možnosť odísť k inému poskytovateľovi.  
- ISO/IEC 42001, ISO/IEC 23894 a NIST AI RMF pomáhajú nastaviť procesy,  
  ale dobrovoľný štandard sám nenahrádza právnu analýzu.  
- Najlepšia ochrana je priebežná: inventár systémov, posúdenie rizík,  
  kvalitné dáta, testovanie, logovanie, ľudský dohľad a plán nápravy.  

## Oficiálne zdroje  

- [GDPR – úplné znenie](https://eur-lex.europa.eu/eli/reg/2016/679/oj)  
- [Európska komisia: AI Act](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)  
- [AI Act Service Desk](https://ai-act-service-desk.ec.europa.eu/en)  
- [HHS: Summary of the HIPAA Privacy Rule](https://www.hhs.gov/hipaa/for-professionals/privacy/laws-regulations/index.html)  
- [NIST: AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)  
- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html)  
- [ISO/IEC 23894:2023](https://www.iso.org/standard/77304.html)  
- [SDEÚ C-579/21 – prístup k záznamom o nahliadnutí](https://curia.europa.eu/juris/liste.jsf?num=C-579/21)  
- [Data Act – úplné znenie](https://eur-lex.europa.eu/eli/reg/2023/2854/oj)  
- [Európska komisia: prenos údajov EÚ – USA](https://commission.europa.eu/law/law-topic/data-protection/international-dimension-data-protection/eu-us-data-transfers_en)  
- [EDPB: odporúčania 01/2020 k doplnkovým opatreniam pri prenose](https://www.edpb.europa.eu/our-work-tools/our-documents/recommendations/recommendations-012020-measures-supplement-transfer_en)  

## Ďalšie zdroje  

- [The Washington Post – príbeh Maxa Schremsa](https://www.washingtonpost.com/business/economy/facebook-privacy-targeted-by-austrian-law-student/2012/10/19/45a38efc-e70c-11e1-936a-b801f1abab19_story.html)  
- [ITlearning – Označovanie AI obsahu: kedy musíte označiť AI obrázok a kedy nie](https://www.itlearning.sk/oznacovanie-ai-obsahu-kedy-musite-oznacit-ai-obrazok-a-kedy-nie/)  

> **Kontrolný zoznam pre študenta:** Viem vysvetliť účel systému? Poznám  
> pôvod dát a právny základ? Viem, kto kontroluje výstup? Mám testy, logy,  
> lehotu uchovávania a postup pri chybe? Ak nie, systém ešte nie je  
> pripravený na zodpovedné nasadenie.  

## Otázky na diskusiu  

1. Kedy je ľudský dohľad skutočný a kedy iba formálny?  
2. Ako navrhnúť chatbot tak, aby vymazanie používateľských dát nevyžadovalo  
   pretrénovanie celého modelu?  
3. Ktoré riziká sa dajú vyriešiť technicky a ktoré vyžadujú organizačné  
   alebo právne rozhodnutie?  
4. Ktoré údaje by ste nikdy neposlali do cloudovej AI služby mimo EÚ  
   a čím by ste ju nahradili?  

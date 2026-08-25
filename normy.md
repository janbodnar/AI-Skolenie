# Normy a regulácie pre umelú inteligenciu

## Praktický prehľad pre vývojárov a používateľov

**Stav informácií: 25. august 2026.** Tento text je vzdelávací prehľad, nie
právne poradenstvo. Povinnosti závisia od krajiny, odvetvia, úlohy organizácie
(poskytovateľ, nasadzovateľ alebo dodávateľ) a od konkrétneho účelu systému.
Pri projekte s osobnými, zdravotnými alebo inými citlivými údajmi treba zapojiť
právnika a odborníka na compliance.

## Prečo regulácie a normy existujú?

AI môže spracúvať osobné údaje, ovplyvňovať prístup k práci alebo službám a
vytvárať bezpečnostné či spoločenské riziká. Zodpovedné riadenie preto rieši
nielen presnosť modelu, ale celý životný cyklus: návrh, vývoj, testovanie,
nasadenie, monitorovanie, aktualizácie a vyradenie.

Najčastejšie riziká:

- **súkromie a bezpečnosť** – únik údajov, nevhodné použitie dát alebo prompt injection;
- **diskriminácia** – nerovnaké výsledky pre rôzne skupiny ľudí;
- **nepresnosť a halucinácie** – presvedčivo formulované, ale nesprávne výstupy;
- **nedostatočná transparentnosť** – človek nevie, že komunikuje so systémom alebo nerozumie dôvodu rozhodnutia;
- **dezinformácie a podvody** – syntetické médiá, vydávanie sa za inú osobu;
- **autorské práva a obchodné tajomstvo** – neoprávnené použitie obsahu alebo vloženie dôverných údajov do verejnej služby.

> **Základná zásada:** Najprv určte účel a riziko, potom vyberte dáta, model,
> kontrolné mechanizmy a spôsob ľudského dohľadu. Samotný „AI nástroj“ nie je
> compliance stratégia.

## Rýchly postup pre AI projekt

1. **Popíšte účel a hranice použitia.** Čo systém robí, pre koho a čo robiť nesmie?
2. **Zmapujte roly a jurisdikcie.** Kto je prevádzkovateľ a spracovateľ podľa GDPR, poskytovateľ alebo nasadzovateľ podľa AI Actu a prípadne business associate podľa HIPAA?
3. **Urobte posúdenie rizík.** Zahrňte súkromie, diskrimináciu, bezpečnosť, presnosť, ľudské práva, dostupnosť a dopad na životné prostredie.
4. **Zvoľte primerané dáta.** Zdokumentujte pôvod, právny základ, licencie, kvalitu, retenčné lehoty a pravidlá prístupu.
5. **Testujte pred nasadením.** Overte presnosť, robustnosť, zaujatosti, úniky osobných údajov, zneužiteľnosť a správanie v hraničných prípadoch.
6. **Zaveďte dohľad a nápravu.** Uchovávajte relevantné logy, sledujte zmeny výkonu, umožnite eskaláciu na človeka a majte incident-response postup.
7. **Priebežne kontrolujte zmenu rizika.** Nový model, nové dáta alebo nový účel môžu znamenať nové povinnosti.

## GDPR – ochrana osobných údajov v EÚ

GDPR sa uplatňuje najmä na organizácie v EHP, ktoré spracúvajú osobné údaje,
a na organizácie mimo EHP, ak ponúkajú služby ľuďom v EÚ alebo sledujú ich
správanie. Neznamená to, že každý AI systém automaticky potrebuje DPIA alebo
že každé použitie vyžaduje súhlas.

### Čo je pri AI dôležité

- **Právny základ a účel:** pred spracovaním určte konkrétny účel a vhodný právny základ. Oprávnený záujem vyžaduje zdokumentovaný balančný test.
- **Minimalizácia:** používajte iba údaje potrebné na daný účel; neposielajte osobné alebo dôverné údaje do verejného modelu bez posúdenia.
- **Transparentnosť:** informujte ľudí o tom, kto údaje spracúva, prečo, aké kategórie údajov používa, ako dlho ich uchováva a či sa používa automatizované rozhodovanie.
- **Kvalita a bezpečnosť:** riešte presnosť, prístupové práva, šifrovanie, pseudonymizáciu, testovanie a riadenie dodávateľov.
- **Uchovávanie:** nastavte primerané lehoty pre vstupy, výstupy, logy a zálohy. „Uchovávať všetko pre prípad“ nie je zásada minimalizácie.
- **DPIA:** posúdenie vplyvu na ochranu údajov je povinné vtedy, keď spracovanie pravdepodobne povedie k vysokému riziku pre práva a slobody, napríklad pri rozsiahlych citlivých údajoch alebo systematickom monitorovaní.

### Práva jednotlivcov

Jednotlivci môžu mať právo na informácie, prístup, opravu, výmaz, obmedzenie
spracovania, prenosnosť a námietku. Pri výhradne automatizovanom rozhodnutí,
ktoré má právny alebo podobne významný účinok, platí osobitný režim podľa
článku 22 GDPR s výnimkami a požiadavkami na primerané záruky. Nie je to
všeobecné právo „zakázať každú AI“ ani absolútne právo na zdrojový kód či úplné
vysvetlenie modelu.

> **Prakticky:** DPIA, záznamy o spracovateľských činnostiach, zmluvy so
> spracovateľmi, proces vybavovania žiadostí a pravidlá mazania pripravte pred
> pilotným nasadením, nie až po incidente.

## AI Act – nariadenie EÚ o umelej inteligencii

AI Act (nariadenie (EÚ) 2024/1689) zavádza rizikový prístup. Uplatňuje sa podľa
úlohy subjektu a použitia systému, nie iba podľa toho, či sa produkt marketingovo
označuje ako „AI“.

| Úroveň | Príklady a hlavná povinnosť |
|---|---|
| **Zakázané praktiky** | Škodlivá manipulácia, sociálne skórovanie a niektoré formy biometrie či predikcie kriminality sú zakázané; konkrétne výnimky a dátumy treba overiť v nariadení. |
| **Vysoké riziko** | Vybrané systémy v nábore, vzdelávaní, kritickej infraštruktúre, službách, migrácii, presadzovaní práva a justícii vyžadujú riadenie rizík, kvalitné dáta, dokumentáciu, logovanie, ľudský dohľad, presnosť, robustnosť a kybernetickú bezpečnosť. |
| **Špecifická transparentnosť** | Používateľ má byť informovaný, keď komunikuje so strojom; syntetický obsah a deepfakes musia byť podľa pravidiel identifikovateľné alebo označené. |
| **Minimálne alebo žiadne riziko** | Väčšina spamových filtrov a herných funkcií nemá podľa AI Actu dodatočné povinnosti, hoci na ňu naďalej môžu dopadať GDPR, autorské, spotrebiteľské či bezpečnostné pravidlá. |

### Stav povinností k 25. 8. 2026

- Nariadenie nadobudlo účinnosť v roku 2024; zákaz vybraných praktík a požiadavky na AI gramotnosť sa uplatňujú od februára 2025.
- Pravidlá pre poskytovateľov všeobecných AI modelov (GPAI) sa uplatňujú od augusta 2025. Zahŕňajú napríklad technickú dokumentáciu, politiku autorských práv a pri systémovom riziku aj hodnotenie a zmierňovanie rizík.
- Pravidlá transparentnosti pre vybrané systémy sa uplatňujú od augusta 2026.
- Harmonogram vysokorizikových systémov a ďalšie prechodné ustanovenia môžu byť ovplyvnené novelami a sektorovými pravidlami. Pred uvedením na trh vždy skontrolujte aktuálne znenie nariadenia, harmonogram a usmernenia Komisie.

AI Act nenahrádza GDPR. Jeden projekt môže súčasne podliehať obom predpisom,
kybernetickým pravidlám, spotrebiteľskému právu a odvetvovým zákonom.

## HIPAA – zdravotné údaje v USA

HIPAA nie je všeobecný zákon o všetkých zdravotných aplikáciách. Privacy Rule
sa vzťahuje najmä na **covered entities** (zdravotné plány, clearinghouses a
určitých poskytovateľov) a na ich **business associates**. To, či AI dodávateľ
spadá do tejto kategórie, závisí od činnosti a prístupu k PHI; samotný názov
produktu nerozhoduje.

**PHI** sú individuálne identifikovateľné zdravotné informácie, ktoré drží alebo
prenáša covered entity alebo business associate. Pri de-identifikácii existuje
safe-harbor metóda odstránenia určených identifikátorov a metóda expertného
posúdenia. Odstránenie mien samo osebe nestačí.

Pre AI riešenie sú podstatné:

- zmluva **Business Associate Agreement**, ak ide o business associate;
- pravidlo minimálne potrebného rozsahu údajov;
- primerané administratívne, fyzické a technické záruky, riadenie prístupov, autentifikácia, auditné záznamy a postup pri incidente;
- pravidlá používania na výskum, tréning a sekundárne účely;
- posúdenie ďalších federálnych a štátnych zákonov, pretože HIPAA nepokrýva všetky zdravotné údaje a štátne pravidlá môžu byť prísnejšie.

> **Oprava častej nepresnosti:** neuvádzajte jednu pevnú sumu pokuty „za každý
> typ porušenia“. Civilné sankcie sa menia, majú ročné limity a závisia od
> okolností; aktuálne sumy treba overiť v pravidlách HHS/OCR.

## Ďalšie relevantné pravidlá a štandardy

### Právo a verejné rámce

- **Autorské právo a licencie:** pri tréningu aj výstupoch overte pôvod dát, licencie, výnimky pre text-and-data mining a podmienky poskytovateľa modelu.
- **Kybernetická bezpečnosť:** NIS2, DORA a odvetvové bezpečnostné pravidlá môžu vyžadovať riadenie rizík, hlásenie incidentov a kontrolu dodávateľov.
- **Digitálne služby a spotrebiteľské právo:** platformy a služby s AI musia riešiť klamlivé praktiky, reklamácie, moderovanie obsahu a ochranu používateľa.
- **Odvetvové predpisy:** zdravotnícke pomôcky, financie, doprava, pracovné právo a vzdelávanie majú vlastné požiadavky na bezpečnosť a dohľad.
- **Mimo EÚ:** v USA sa povinnosti skladajú z federálnych, štátnych a odvetvových pravidiel; NIST AI RMF je dobrovoľný rámec, nie federálny zákon.

### Dobrovoľné normy a rámce

- **ISO/IEC 42001:2023** – požiadavky na systém riadenia umelej inteligencie (AIMS) pre organizácie, ktoré AI vyvíjajú alebo používajú;
- **ISO/IEC 23894:2023** – usmernenie pre riadenie rizík AI;
- **ISO/IEC 42005:2025** – posudzovanie vplyvu AI systémov;
- **NIST AI RMF 1.0** – dobrovoľný rámec so štyrmi funkciami: *Govern, Map, Measure, Manage*; pre generatívnu AI existuje profil NIST AI 600-1;
- **OECD AI Principles** a odporúčania UNESCO – medzinárodné zásady pre dôveryhodnú, bezpečnú a človekom riadenú AI.

Norma ISO sama osebe nenahrádza zákon ani automaticky neznamená súlad s AI
Actom. Môže však poskytnúť auditovateľný systém procesov a dôkazov.

## Príklad: chatbot e-shopu v EÚ

Chatbot odpovedá na otázky k objednávkam a pracuje s menom, kontaktnými údajmi
a históriou nákupov.

1. Určte účely, roly a právne základy; aktualizujte záznam o spracovateľských činnostiach a zmluvu so spracovateľom.
2. Zobrazte, že používateľ komunikuje s AI, a poskytnite stručnú informáciu o spracovaní s odkazom na podrobné zásady ochrany osobných údajov.
3. Do modelu posielajte iba minimum údajov. Citlivé prípady presmerujte na vyškoleného pracovníka.
4. Nastavte krátku a odôvodnenú lehotu uchovávania konverzácií a oddelene riešte bezpečnostné logy, analytiku a tréning.
5. Otestujte únik osobných údajov, prompt injection, nesprávne odpovede, diskriminačné správanie a dostupnosť pre používateľov.
6. Umožnite opravu údajov, vybavenie žiadosti používateľa a ľahké prepnutie na človeka. Incidenty a zmeny modelu evidujte.

**Dôležité:** vymazanie záznamu konverzácie nemusí vymazať informáciu z váh
modelu. Preto tréningové dáta oddeľte od prevádzkových logov, obmedzte ich
opätovné použitie a používajte techniky ako filtrovanie, pseudonymizáciu,
retenciu a prípadne retrieval vrstvu namiesto nekontrolovaného dotrénovania.

## Zhrnutie

- GDPR chráni osobné údaje a práva ľudí; DPIA sa robí podľa rizika, nie automaticky pri každom AI projekte.
- AI Act zavádza povinnosti podľa rizika, úlohy subjektu a použitia systému. K 25. augustu 2026 je podstatné sledovať aj pravidlá transparentnosti a GPAI.
- HIPAA je sektorový rámec USA s obmedzeným rozsahom, nie univerzálna norma pre všetky zdravotné aplikácie.
- ISO/IEC 42001, ISO/IEC 23894 a NIST AI RMF pomáhajú nastaviť procesy, ale dobrovoľný štandard sám nenahrádza právnu analýzu.
- Najlepšia ochrana je priebežná: inventár systémov, posúdenie rizík, kvalitné dáta, testovanie, logovanie, ľudský dohľad a plán nápravy.

## Oficiálne zdroje

- [GDPR – úplné znenie](https://eur-lex.europa.eu/eli/reg/2016/679/oj)
- [Európska komisia: AI Act](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai)
- [AI Act Service Desk](https://ai-act-service-desk.ec.europa.eu/en)
- [HHS: Summary of the HIPAA Privacy Rule](https://www.hhs.gov/hipaa/for-professionals/privacy/laws-regulations/index.html)
- [NIST: AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
- [ISO/IEC 42001:2023](https://www.iso.org/standard/81230.html)
- [ISO/IEC 23894:2023](https://www.iso.org/standard/77304.html)

> **Kontrolný zoznam pre študenta:** Viem vysvetliť účel systému? Poznám pôvod
> dát a právny základ? Viem, kto kontroluje výstup? Mám testy, logy, lehotu
> uchovávania a postup pri chybe? Ak nie, systém ešte nie je pripravený na
> zodpovedné nasadenie.

## Otázky na diskusiu

1. Kedy je ľudský dohľad skutočný a kedy iba formálny?
2. Ako navrhnúť chatbot tak, aby vymazanie používateľských dát nevyžadovalo pretrénovanie celého modelu?
3. Ktoré riziká sa dajú vyriešiť technicky a ktoré vyžadujú organizačné alebo právne rozhodnutie?

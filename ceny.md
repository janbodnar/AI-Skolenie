# Ceny AI modelov

Ceny AI modelov môžu na prvý pohľad pôsobiť zložito. Poskytovatelia používajú 
viacero modelov, rôzne úrovne výkonu a osobitné ceny za vstup, výstup, uložený 
kontext či nástroje. Základný princíp je však jednoduchý: platí sa za množstvo 
textu a ďalších dát, ktoré model spracuje. 

Cenníky sa často menia. Model môže zlacnieť, pribudne jeho menšia verzia alebo 
poskytovateľ zavedie lacnejší režim pre požiadavky, ktoré nemusia byť vybavené 
okamžite. Konkrétnu cenu preto treba vždy overiť v oficiálnom cenníku daného 
poskytovateľa. Táto kapitola vysvetľuje, **ako sa cena počíta**, nie jeden 
nemenný cenník.

## Čo je token?

Jazykový model nečíta text presne po slovách ani po znakoch. Najprv ho rozdelí 
na menšie časti nazývané **tokeny**. Token môže byť celé krátke slovo, časť 
dlhšieho slova, medzera, interpunkčné znamienko alebo kombinácia týchto prvkov. 

Preto neplatí jednoduché pravidlo, že jeden token je jedno slovo. V angličtine 
je jedno slovo často približne jeden token, ale čísla, programový kód, odborné 
výrazy a slovenčina môžu tokenov spotrebovať viac. Presný počet závisí od 
tokenizéra konkrétneho modelu. 

Pre bežné odhady sa používa jednotka **milión tokenov**, označovaná ako **1M 
tokenov**. Ak model spracuje iba niekoľko tisíc tokenov, výsledná suma môže byť 
veľmi malá, ale pri veľkej aplikácii sa rozdiely medzi modelmi rýchlo znásobia. 

## Vstupné a výstupné tokeny

Pri API sa zvyčajne rozlišujú dve základné kategórie:

*   **Vstupné tokeny (input tokens)** – všetko, čo aplikácia odošle modelu:
	systémové pokyny, otázka používateľa, predchádzajúca konverzácia,
	vložené dokumenty a niekedy aj definície nástrojov.
*   **Výstupné tokeny (output tokens)** – text, ktorý model vygeneruje ako
	odpoveď. Pri modeloch s rozšíreným uvažovaním sa do tejto kategórie môžu
	započítať aj interné reasoning tokeny, hoci ich používateľ priamo nevidí.

Výstupné tokeny bývajú drahšie než vstupné, pretože ich model vytvára postupne
a každý ďalší token vyžaduje ďalší výpočet. Dlhá odpoveď preto môže stáť viac
ako krátka otázka, aj keď otázka samotná bola rovnaká.

Treba počítať s celým vstupom, nie iba s poslednou správou. Ak aplikácia pri
každej požiadavke posiela celú históriu chatu, všetky predchádzajúce správy sa
započítavajú znova. Rovnako sa započítavajú aj pokyny, opis dostupných nástrojov
a text dokumentov priložených ku konverzácii.

## Základný vzorec ceny

Poskytovateľ zvyčajne uvádza cenu za 1 milión tokenov osobitne pre vstup a
výstup. Celkovú cenu jednej požiadavky môžeme približne vypočítať takto:

$$
cena =
\frac{\text{vstupné tokeny}}{1\,000\,000} \times \text{cena vstupu}
+
\frac{\text{výstupné tokeny}}{1\,000\,000} \times \text{cena výstupu}
$$

Predstavme si model s cenou **2 $ za 1M vstupných tokenov** a **8 $ za 1M
výstupných tokenov**. Požiadavka obsahuje 12 000 vstupných tokenov a odpoveď
má 3 000 výstupných tokenov:

*   vstup: $12\,000 / 1\,000\,000 \times 2 = 0{,}024$ $,
*   výstup: $3\,000 / 1\,000\,000 \times 8 = 0{,}024$ $,
*   spolu: **0,048 $**.

Jedna požiadavka je teda lacná. Ak by však aplikácia spracovala 100 000
rovnakých požiadaviek, náklad by bol približne **4 800 $**. Pri odhade rozpočtu
je preto dôležitejší počet požiadaviek a ich veľkosť než cena jedného testu.

## Čo všetko môže byť účtované?

Tokeny nie sú jediná možná položka v cenníku. Záleží na konkrétnom poskytovateľovi
a modeli, ale stretnúť sa môžeme najmä s týmito poplatkami:

*   **Štandardný vstup a výstup:** základné účtovanie za text odoslaný modelu
	a text vygenerovaný modelom.
*   **Cached input:** opakovane používaná časť vstupu môže byť uložená v cache
	a účtovaná lacnejšie. Hodí sa to napríklad pri dlhých systémových pokynoch,
	ktoré sa nemenia medzi požiadavkami.
*   **Reasoning tokeny:** model môže pri uvažovaní vytvoriť interné tokeny.
	Niektorí poskytovatelia ich uvádzajú spolu s výstupom, iní ich zobrazujú
	ako samostatnú položku v štatistikách.
*   **Obrázky a audio:** obrazové vstupy, generované obrázky, prepis reči
	a syntéza hlasu môžu mať vlastné jednotky a ceny. Obrázok sa nemusí
	účtovať ako obyčajný textový token.
*   **Nástroje:** webové vyhľadávanie, spúšťanie kódu, vektorové úložisko,
	dávkové vyhľadávanie alebo iný nástroj môže mať samostatný poplatok.
*   **Dlhý kontext:** niektoré modely majú pri veľmi dlhom vstupe inú cenu
	alebo samostatnú cenovú úroveň.

## API: platba podľa spotreby

**API** je rozhranie určené na zabudovanie modelu do vlastnej aplikácie. Program
odošle požiadavku a poskytovateľ vráti odpoveď. Účet sa potom účtuje podľa
spotreby, najčastejšie podľa počtu vstupných a výstupných tokenov.

Pri API sa zvyčajne neplatí za to, že je otvorená stránka s chatom. Platí sa za
skutočne vykonané požiadavky. To prináša veľkú flexibilitu, ale aj zodpovednosť:
aplikácia môže posielať tisíce požiadaviek bez toho, aby si to používateľ
okamžite všimol.

API je vhodné najmä vtedy, keď:

*   chceme AI zabudovať do vlastného programu, webu alebo firemného systému,
*   potrebujeme automaticky spracovať veľké množstvo dokumentov,
*   chceme vybrať konkrétny model podľa kvality, rýchlosti a ceny,
*   potrebujeme vlastné pravidlá, logovanie, oprávnenia a kontrolu nákladov.

Pri používaní API treba sledovať nielen cenník, ale aj **limity rýchlosti**.
Poskytovateľ môže obmedziť počet požiadaviek alebo počet tokenov za minútu.
Vyšší limit môže vyžadovať overenie účtu, vyšší kredit alebo osobitnú zmluvu.

## Kontrola nákladov a ochrana pred vysokým účtom

Poskytovatelia API ponúkajú viacero nástrojov, ktoré pomáhajú sledovať a
obmedzovať spotrebu. Ich názvy a presné správanie sa líšia, ale princíp býva
podobný:

*   **Usage dashboard:** prehľad počtu tokenov, požiadaviek a minutých peňazí
	podľa dňa, modelu, projektu alebo API kľúča.
*   **Cost alerts:** upozornenie e-mailom alebo iným kanálom, keď spotreba
	prekročí nastavenú sumu alebo sa blíži k rozpočtu.
*   **Soft limit:** upozornenie alebo odporúčanie po dosiahnutí určenej sumy.
	Ďalšie požiadavky môžu pokračovať, ak používateľ neurobí žiadnu zmenu.
*   **Hard limit:** pevný strop, po ktorom sa požiadavky zastavia alebo účet
	prestane používať ďalší kredit. Nie každý poskytovateľ ho ponúka ako
	okamžitú garanciu, preto treba overiť jeho význam v dokumentácii.
*   **Rate limit:** obmedzenie počtu požiadaviek alebo tokenov za minútu.
	Chráni účet pred nárazovou spotrebou aj pred nekonečnou slučkou v programe.
*   **Prepaid kredit:** používanie vopred vloženého zostatku. Po jeho minutí
	sa ďalšie požiadavky môžu zastaviť, prípadne sa kredit automaticky dobije.
*   **Oddelené projekty a kľúče:** vývoj, testovanie a produkcia môžu mať
	samostatné rozpočty, oprávnenia a API kľúče.
*   **Modelové povolenia:** tím môže povoliť iba schválené modely, aby aplikácia
	omylom nepoužila najdrahšiu dostupnú možnosť.

Upozornenie nie je to isté ako blokovanie. Alert môže prísť až po spracovaní
požiadaviek alebo s oneskorením. Ak je dôležité neprekročiť presný rozpočet,
treba kombinovať nastavenia poskytovateľa s vlastnou kontrolou v aplikácii.

Vlastná aplikácia môže pred odoslaním požiadavky skontrolovať odhadovanú cenu,
počítať spotrebu podľa používateľa a zastaviť ďalšie volania po dosiahnutí
denného alebo mesačného limitu. Mala by tiež zaznamenávať chybové opakovania,
pretože automatický retry mechanizmus môže pri nedostupnosti služby vytvoriť
veľké množstvo platených požiadaviek.

Praktické minimum pre produkčnú aplikáciu je:

1.  samostatný API kľúč pre vývoj a produkciu,
2.  nastavený rozpočet a cost alert,
3.  rate limit a maximálny počet výstupných tokenov,
4.  logovanie spotreby podľa modelu a používateľa,
5.  ochrana proti opakovaniu požiadaviek a neobvyklej aktivite.

## Predplatné: platba za prístup

Pri **predplatnom** používateľ platí pravidelnú mesačnú sumu za prístup k
aplikácii, napríklad k webovému chatu. Predplatné zvyčajne poskytuje vyššie
limity než bezplatný účet, prístup k lepším modelom alebo nástrojom a prioritu
pri vyťažení služby.

Predplatné však neznamená neobmedzené používanie. Môže mať:

*   denný alebo týždenný limit správ,
*   samostatné limity pre najvýkonnejšie modely,
*   pomalší prístup po prekročení určitého množstva,
*   pravidlá férového používania,
*   odlišné podmienky pre osobný, tímový a podnikový plán.

Predplatné a API sú často **dve oddelené služby**. Mesačné predplatné chatovacej
aplikácie automaticky neplatí API požiadavky a kredit v API automaticky
neodomkne platený chat. Pri práci s oboma službami treba skontrolovať, ku ktorej
službe je priradená platba.

| Vlastnosť | API | Predplatné |
| :--- | :--- | :--- |
| Spôsob platby | podľa spotreby | pravidelný mesačný poplatok |
| Určenie | vlastné aplikácie a automatizácia | používanie hotovej aplikácie |
| Výber modelu | zvyčajne široký, podľa cenníka | podľa konkrétneho plánu |
| Kontrola nákladov | rozpočet, limity a logy v aplikácii | limity a pravidlá plánu |
| Výsledná cena | závisí od počtu a veľkosti požiadaviek | predvídateľnejšia, ale nie vždy neobmedzená |

## Peak, off-peak a lacnejšie režimy

Niektorí poskytovatelia rozlišujú, **kedy** sa požiadavka spracuje. Počas
vyťažených hodín, takzvaného **peak režimu**, môže byť cena vyššia alebo môže
byť dostupná menšia kapacita. Počas menej vyťažených hodín, teda v režime
**off-peak**, môže byť cena znížená.

Príkladom je **DeepSeek**, ktorý pri vybraných modeloch a typoch použitia
ponúkal odlišné ceny počas špičky a mimo špičky. Takéto podmienky sa môžu meniť
podľa modelu, regiónu, času a typu účtu, preto netreba predpokladať, že jeden
časový rozvrh platí navždy.

Lacnejší režim môže mať aj inú podobu:

*   **Batch processing:** požiadavky sa spracujú neskôr, často za nižšiu cenu.
*   **Flex alebo priority režim:** používateľ si vyberie medzi cenou, rýchlosťou
	a zaručenou dostupnosťou.
*   **Spotová kapacita:** cena môže byť nižšia, ale požiadavka nemusí mať
	rovnakú dostupnosť ako pri štandardnom režime.
*   **Zľava za objem:** veľký zákazník môže dostať individuálne podmienky.

Takéto režimy sú výhodné pre úlohy, ktoré nemusia byť dokončené okamžite:
indexovanie dokumentov, nočné reporty, hromadné preklady alebo prípravu dát.
Naopak, chat pre používateľa v reálnom čase potrebuje nízku latenciu, takže
úsporný off-peak alebo batch režim nemusí byť vhodný.

## Prečo má jeden model viac cien?

Model nie je iba jedna vlastnosť. Poskytovatelia cenu prispôsobujú viacerým
faktorom:

*   **Veľkosť modelu:** menší model je často lacnejší a rýchlejší, ale nemusí
	zvládnuť zložité uvažovanie.
*   **Kvalita a schopnosti:** najvýkonnejší model môže mať drahší výstup,
	väčšie nároky na výpočet a vyššiu latenciu.
*   **Rýchlosť:** expresné spracovanie stojí viac než dávkové spracovanie.
*   **Dĺžka kontextu:** spracovanie mimoriadne dlhého vstupu môže byť drahšie.
*   **Typ zákazníka:** individuálny vývojár, tím a veľká firma môžu mať
	rozdielne zmluvné ceny.
*   **Konkurenčný tlak:** po vydaní nového modelu môžu ceny starších modelov
	klesnúť, aby zostali atraktívne.

Preto nemá zmysel porovnávať iba číslo pri položke „input“. Model s lacným
vstupom môže byť drahší v praxi, ak generuje dlhé odpovede alebo vyžaduje veľa
opakovaných volaní.

## Ako znížiť náklady

Najlepšia optimalizácia začína meraním. Aplikácia by mala pri každej požiadavke
vedieť zaznamenať použitý model, počet vstupných tokenov, počet výstupných
tokenov, čas odpovede a výslednú cenu.

Pomáhajú najmä tieto postupy:

1.  **Skrátiť zbytočný kontext.** Neposielajme pri každej požiadavke celú
	históriu, ak stačí jej zhrnutie alebo niekoľko posledných správ.
2.  **Obmedziť maximálny výstup.** Jasná požiadavka a vhodný limit zabránia
	tomu, aby model vytváral zbytočne dlhé odpovede.
3.  **Použiť menší model na jednoduché úlohy.** Klasifikácia, extrakcia polí
	alebo krátke zhrnutie často nepotrebujú najdrahší model.
4.  **Využiť cache.** Nemenné pokyny alebo dlhé dokumenty môžu byť pri
	podporovaných API účtované lacnejšie.
5.  **Dávkovať úlohy.** Spracovanie mimo špičky alebo cez batch režim môže byť
	lacnejšie, ak výsledok nemusí prísť okamžite.
6.  **Nastaviť limity.** Rozpočet, maximálny počet tokenov, rate limit a
	upozornenia zabránia nechcenému vysokému účtu.
7.  **Kontrolovať opakovanie.** Chybná slučka v programe môže jednu požiadavku
	odoslať tisíckrát. Ochrana proti opakovaniu je dôležitejšia než malé
	rozdiely medzi dvoma cenníkmi.

## Časté omyly

**„Platím za slová.“** Nie presne. Platí sa za tokeny a jeden token nemusí byť
jedno slovo.

**„Platím iba za odpoveď.“** Pri API sa zvyčajne účtuje vstup aj výstup.
Rozsiahla história konverzácie môže byť drahá aj vtedy, keď je odpoveď krátka.

**„Mesačné predplatné zahŕňa API.“** Chatová aplikácia a API majú často oddelené
účtovanie.

**„Najlacnejší vstup znamená najlacnejšiu službu.“** Treba zohľadniť aj cenu
výstupu, dĺžku odpovede, reasoning tokeny, opakované volania a nástroje.

**„Cena z minulého roka stále platí.“** Cenníky sa menia. Poskytovateľ môže
zmeniť cenu, názov modelu, limity aj podmienky off-peak režimu.

## Zhrnutie kapitoly

*   AI modely sa pri API najčastejšie účtujú podľa počtu vstupných a výstupných 
	tokenov.
*   Vstup obsahuje nielen otázku, ale aj systémové pokyny, históriu, dokumenty 
	a definície nástrojov.
*   Výstup býva drahší než vstup a pri reasoning modeloch môžu cenu zvýšiť aj 
	interné tokeny uvažovania.
*   API znamená platbu podľa spotreby, kým predplatné platí za prístup k hotovej 
	aplikácii a konkrétnemu plánu.
*   Predplatné automaticky nemusí zahŕňať API a API kredit nemusí zahŕňať chat. 
*   Peak, off-peak, batch, cache a objemové zľavy môžu výslednú cenu výrazne 
	zmeniť. DeepSeek je príklad poskytovateľa, ktorý používal odlišné ceny 
	počas špičky a mimo špičky pri vybraných modeloch. 
*   Pri porovnávaní treba sledovať celú požiadavku, nie iba cenu jedného tokenu. 

## Otázky & diskusia



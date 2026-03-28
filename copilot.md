# Kapitola: Ekosystém Microsoft Copilot  

Keď sa dnes povie „Copilot", väčšina ľudí si predstaví chatovacieho robota od Microsoftu.  
To je síce pravda, ale len čiastočne. Microsoft stratégiou značky „Copilot" zjednotil všetky  
svoje nástroje umelej inteligencie pod jednu strechu. Pre začiatočníka v oblasti AI je však  
dôležité vedieť, že **nie každý Copilot je rovnaký**.  

Rôzne verzie Copilota majú rôzne schopnosti, pracujú s rôznymi dátami a sú určené  
pre rôzne skupiny používateľov. V tejto kapitole si rozoberieme hlavné produkty z rodiny  
Copilot, aby ste vedeli, ktorý nástroj použiť na konkrétnu úlohu.  

## Prehľad produktov Copilot  

Nasledujúca tabuľka vám poskytne rýchly orientačný prehľad o tom, kde jednotlivé nástroje  
nájdete a na čo slúžia:  

| Produkt | Kde sa používa | Účel |  
| :--- | :--- | :--- |  
| **Copilot** | web, mobil, Windows | všeobecný AI asistent |  
| **Copilot for Microsoft 365** | Word, Excel, Outlook, Teams | práca s dokumentmi a firemnými dátami |  
| **GitHub Copilot** | VS Code, JetBrains | generovanie kódu |  
| **Copilot in Windows** | Windows 11 | ovládanie PC a sumarizácia okien |  
| **Copilot Studio** | web | tvorba vlastných AI agentov |  
| **Copilot for Security** | SOC nástroje | bezpečnostná analýza |  

## Podrobnejší pohľad na jednotlivé nástroje  

Aby ste lepšie pochopili rozdiely, pozrime sa na každý produkt bližšie:  

### 1. Copilot (Všeobecný asistent)  
Toto je verzia, ktorú pozná väčšina verejnosti.  
Je dostupná zadarmo (s možnosťou platenej verzie Pro) cez webový prehliadač,  
mobilnú aplikáciu alebo ako samostatná aplikácia vo Windows.  

*   **Na čo slúži:** Odpovedá na otázky, pomáha s písaním textov, generuje obrázky  
    (cez DALL-E 3) a vyhľadáva informácie na webe.  
*   **Kontext dát:** Pracuje predovšetkým s verejnými informáciami z internetu.  
    Nevidí do vašich firemných e-mailov ani súkromných dokumentov (pokiaľ mu ich  
    explicitne neposkytnete v chate).  

### 2. Copilot for Microsoft 365 (Firemný asistent)  
Toto je prémiová verzia určená pre firmy a organizácie, ktoré využívajú balík  
Microsoft 365.  

*   **Na čo slúži:** Je integrovaný priamo do aplikácií, ktoré poznáte.  
    Vo **Word**e napíše koncept dokumentu, v **Exeli** analyzuje tabuľky,  
    v **Outlook**u zhrnie dlhý reťazec e-mailov a v **Teams**ách spraví zápis  
    zo schôdzky.  
*   **Kontext dát:** Toto je kľúčový rozdiel.  
    Tento Copilot „vidí" vaše firemné dáta (e-maily, súbory na OneDrive, kalendár).  
    Preto je prísne zabezpečený a dodržiava firemné politiky ochrany údajov.  

### 3. GitHub Copilot (Asistent pre programátorov)  
Nástroj určený špecificky pre vývojárov softvéru.  
Vlastní ho Microsoft (cez GitHub), ale funguje nezávisle od kancelárskych balíkov.  

*   **Na čo slúži:** Funguje ako „pair programmer".  
    Navrhuje riadky kódu, dokončuje funkcie, píše testy a pomáha hľadať chyby  
    priamo v editore kódu (napr. VS Code).  
*   **Kontext dát:** Učí sa z verejných repozitárov na GitHube a z kontextu  
    vášho aktuálneho projektu.  

### 4. Copilot in Windows (Súčasť operačného systému)  
Tento nástroj je hlboko integrovaný priamo do operačného systému Windows 11.  

*   **Na čo slúži:** Pomáha meniť nastavenia systému (napr. „zapni tmavý režim"),  
    robí snímky obrazovky alebo sumarizuje obsah otvorených okien.  
*   **Kontext dát:** Má prístup k kontextu vášho desktopu a otvorených aplikácií,  
    aby mohol reagovať na to, čo práve robíte na PC.  

### 5. Copilot Studio (Tvorca vlastných agentov)  
Nástroj pre pokročilejších používateľov a firmy, ktorým nestačí štandardný Copilot.  

*   **Na čo slúži:** Umožňuje vytvoriť si vlastného AI agenta „na mieru".  
    Môžete ho naučiť pracovať s vašimi špecifickými dátami, napojiť ho na vlastné  
    databázy alebo definovať špecifické pracovné postupy.  
*   **Kontext dát:** Definujete si ho vy sami. Môže byť verejný alebo interný.  

### 6. Copilot for Security (Bezpečnostný analytik)  
Špecializovaný nástroj pre kyberbezpečnostné tímy (SOC – Security Operations Center).  

*   **Na čo slúži:** Analyzuje bezpečnostné incidenty, hľadá hrozby v sieťovej premávke  
    a pomáha reagovať na kyberútoky rýchlejšie pomocou AI.  
*   **Kontext dát:** Pracuje s bezpečnostnými logmi a dátami z ochranných systémov  
    firmy.  

## Kľúčové rozdiely: Prečo na tom záleží?  

Prečo musíme rozlišovať medzi týmito verziami?  
Hlavným dôvodom sú **dáta a kontext**.  

1.  **Súkromie:** Bežný Copilot (web) by nemal používať na trénovanie vaše firemné  
    tajomstvá.  
    Copilot for M365 garantuje, že vaše firemné dáta zostanú vo vnútri firmy.  
2.  **Schopnosti:** Copilot vo Worde nevie napísať kód tak dobre ako GitHub Copilot.  
    GitHub Copilot zase nevie zhrnúť váš e-mail v Outlooku.  
3.  **Cena:** Zatiaľ čo základný Copilot je často zdarma, verzie pre firmy  
    (M365, Security, Studio) vyžadujú špecifické licencie.  

## Zhrnutie kapitoly  

*   **Copilot** nie je jeden produkt, ale celá rodina nástrojov umelej inteligencie  
    od Microsoftu.  
*   **Všeobecný Copilot** slúži na bežné otázky a tvorbu obsahu z verejných zdrojov.  
*   **Copilot for Microsoft 365** pracuje s vašimi súkromnými dokumentmi a e-mailmi.  
*   **GitHub Copilot** je špecialista na programovanie.  
*   **Copilot Studio** umožňuje stavať vlastných AI agentov.  
*   Vždy si uvedomte, **s akými dátami** daný Copilot pracuje, aby ste predišli  
    úniku informácií.  

## Otázky a diskusia

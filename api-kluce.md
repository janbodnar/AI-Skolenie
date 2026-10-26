# Základy AI: API kľúče  

*Verzia 1.1 · stav k októbru 2026. Názvy modelov, ceny, limity a cesty v menu  
sa menia, vždy ich overte v oficiálnej dokumentácii poskytovateľa.*  

## 1. Čo je API a API kľúč  

**API** (rozhranie pre programovanie aplikácií) je spôsob, ako spolu  
komunikujú programy. Váš kód pošle požiadavku a služba vráti odpoveď.  

**API kľúč** je tajný reťazec, ktorý sa posiela spolu s požiadavkou.  
Najčastejšie identifikuje váš účet alebo projekt, nie konkrétnu osobu. Slúži  
na:  

- **autentifikáciu** (kto volá),  
- **autorizáciu** (čo smie robiť),  
- **meranie spotreby** (komu sa účtuje).  

Poskytovatelia AI služieb vyžadujú kľúč pri každej požiadavke.  

### 1.1 Prečo je API kľúč lepší ako meno a heslo

Heslo patrí človeku a slúži na prihlásenie do účtu. API kľúč patrí aplikácii  
alebo skriptu a má tieto výhody:  

- **Obmedzený prístup** – kľúč možno nastaviť len na potrebné operácie a  
  projekty, kým heslo otvára celý účet.  
- **Zrušenie bez zásahu do účtu** – kľúč možno kedykoľvek zrušiť alebo  
  nahradiť novým a heslo používateľa zostane nezmenené.  
- **Nezávislosť od človeka** – aplikácia nepotrebuje heslo používateľa, ktoré  
  by si musela uchovávať.  
- **Sledovanie použitia** – spotreba a aktivita sa dajú priradiť ku  
  konkrétnemu kľúču.  
- **Menšie riziko pri úniku** – heslo sa často používa na viacerých službách,  
  kým kľúč je zvyčajne viazaný na jednu službu.  

API kľúč však nie je bezpečný sám o sebe: nevie overiť človeka a každý, kto ho  
získa, ho môže použiť. Preto ho treba chrániť rovnako starostlivo ako heslo.  

### 1.2 Aplikácie s umelou inteligenciou

Mnohé aplikácie AI na komunikáciu s poskytovateľom modelu používajú API kľúče  
alebo tokeny. Nie všetky však fungujú rovnako:  

- **Rozšírenia vo VS Code** – ak rozšírenie volá API poskytovateľa (napr.  
  OpenAI alebo Anthropic), zvyčajne zadáte svoj API kľúč do nastavení  
  rozšírenia. Niektoré rozšírenia namiesto kľúča používajú prihlásenie cez  
  účet, napríklad GitHub Copilot.  
- **ChatGPT** – webová aplikácia sa prihlasuje cez váš účet a používa interný  
  token relácie. Používateľ tam API kľúč nezadáva. API kľúč potrebujete až  
  vtedy, keď ChatGPT volá vaša vlastná aplikácia cez API platformu  
  poskytovateľa.  
Pravidlo: kľúč zadaný do editora alebo aplikácie ukladajte do bezpečného  
úložiska (pozri časť 5) a nikdy ho necommitujte do repozitára.  

## 2. Ako API kľúč funguje  

Kľúč sa posiela v **hlavičke** požiadavky. Štandardom je hlavička  
`Authorization: Bearer <kľúč>` (niektorí poskytovatelia používajú vlastnú,  
napr. Anthropic `x-api-key`).  

> **Nikdy neposielajte kľúč v URL (parametri).** Adresy sa ukladajú do logov  
> servera, proxy a histórie prehliadača, takže kľúč jednoducho unikne.  

Server overí platnosť kľúča a oprávnenia:  

- neplatný alebo chýbajúci kľúč: chyba **401**,  
- kľúč nemá oprávnenie na danú akciu: chyba **403**,  
- príliš veľa požiadaviek: chyba **429**,  
- platný kľúč: server požiadavku spracuje a vráti odpoveď.  

Najrýchlejší test kľúča je volanie cez `curl`:  

```bash
curl https://api.openai.com/v1/chat/completions \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-4o-mini",
    "messages": [{"role": "user", "content": "Ahoj"}]
  }'
```

Pri ladení používajte izolované prostredie (samostatný testovací projekt),  
nástroje ako `curl` alebo Postman a sledujte logy, či sa kľúč náhodou  
neposiela v URL. Nikdy nelogujte celý kľúč, iba jeho zamaskovanú časť, napr.  
`sk-...a1b2`.  

## 3. Kľúče, tokeny a servisné účty  

Termíny sa často miešajú, no ide o rôzne veci:  

- **Tajný kľúč (secret key):** dlhodobý kľúč s plným prístupom k vášmu účtu  
  alebo projektu. Pri väčšine AI poskytovateľov (OpenAI, Anthropic) existujú  
  iba tajné kľúče. Nikdy ich nezverejňujte.  
- **Verejný kľúč:** pojem zo služieb ako Stripe alebo Firebase, kde je určený  
  na použitie vo frontende a má obmedzené práva. AI poskytovatelia ho zvyčajne  
  nemajú.  
- **Dočasný token:** vypršie po určitom čase (napr. OAuth tokeny). Pri úniku  
  je škoda časovo obmedzená.  
- **Servisný účet:** identita pre automatizované aplikácie a servery (typické  
  pre Google Cloud). Má vlastné práva a nepatrí konkrétnemu človeku.  

## 4. Kde získať API kľúč  

Cesty v menu sa menia, orientačne:  

| Poskytovateľ | Kde kľúč získať |
| --- | --- |
| OpenAI | platform.openai.com → API keys |
| Anthropic | console.anthropic.com → API keys |
| Google (Gemini) | aistudio.google.com → Get API key (Cloud Console / Vertex AI slúži na podnikové nasadenie) |
| Hugging Face | huggingface.co → Settings → Access Tokens |
| Microsoft Azure | portal.azure.com → Azure OpenAI / Azure AI Foundry |

Postup je všade podobný:  

1. Vytvorte si účet a overte e-mail alebo telefón.  
2. Prejdite do sekcie API alebo vývojárskeho portálu.  
3. Nastavte fakturáciu (väčšina služieb nefunguje bez kreditu alebo platobnej  
   karty).  
4. Kliknite na „Create new secret key“ alebo podobné tlačidlo a kľúču dajte  
   zmysluplný názov (napr. `moj-projekt-dev`).  
5. Kľúč si okamžite uložte. Mnohé služby (napr. OpenAI, Anthropic) ho zobrazia  
   iba raz. Ak ho stratíte, vygenerujete nový.  

Kľúč **nikdy neposielajte e-mailom ani do chatu**, vrátane chatu s AI  
asistentom.  

## 5. Ako kľúč bezpečne uložiť  

Zlaté pravidlo: **kľúč nepatrí do zdrojového kódu.** Namiesto toho ho uložte  
mimo kódu a program ho načíta za behu.  

### Premenné prostredia  

Python:  

```python
import os

api_key = os.getenv("OPENAI_API_KEY")
```

JavaScript (Node.js):  

```javascript
const key = process.env.OPENAI_API_KEY;
```

Shell (Linux/macOS):  

```bash
export OPENAI_API_KEY="sk-..."
```

PowerShell (Windows):  

```powershell
$env:OPENAI_API_KEY = "sk-..."
```

Týmto oddelíte tajomstvá od kódu.  

### Súbor .env pri vývoji  

Pri lokálnom vývoji je pohodlné mať kľúče v súbore `.env`:  

```
OPENAI_API_KEY=sk-...
```

- Súbor `.env` pridajte do `.gitignore` **skôr, než prvýkrát spravíte  
  commit.** Kľúč, ktorý sa raz dostal do histórie Gitu, sa už považuje za  
  uniknutý.  
- Do repozitára dajte `.env.example` s názvami premenných bez hodnôt, aby  
  ostatní vedeli, čo nastaviť.  

### Produkcia  

V produkcii používajte správcu tajomstiev: AWS Secrets Manager, Google Secret  
Manager, Azure Key Vault, prípadne tajomstvá vášho hostingu alebo CI/CD  
(GitHub Actions secrets). Na osobné kľúče postačí správca hesiel.  

Používajte **samostatné kľúče pre vývoj a produkciu**, aby únik testovacieho  
kľúča neohrozil ostrú prevádzku.  

## 6. Príklady použitia  

Knižnice sa vyvíjajú, pozrite si aktuálnu dokumentáciu a názov modelu nahraďte  
aktuálnym.  

### Python, OpenAI  

```python
import os
from openai import OpenAI

client = OpenAI(api_key=os.getenv("OPENAI_API_KEY"))

response = client.chat.completions.create(
    model="gpt-4o-mini",  # skontrolujte aktuálny zoznam modelov
    messages=[{"role": "user", "content": "Ahoj"}],
)
print(response.choices[0].message.content)
```

### Python, Anthropic  

Klient si kľúč automaticky načíta z premennej `ANTHROPIC_API_KEY`.  

```python
from anthropic import Anthropic

client = Anthropic()

message = client.messages.create(
    model="claude-sonnet-5-5",  # skontrolujte aktuálny zoznam modelov
    max_tokens=500,
    messages=[{"role": "user", "content": "Ahoj"}],
)
print(message.content[0].text)
```

### JavaScript (Node.js), priame volanie  

```javascript
const response = await fetch("https://api.openai.com/v1/chat/completions", {
  method: "POST",
  headers: {
    "Authorization": `Bearer ${process.env.OPENAI_API_KEY}`,
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    model: "gpt-4o-mini",
    messages: [{ role: "user", content: "Ahoj" }],
  }),
});

const data = await response.json();
console.log(data.choices[0].message.content);
```

## 7. Bezpečnosť a časté chyby  

Kľúč je ako heslo: chráňte ho rovnako dôsledne.  

**Zásady:**  

- Obmedzte práva kľúča na nevyhnutné minimum.  
- Používajte samostatný kľúč pre každý projekt a prostredie, nie jeden na  
  všetko.  
- Sledujte, kto má prístup k projektu a kľúčom.  
- Kľúče pravidelne rotujte.  
- Pri úniku kľúč okamžite odvolajte (pozri sekciu 9).  

**Najčastejšie chyby:**  

- Kľúč v kóde alebo v **verejnom GitHub repozitári**. Boti ich vyhľadávajú v  
  priebehu minút.  
- Zdieľanie kľúča v e-maile, na Slacku alebo v chate.  
- **Použitie kľúča vo frontende** (JavaScript v prehliadači, mobilná  
  aplikácia). Každý návštevník ho vidí v sieťovej komunikácii.  
- Ignorovanie upozornení na kvóty a expiráciu.  
- Kopírovanie jedného kľúča do viacerých projektov bez potreby.  

**Ako použiť AI z webu bez vystavenia kľúča?** Vytvorte vlastný backend  
(proxy). Frontend volá váš server, server pridá kľúč a zavolá poskytovateľa.  
Na vlastnom serveri môžete pridať aj autentifikáciu používateľov a vlastné  
limity.  

## 8. Kvóty, limity a fakturácia  

Poskytovatelia obmedzujú rýchlosť aj objem používania. Pri AI sa typicky  
sledujú:  

- **RPM**: počet požiadaviek za minútu,  
- **TPM**: počet tokenov za minútu,  
- celková mesačná spotreba a úroveň (tier) účtu.  

Konkrétne čísla závisia od poskytovateľa a účtu, nájdete ich v dokumentácii a  
v dashboarde.  

Prekročenie limitu vráti chybu **429**. Odporúčaný postup je zopakovať  
požiadavku s postupne rastúcim čakaním (exponential backoff).  

Aby vás faktúra neprekvapila:  

- nastavte **mesačný rozpočtový strop** (spend limit) a upozornenia v  
  dashboarde,  
- pravidelne kontrolujte spotrebu,  
- využívajte caching a dávkové spracovanie (batch), ak ho poskytovateľ ponúka,  
- vyberajte lacnejší model tam, kde stačí.  

## 9. Rotácia, odvolanie a únik kľúča  

**Rotácia** je výmena kľúča za nový. Správny postup, aby nenastal výpadok:  

1. vytvorte nový kľúč,  
2. nasaďte ho do aplikácie,  
3. overte, že všetko funguje,  
4. až potom odvolajte starý kľúč.  

**Odvolanie** okamžite zablokuje prístup so starým kľúčom.  

**Ak kľúč uniknul** (napr. skončil v repozitári):  

1. **Okamžite ho odvolajte.** Samotné zmazanie z Gitu nestačí, kľúč zostáva v  
   histórii a mohol byť už skopírovaný.  
2. Vygenerujte nový kľúč a nasaďte ho.  
3. Skontrolujte spotrebu a logy, či ho niekto nezneužil.  
4. Ak boli v ohrození aj ďalšie tajomstvá (databázové heslá, iné kľúče),  
   zmeňte aj tie.  
5. Zapnite secret scanning (napr. na GitHube), ktorý podobné úniky odhalí  
   skoro.  

## 10. Etika a zodpovednosť  

Kľúč je viazaný na váš účet a **vy zodpovedáte za všetko, čo sa cez neho  
vykoná.** Preto:  

- nezneužívajte službu na škodlivý obsah,  
- dodržiavajte podmienky používania poskytovateľa,  
- rešpektujte súkromie a autorské práva,  
- nevkladajte do požiadaviek osobné alebo citlivé údaje, ak na to nemáte  
  oprávnenie.  

## 11. Záver a kontrolný zoznam  

API kľúče sú základom práce s AI službami. Správna správa kľúčov chráni vaše  
dáta aj peniaze. Ak si nie ste istí, vždy sa riaďte oficiálnou dokumentáciou  
poskytovateľa.  

**Kontrolný zoznam:**  

- [ ] Kľúč nie je v zdrojovom kóde ani v Gite.  
- [ ] `.env` je v `.gitignore` a v repozitári je `.env.example`.  
- [ ] Vývoj a produkcia majú samostatné kľúče.  
- [ ] Kľúč sa nepoužíva vo frontende, ale cez backend.  
- [ ] Je nastavený rozpočtový strop a upozornenia na spotrebu.  
- [ ] Viem, ako kľúč rotovať a odvolať.  

## Skills (zručnosti) v rámci prispôsobenia VS Code agenta

Skills (zručnosti) sú dopyty (on-demand) riadené pracovné postupy, ktoré  
kombinujú doménové znalosti s opakovane použiteľnými skriptami a šablónami.  
Na rozdiel od vždy zapnutých inštrukcií sa skill načítava iba vtedy, keď agent  
deteguje relevantné spúšťacie slovo vo vašej požiadavke.

### Anatómia skill-u

Skill žije vo vlastnom adresári `.agents/skills/<názov>/` a pozostáva z:

```
.agents/skills/<názov>/
├── SKILL.md      # Metadáta + inštrukcie pre agenta
└── scripts/      # (voliteľné) Pribalené nástroje
```

Súbor `SKILL.md` používa YAML frontmatter na objavenie (discovery) a telo v  
markdown pre samotné inštrukcie.

### Príklad: Skill na hádzanie kockami

Praktický príklad — skill, ktorý hádže polyedrickými kockami (d6, d20, 3d6, atď.)  
pomocou Pythonu:

#### Frontmatter

```yaml
---
name: dice
description: Roll one or more dice with any number of sides (e.g., d6, d20, 3d6, 2d10).
    Use when asked to roll dice, generate random numbers, or simulate tabletop RPG dice rolls.
compatibility: Platform independent — requires Python 3. No internet or API key needed.
---
```

Kľúčové polia:
- **`name`** — Musí sa zhodovať s názvom adresára (`dice` → `.agents/skills/dice/`)
- **`description`** — Povrch pre spúšťanie. Agent prehľadáva toto pole, aby sa  
rozhodol, kedy skill načítať. Uveďte konkrétne kľúčové slová, ktoré by používateľ  
mohol povedať (napr. "hoď kockou", "d20", "náhodné číslo").
- **`compatibility`** — Pomáha agentovi poznať predpoklady (v tomto prípade Python 3).

#### Telo — Inštrukcie

Telo hovorí agentovi **ako** používať pribalené skripty:

```markdown
## Roll dice

Use the bundled Python scripts in `scripts/`. Format: `<count>d<sides>`.

```bash
# Single die (e.g. d20)
python3 scripts/roll.py <sides>

# Multiple dice with total (e.g. 3d6)
python3 scripts/roll_multi.py <count> <sides>

# Roll with advantage (2 dice, keep highest)
python3 scripts/roll_advantage.py <sides>
```
```

#### Pribalené skripty

Adresár `scripts/` obsahuje tri Python súbory, každý samostatne spustiteľný:

**`scripts/roll.py`** — Hod jednej kocky:
```python
#!/usr/bin/env python3
import random, sys
print(random.randint(1, int(sys.argv[1])))
```

**`scripts/roll_multi.py`** — Hod viacerými kockami a súčet:
```python
#!/usr/bin/env python3
import random, sys
count, sides = int(sys.argv[1]), int(sys.argv[2])
rolls = [random.randint(1, sides) for _ in range(count)]
for i, r in enumerate(rolls, 1):
    print(f"Die {i}: {r}")
print(f"Total: {sum(rolls)}")
```

**`scripts/roll_advantage.py`** — Hod s výhodou:
```python
#!/usr/bin/env python3
import random, sys
sides = int(sys.argv[1])
a, b = random.randint(1, sides), random.randint(1, sides)
print(f"Rolls: {a}, {b} | Best: {max(a, b)}")
```

#### V akcii

Keď používateľ povie *"hoď d20"*, agent deteguje spúšťač, načíta skill a vykoná:

```
$ python3 scripts/roll.py 20
→ 17
```

Alebo s výhodou:

```
$ python3 scripts/roll_advantage.py 20
→ Rolls: 7, 18 | Best: 18
```

### Prečo používať skills?

| Vlastnosť | Výhoda |
|---|---|
| **Na požiadanie** | Načíta sa len keď je to relevantné — šetrí kontextové okno |
| **Samonosné** | Obsahuje všetky potrebné skripty |
| **Znovupoužiteľné** | Rovnaký skill funguje v akomkoľvek projekte v workspaci |
| **Objaviteľné** | Pole `description` je indexované pre automatické spúšťanie |

### Príklad: Weather skill (počasie)

Weather skill umožňuje agentovi získať aktuálne počasie, teplotu,  
vlhkosť, rýchlosť vetra a predpoveď pre ľubovoľné mesto.  
Používa verejné API wttr.in, ktoré nevyžaduje API kľúč.  

#### Frontmatter

```yaml
---
name: weather
description: Get current weather, temperature, humidity, wind speed,
    and forecast for any city using the wttr.in API. Use when asked about the
    weather, temperature, forecast, or climate in a specific location.
compatibility: Requires internet access. Uses the free wttr.in API (no API key needed).
---
```

#### Telo — Inštrukcie

Inštrukcie hovoria agentovi, ako zavolať curl príkaz na získanie  
aktuálneho počasia alebo 3-dňovej predpovede:  

```markdown
## Get weather

Use curl to fetch weather data from wttr.in:


# Detailed weather
curl -s "wttr.in/<city>?format=%l:+%C,+%t(feels+like+%f),+humidity+%h,+wind+%w"

# Full 3-day forecast
curl -s "wttr.in/<city>?u&0"
```

#### V akcii

Keď používateľ povie *"aké je počasie v Bratislave?"*, agent spustí:  

```
$ curl -s "wttr.in/Bratislava?format=%l:+%C,+%t(feels+like+%f),+humidity+%h,+wind+%w"
→ Bratislava: Partly Cloudy, +22°C(feels like +25°C), humidity 57%, wind →17km/h
```

Pre 3-dňovú predpoveď:  

```
$ curl -s "wttr.in/Bratislava?3"
→ zobrazí tabuľku s predpoveďou na 3 dni
```

### Príklad: World-Time skill (svetový čas)

World-Time skill poskytuje aktuálny dátum a čas pre ľubovoľné mesto  
alebo časovú zónu na svete. Používa worldtimeapi.org s fallbackom na  
timeapi.io.  

#### Frontmatter

```yaml
---
name: world-time
description: Get the current date and time for any city or timezone worldwide.
    Use when asked about the time in a specific location, timezone differences,
    or what time it is somewhere.
compatibility: Requires internet access. Uses the free Time API (worldtimeapi.org)
    and fallback to timeapi.io.
---
```

#### Telo — Inštrukcie

Inštrukcie hovoria agentovi, ako zavolať API na získanie času  
podľa časovej zóny alebo kontinentu a mesta:  

```markdown
## Get current time

Use curl to fetch the current time from a public time API:


# By timezone
curl -s "https://worldtimeapi.org/api/timezone/<timezone>"

# Search by city
curl -s "https://worldtimeapi.org/api/timezone/<continent>/<city>"
```

#### V akcii

Keď používateľ povie *"koľko je hodín v Tokiu?"*, agent zavolá:  

```
$ curl -s "https://www.timeapi.io/api/Time/current/zone?timeZone=Asia/Tokyo"
→ {"year":2026,"month":7,"day":7,"hour":6,"minute":20,...,"time":"06:20",...}
```

Pre Moskvu:  

```
$ curl -s "https://www.timeapi.io/api/Time/current/zone?timeZone=Europe/Moscow"
→ {"year":2026,"month":7,"day":7,"hour":0,"minute":20,...,"time":"00:20",...}
```

### Príklad: Firms skill (vyhľadávanie firiem)

Firms skill umožňuje agentovi vyhľadávať slovenské a české spoločnosti  
podľa názvu alebo IČa a získavať detailné informácie z obchodného registra,  
vrátane DIČ, právnej formy, sídla a registračných údajov.  
Používa verejné API subjekt.sk, ktoré nevyžaduje API kľúč.  

#### Frontmatter

```yaml
---
name: firms
description: Look up Slovak and Czech companies by name or ICO number.
    Get company details like VAT, legal form, address, registration info.
    Use when asked about company registry, business data, ICO, DIC,
    or firm info for SK/CZ entities.
compatibility: Requires internet access. Uses the free subjekt.sk API
    (no API key needed). Requires Python 3 with `requests`.
---
```

#### Telo — Inštrukcie

Inštrukcie hovoria agentovi, ako použiť pribalené Python skripty  
na vyhľadávanie a detail firmiem:  

```markdown
## Search companies by name or ICO

```bash
python3 scripts/search_firm.py "<query>" [country] [limit]
```

- `country`: `sk`, `cz`, or `both` (default: `sk`)
- `limit`: 1–50 (default: `10`)

## Get company detail by ICO

```bash
python3 scripts/firm_detail.py <ico> [country]
```
```

#### Pribalené skripty

Adresár `scripts/` obsahuje dva Python súbory, ktoré používajú knižnicu  
`requests` na komunikáciu s REST API subjekt.sk:  

**`scripts/search_firm.py`** — Vyhľadanie firmy podľa názvu alebo IČa:  
```python
#!/usr/bin/env python3
import requests, sys

BASE = "https://subjekt.sk/api/v1"
query, country, limit = sys.argv[1], sys.argv[2] if len(sys.argv) > 2 else "sk", \
                        int(sys.argv[3]) if len(sys.argv) > 3 else 10
resp = requests.get(f"{BASE}/search",
    params={"q": query, "country": country, "limit": limit},
    headers={"User-Agent": "subjekt-skill/1.0"}, timeout=10)
data = resp.json()

for item in data.get("items", []):
    ico = item.get("ico", "?")
    name = item.get("name", "?")
    city = item.get("city") or ""
    zipcode = item.get("zip") or ""
    street = item.get("street") or ""
    addr = ", ".join(p for p in [street, f"{city} {zipcode}".strip()] if p)
    vat = item.get("vat") or "—"
    vat_eu = item.get("vatEu") or "—"
    form = item.get("legalForm") or "—"
    print(f"{ico}  {name}")
    print(f"    {addr}")
    print(f"    VAT: {vat}  VAT (EU): {vat_eu}")
    print(f"    Legal form: {form}\n")

print(f"Results: {data.get('total', len(data.get('items', [])))}")
```

**`scripts/firm_detail.py`** — Detail firmy podľa IČa:  
```python
#!/usr/bin/env python3
import requests, sys

BASE = "https://subjekt.sk/api/v1"
ico = sys.argv[1]
country = sys.argv[2] if len(sys.argv) > 2 else None
url = f"{BASE}/entity/{ico}"
if country:
    url += f"?country={country}"

resp = requests.get(url, headers={"User-Agent": "subjekt-skill/1.0"}, timeout=10)
data = resp.json()
if not data.get("ico"):
    print(f"Entity not found for ICO: {ico}")
    sys.exit(1)

print(f'{data["ico"]}  {data.get("name", "?")}')
print("=" * 40)
for key, label in [("street", "Address"), ("city", "City"), ("zip", "ZIP"),
                    ("country", "Country"), ("legalForm", "Legal form"),
                    ("vat", "VAT"), ("vatEu", "VAT (EU)"),
                    ("established", "Established"), ("terminated", "Terminated"),
                    ("register", "Register")]:
    val = data.get(key)
    if val:
        print(f"{label + ':':12s} {val}")
```

#### V akcii

Keď používateľ povie *"nájdi firmu Macrosoft"*, agent spustí:  

```
$ python3 scripts/search_firm.py "Macrosoft" sk 10
→ 36527904  MACROSOFT INTERNATIONAL, s.r.o.
      Ľ. Štúra, Nové Zámky 94001
      Legal form: Spoločnosť s ručením obmedzeným

  36791598  Macrosoft s.r.o.
      Štefánikova, Bratislava - Staré Mesto 81104
      VAT: 2022400985  VAT (EU): SK2022400985
      Legal form: Spoločnosť s ručením obmedzeným
  Results: 3
```

Alebo na detail konkrétnej firmy:  

```
$ python3 scripts/firm_detail.py 36791598 sk
→ 36791598  Macrosoft s.r.o.
  ========================================
  Address:      Štefánikova, Bratislava 81104
  Country:      SK
  Legal form:   Spoločnosť s ručením obmedzeným
  VAT:          2022400985
  VAT (EU):     SK2022400985
  Established:  2007-06-15
  Register:     Mestský súd Bratislava III no. Sro/46472/B
```

Parametre `country` a `limit` umožňujú flexibilné vyhľadávanie:  

*Hľadanie v českom registri (country=cz):*  

```
$ python3 scripts/search_firm.py "Macrosoft" cz 5
→ Results: 0
```

*Hľadanie v oboch krajinách (country=both):*  

```
$ python3 scripts/search_firm.py "Macrosoft" both 3
→ 36527904  MACROSOFT INTERNATIONAL, s.r.o.
      Ľ. Štúra, Nové Zámky 94001
      Legal form: Spoločnosť s ručením obmedzeným

  34540539  Mária Strmisková - MACROSOFT
      Majerníkova, Bratislava - Karlova Ves 84105
      Legal form: Podnikateľ-fyzická osoba

  36791598  Macrosoft s.r.o.
      Štefánikova, Bratislava - Staré Mesto 81104
      VAT: 2022400985  VAT (EU): SK2022400985
      Legal form: Spoločnosť s ručením obmedzeným
  Results: 3
```

*Obmedzenie počtu výsledkov (limit=1):*  

```
$ python3 scripts/search_firm.py "Macrosoft" sk 1
→ 36527904  MACROSOFT INTERNATIONAL, s.r.o.
      Ľ. Štúra, Nové Zámky 94001
      Legal form: Spoločnosť s ručením obmedzeným
  Results: 1
```

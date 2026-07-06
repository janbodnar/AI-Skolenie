# Agent Skills — Kompletný sprievodca

> **Agent Skills** sú ľahký, otvorený formát na rozširovanie schopností AI agentov pomocou špecializovaných znalostí a workflowov.
>
> Oficiálna stránka: [https://agentskills.io](https://agentskills.io)


## 📑 Obsah

1. [Čo sú Agent Skills?](#čo-sú-agent-skills)
2. [Prečo používať Agent Skills?](#prečo-používať-agent-skills)
3. [Ako Agent Skills fungujú?](#ako-agent-skills-fungujú)
4. [Štruktúra skillu](#štruktúra-skillu)
5. [Specifikácia `SKILL.md`](#specifikácia-skillmd)
6. [Praktické príklady](#praktické-príklady)
7. [Best practices](#best-practices)
8. [Používanie skriptov](#používanie-skriptov)
9. [Optimalizácia popisov](#optimalizácia-popisov)
10. [Klientská podpora](#klientská-podpora)
11. [VS Code Skills — workspace skills](#vs-code-skills--workspace-skills)



## Čo sú Agent Skills?

Agent Skills sú **otvorený štandard** pôvodne vyvinutý spoločnosťou [Anthropic](https://www.anthropic.com/) na balenie špecializovaných znalostí a workflowov do prenosných, verzovateľných priečinkov, ktoré AI agenti načítavajú podľa potreby.

V jadre je skill jednoduchý priečinok obsahujúci `SKILL.md` súbor s metadátami (`name` a `description`) a inštrukciami, ktoré agentovi hovoria, ako vykonať konkrétnu úlohu.

```
my-skill/
├── SKILL.md          # Povinné: metadáta + inštrukcie
├── scripts/          # Voliteľné: spustiteľný kód
├── references/       # Voliteľné: dokumentácia
├── assets/           # Voliteľné: šablóny, zdroje
└── ...               # Ďalšie súbory alebo priečinky
```



## Prečo používať Agent Skills?

Agenti sú čoraz schopnejší, ale často im chýba **kontext** na spoľahlivé vykonávanie reálnych úloh. Skills riešia tento problém tým, že balia procedurálne znalosti do formátu, ktorý agenti načítavajú na požiadanie:

- **Doménová expertíza** — zachyťte špecializované znalosti (právne procesy, data pipelines, formátovanie prezentácií) ako opakovane použiteľné inštrukcie.
- **Opakovateľné workflowy** — premeňte viackrokové úlohy na konzistentné, auditovateľné procedúry.
- **Cross-produktové zdieľanie** — vytvorte skill raz a používajte ho v akomkoľvek kompatibilnom agentovi.



## Ako Agent Skills fungujú?

Agenti načítavajú skills pomocou **progresívneho zverejňovania** (progressive disclosure) v troch fázach:

```
┌─────────────────────────────────────────────────────┐
│                     DISCOVERY                       │
│  Pri štarte agent načíta len name a description     │
│  (~100 tokenov) pre každý skill                     │
├─────────────────────────────────────────────────────┤
│                     ACTIVATION                      │
│  Keď úloha zodpovedá popisu, agent načíta celý      │
│  SKILL.md do kontextu (< 5000 tokenov odporúčaných) │
├─────────────────────────────────────────────────────┤
│                     EXECUTION                       │
│  Agent nasleduje inštrukcie, volá skripty a         │
│  načíta referenčné súbory podľa potreby             │
└─────────────────────────────────────────────────────┘
```



## Štruktúra skillu

### Povinné súbory

| Súbor | Popis |
|-|-|
| `SKILL.md` | YAML frontmatter + Markdown inštrukcie |

### Voliteľné priečinky

| Priečinok | Popis |
|--|-|
| `scripts/` | Spustiteľný kód (Python, Bash, JavaScript, ...) |
| `references/` | Doplňujúca dokumentácia načítavaná na požiadanie |
| `assets/` | Šablóny, obrázky, dátové súbory |



## Specifikácia `SKILL.md`

### YAML Frontmatter

| Pole | Povinné | Obmedzenia |
||||
| `name` | Áno | Max 64 znakov. Len malé písmená, číslice a pomlčky. Musí zodpovedať názvu priečinka. |
| `description` | Áno | Max 1024 znakov. Popisuje čo skill robí a kedy ho použiť. |
| `license` | Nie | Názov licencie alebo odkaz na licenčný súbor. |
| `compatibility` | Nie | Max 500 znakov. Požiadavky na prostredie. |
| `metadata` | Nie | Ľubovoľné kľúč-hodnota páry. |
| `allowed-tools` | Nie | Zoznam povolených nástrojov (experimentálne). |

### Príklady frontmatter

**Minimálny príklad:**

```yaml

name: roll-dice
description: Roll dice using a random number generator. Use when asked to roll a die (d6, d20, etc.), roll dice, or generate a random dice roll.

```

**Rozšírený príklad:**

```yaml

name: pdf-processing
description: Extracts text and tables from PDF files, fills PDF forms, and merges multiple PDFs. Use when working with PDF documents.
license: Apache-2.0
compatibility: Requires Python 3.14+ and uv
metadata:
  author: example-org
  version: "1.0"

```

### Body (inštrukcie)

Telo `SKILL.md` za frontmatterom obsahuje samotné inštrukcie. Neexistujú žiadne formátovacie obmedzenia. Odporúčané sekcie:

- **Krok-za-krokom inštrukcie**
- **Príklady vstupov a výstupov**
- **Bežné edge case-y**
- **Gotchas** — konkrétne korekcie chýb, ktoré agent robí



## Praktické príklady

### Príklad 1: Roll Dice 🎲

Jeden z najjednoduchších skillov — agent hodí kockou pomocou terminálového príkazu.

**Umiestnenie:** `.agents/skills/roll-dice/SKILL.md`

```markdown

name: roll-dice
description: Roll dice using a random number generator. Use when asked to roll a die (d6, d20, etc.), roll dice, or generate a random dice roll.


To roll a die, use the following command that generates a random number from 1
to the given number of sides:

```bash
echo $((RANDOM % <sides> + 1))
```

```powershell
Get-Random -Minimum 1 -Maximum (<sides> + 1)
```

Replace `<sides>` with the number of sides on the die (e.g., 6 for a standard
die, 20 for a d20).
```

> **Použitie:** `"Roll a d20"` → agent spustí `echo $((RANDOM % 20 + 1))` → vráti číslo medzi 1 a 20.



### Príklad 2: Python Code Formatter 🐍

Skill, ktorý automaticky formátuje Python kód podľa štandardov projektu.

**Umiestnenie:** `.agents/skills/python-formatter/SKILL.md`

```markdown

name: python-formatter
description: Format Python code using ruff and black. Use when asked to format Python files, fix code style, or apply linting. Also triggered when the user mentions "format", "lint", or "PEP 8".


## Format Python code

1. Run ruff to check for issues:
   ```bash
   uvx ruff@0.8.0 check --fix .
   ```

2. Format with black:
   ```bash
   uvx black@24.10.0 .
   ```

3. If `uvx` is not available, fall back to:
   ```bash
   pipx run 'ruff==0.8.0' check --fix .
   pipx run 'black==24.10.0' .
   ```

## Gotchas

- Always run ruff before black
- If the file has syntax errors, ruff will fail — report them to the user
- Use `--check` flag without `--fix` if the user only wants to see issues without auto-fixing
```



### Príklad 3: CSV Data Analysis 📊

Skill na analýzu CSV súborov s vizualizáciou.

**Umiestnenie:** `.agents/skills/csv-analysis/SKILL.md`

```markdown

name: csv-analysis
description: Analyze CSV and tabular data files — compute summary statistics, add derived columns, generate charts, and clean messy data. Use when the user has a CSV, TSV, or Excel file and wants to explore, transform, or visualize data.
compatibility: Requires Python 3.10+ and uv


## Available scripts

- **`scripts/analyze.py`** — Compute summary statistics and generate charts
- **`scripts/clean.py`** — Clean and normalize messy data

## Workflow

1. **Explore the data:**
   ```bash
   python3 scripts/analyze.py --input "<file>" --summary
   ```

2. **Generate visualizations:**
   ```bash
   python3 scripts/analyze.py --input "<file>" --chart histogram --column "<column>"
   ```

3. **Clean messy data:**
   ```bash
   python3 scripts/clean.py --input "<file>" --output "<cleaned_file>"
   ```

## Output format

Present results in a markdown table with:
- Column name, type, non-null count, mean/min/max for numeric columns
- Top values and their frequencies for categorical columns
```

**Skript:** `.agents/skills/csv-analysis/scripts/analyze.py`

```python
# /// script
# dependencies = [
#   "pandas>=2.0",
#   "matplotlib>=3.7",
#   "seaborn>=0.12",
# ]
# ///

import argparse
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import json
import sys

def main():
    parser = argparse.ArgumentParser(description="Analyze CSV data")
    parser.add_argument("--input", required=True, help="Path to CSV file")
    parser.add_argument("--summary", action="store_true", help="Print summary statistics")
    parser.add_argument("--chart", choices=["histogram", "bar", "scatter"], help="Chart type")
    parser.add_argument("--column", help="Column name for chart")
    parser.add_argument("--x", help="X-axis column for scatter")
    parser.add_argument("--y", help="Y-axis column for scatter")

    args = parser.parse_args()

    try:
        df = pd.read_csv(args.input)
    except FileNotFoundError:
        print(f"Error: File '{args.input}' not found.", file=sys.stderr)
        sys.exit(1)
    except pd.errors.EmptyDataError:
        print(f"Error: File '{args.input}' is empty.", file=sys.stderr)
        sys.exit(1)

    if args.summary:
        summary = {
            "shape": list(df.shape),
            "columns": list(df.columns),
            "dtypes": {col: str(dtype) for col, dtype in df.dtypes.items()},
            "missing": df.isnull().sum().to_dict(),
            "numeric_summary": df.describe().to_dict()
        }
        print(json.dumps(summary, indent=2))

    if args.chart and args.column:
        if args.column not in df.columns:
            print(f"Error: Column '{args.column}' not found. Available: {list(df.columns)}", file=sys.stderr)
            sys.exit(1)

        plt.figure(figsize=(10, 6))
        numeric_cols = df.select_dtypes(include="number").columns

        if args.chart == "histogram" and args.column in numeric_cols:
            sns.histplot(df[args.column].dropna(), bins=30)
        elif args.chart == "bar":
            df[args.column].value_counts().head(20).plot(kind="bar")
        elif args.chart == "scatter":
            if args.x and args.y and args.x in numeric_cols and args.y in numeric_cols:
                sns.scatterplot(data=df, x=args.x, y=args.y)
            else:
                print("Error: --x and --y required for scatter plots, and must be numeric", file=sys.stderr)
                sys.exit(1)

        plt.title(f"{args.chart.title()} of {args.column}")
        plt.tight_layout()
        plt.savefig(f"chart_{args.column}.png", dpi=150)
        print(f"Chart saved to chart_{args.column}.png")


if __name__ == "__main__":
    main()
```

> **Použitie:** `"Analyze my sales.csv and show me a histogram of revenue"` → agent spustí skript, vygeneruje štatistiky a graf.



### Príklad 4: Database Query Helper 🗄️

Skill na bezpečné a konzistentné dotazovanie sa do databázy.

**Umiestnenie:** `.agents/skills/db-queries/SKILL.md`

```markdown

name: db-queries
description: Query the project database safely. Use when the user asks about data, needs to run SQL queries, or wants to explore the database schema.
compatibility: Requires psql (PostgreSQL client) and database credentials in .env


## Database schema

See [references/SCHEMA.md](references/SCHEMA.md) for the full schema reference.

## Query rules

1. **Always use parameterized queries** — never concatenate user input into SQL
2. **Always add LIMIT** — default to 100 rows unless the user specifies more
3. **Never run destructive queries** — INSERT, UPDATE, DELETE require explicit user confirmation

## Gotchas

- The `users` table uses soft deletes. Queries must include `WHERE deleted_at IS NULL`
- The user ID is `user_id` in the database, `uid` in the auth service, and `accountId` in the billing API
- The `/health` endpoint returns 200 even if DB is down — use `/ready` for full health check

## Workflow

```bash
psql "$DATABASE_URL" -c "SELECT id, email, created_at FROM users WHERE deleted_at IS NULL LIMIT 10;"
```
```

**Referencia:** `.agents/skills/db-queries/references/SCHEMA.md`

```markdown
# Database Schema

## `users`
| Column | Type | Notes |
|--||-|
| id | UUID | Primary key |
| email | VARCHAR(255) | Unique, not null |
| deleted_at | TIMESTAMP | NULL = active, set = soft-deleted |
| created_at | TIMESTAMP | Default NOW() |

## `orders`
| Column | Type | Notes |
|--||-|
| id | UUID | Primary key |
| user_id | UUID | FK → users.id |
| total | DECIMAL(10,2) | |
| status | VARCHAR(50) | pending, confirmed, shipped, delivered, cancelled |
```



### Príklad 5: Git Commit Message Generator 📝

Skill, ktorý analyzuje zmeny a generuje konzistentné commit správy podľa Conventional Commits.

**Umiestnenie:** `.agents/skills/git-commit/SKILL.md`

```markdown

name: git-commit
description: Generate conventional Git commit messages from staged changes. Use when asked to commit, create a commit message, or stage and commit changes.
compatibility: Requires git


## Workflow

1. Check the current state:
   ```bash
   git status --short
   ```

2. Review staged changes:
   ```bash
   git diff --cached --stat
   ```

3. Generate a commit message using this template:
   ```
   <type>(<scope>): <short summary>

   <body>
   ```

   **Types:** feat, fix, refactor, test, docs, chore, style, perf, ci
   **Scope:** Optional — the module or component affected
   **Summary:** Max 72 characters, imperative mood, no period

4. Commit:
   ```bash
   git commit -m "<message>"
   ```

## Examples

```
feat(auth): add OAuth2 login with Google provider

Implement Google OAuth2 flow with passport.js.
Includes token refresh and session management.
```

```
fix(api): handle null response in user lookup

Return 404 instead of crashing when user ID doesn't exist.
```

## Gotchas

- If nothing is staged, suggest `git add -p` for interactive staging
- Breaking changes get a `!` after the type: `feat!(api): remove deprecated v1 endpoints`
```



### Príklad 6: Code Review Assistant 🔍

Skill na štruktúrovanú kontrolu kódu s dôrazom na bezpečnosť a kvalitu.

**Umiestnenie:** `.agents/skills/code-review/SKILL.md`

```markdown

name: code-review
description: Perform structured code review of pull requests and code changes. Use when asked to review code, check a PR, audit changes, or look for bugs and security issues.


## Code Review Checklist

### Security
- [ ] Check all database queries for SQL injection (use parameterized queries)
- [ ] Verify authentication checks on every endpoint
- [ ] Confirm error messages don't leak internal details
- [ ] Check for hardcoded secrets, API keys, or passwords

### Correctness
- [ ] Look for race conditions in concurrent code paths
- [ ] Verify edge cases: empty inputs, null values, boundary conditions
- [ ] Check error handling — are errors caught, logged, and handled?
- [ ] Validate type consistency across function boundaries

### Maintainability
- [ ] Are functions and variables named clearly?
- [ ] Is there duplicated code that should be extracted?
- [ ] Are there TODO/FIXME comments that need attention?
- [ ] Is the code consistent with the project's style guide?

## Output Format

```markdown
## Review of [file/PR name]

### Issues

1. **Severity: High** — Description of critical issue
   - Location: `file.py:42`
   - Suggestion: How to fix it

2. **Severity: Medium** — Description
   - Location: `file.py:87`
   - Suggestion: How to fix it

### Summary
[Overall assessment and recommendations]
```
```



### Príklad 7: Docker Compose Development Environment 🐳

Skill na rýchle spustenie vývojového prostredia s Dockerom.

**Umiestnenie:** `.agents/skills/docker-dev/SKILL.md`

```markdown

name: docker-dev
description: Set up and manage Docker Compose development environments. Use when asked to start a dev environment, run services locally, or troubleshoot Docker containers.
compatibility: Requires docker and docker-compose


## Available scripts

- **`scripts/start-dev.sh`** — Start the development environment
- **`scripts/reset-db.sh`** — Reset the database to a clean state

## Workflow

1. Start the dev environment:
   ```bash
   bash scripts/start-dev.sh
   ```

2. Check running services:
   ```bash
   docker compose ps
   ```

3. View logs for a specific service:
   ```bash
   docker compose logs --tail=50 <service_name>
   ```

4. Reset if something goes wrong:
   ```bash
   bash scripts/reset-db.sh
   ```

## Gotchas

- Port 3000, 5432, and 6379 must be free — check with `lsof -i :PORT`
- First startup pulls images and can take 2-5 minutes
- If containers fail to start, check `docker compose logs` before retrying
```



## Best Practices

### 1. Vychádzajte z reálnej expertízy

Nežiadajte LLM, aby vygeneroval skill bez doménového kontextu — výsledok bude príliš všeobecný. Namiesto toho:

- **Extrahujte z reálnej úlohy** — dokončite úlohu s agentom, potom extrahujte opakovateľný pattern
- **Syntetizujte z existujúcich artefaktov** — interná dokumentácia, runbooky, API špecifikácie, code review komentáre

### 2. Minimalizujte záťaž kontextu

Každý token v `SKILL.md` súťaží o pozornosť agenta s celým kontextovým oknom.

- **Pridajte to, čo agentovi chýba, vynechajte to, čo vie** — nemusíte vysvetľovať čo je PDF alebo ako funguje HTTP
- **Navrhujte koherentné celky** — skill by mal pokrývať jednu ucelenú oblasť
- **Mierte na primeranú úroveň detailov** — príliš komplexné skilly škodia viac než pomáhajú

### 3. Kalibrujte mieru kontroly

| Situácia | Prístup |
|-||
| Viacero platných prístupov | Dajte agentovi voľnosť, vysvetlite **prečo** |
| Krehké operácie | Buďte preskriptívni — presný príkaz, žiadne voľby |
| Výber nástroja | Uveďte predvolený, alternatívy len okrajovo |

### 4. Vzory pre efektívne inštrukcie

| Vzor | Použitie |
||-|
| **Gotchas** | Konkrétne korekcie chýb, ktoré agent opakovane robí |
| **Šablóny výstupu** | Konkrétna štruktúra výstupu je spoľahlivejšia než prozaický popis |
| **Checklisty** | Pomáhajú agentovi sledovať postup a nepreskakovať kroky |
| **Validačné slučky** | Urob → validuj → oprav → opakuj, kým neprejde |
| **Plán-validuj-vykonaj** | Pre dávkové alebo deštruktívne operácie vytvorte medziplán, validujte ho, až potom vykonajte |

### 5. Iteratívne vylepšovanie

Prvý návrh skilly zvyčajne potrebuje doladiť:

1. Spustite skill na reálnych úlohách
2. Analyzujte výsledky (nielen neúspechy)
3. Opravte inštrukcie podľa toho, čo ste sa naučili
4. Opakujte

> 💡 Keď agent urobí chybu, ktorú musíte opraviť, pridajte opravu do sekcie **Gotchas**.



## Používanie skriptov

### One-off príkazy

Pre jednoduché operácie nie je potrebný `scripts/` priečinok — stačí referencia v `SKILL.md`:

```bash
# Python (uvx)
uvx ruff@0.8.0 check --fix .

# Python (pipx)
pipx run 'black==24.10.0' .

# Node.js (npx)
npx eslint@9 --fix .

# Go
go run golang.org/x/tools/cmd/goimports@v0.28.0 .
```

### Self-contained skripty

Pre zložitejšiu logiku použite **PEP 723** inline dependencies:

```python
# /// script
# dependencies = [
#   "beautifulsoup4>=4.12",
#   "requests>=2.31",
# ]
# ///

import requests
from bs4 import BeautifulSoup

response = requests.get("https://example.com")
soup = BeautifulSoup(response.text, "html.parser")
print(soup.title.text)
```

Spustenie: `uv run scripts/scrape.py`

### Design skriptov pre agentov

| Pravidlo | Prečo? |
|-|--|
| ❌ Žiadne interaktívne výzvy | Agenti pracujú v neinteraktívnom shelli |
| ✅ `--help` dokumentácia | Primárny spôsob, ako sa agent naučí rozhranie |
| ✅ Užitočné chybové hlášky | "Error: --format must be one of: json, csv, table" |
| ✅ Štruktúrovaný výstup (JSON) | Dá sa ďalej spracovávať (`jq`, `cut`) |
| ✅ Idempotencia | Agenti môžu príkazy opakovať |
| ✅ Dry-run podpora | Pre deštruktívne operácie |
| ✅ Predvídateľná veľkosť výstupu | Agenti automaticky orezávajú veľký výstup |



## Optimalizácia popisov

Popis (`description`) je **jediný mechanizmus**, ktorým agent rozhoduje, či skill aktivovať.

### Zásady písania popisov

- **Imperatívne frázovanie**: "Use this skill when..." namiesto "This skill does..."
- **Zamerajte sa na zámer užívateľa**, nie na implementáciu
- **Buďte mierne agresívni**: explicitne vymenujte kontexty, kde skill platí
- **Stručnosť**: pár viet až krátky odsek (max 1024 znakov)

### Príklad zlepšenia popisu

```yaml
# Before
description: Process CSV files.

# After
description: >
  Analyze CSV and tabular data files — compute summary statistics,
  add derived columns, generate charts, and clean messy data. Use this
  skill when the user has a CSV, TSV, or Excel file and wants to
  explore, transform, or visualize the data, even if they don't
  explicitly mention "CSV" or "analysis."
```

### Testovanie triggerovania

1. Vytvorte eval sadu ~20 dotazov (8-10 trigger, 8-10 not-trigger)
2. Každý dotaz spustite 3× a vypočítajte **trigger rate**
3. Optimalizačný loop: vyhodnoť → identifikuj zlyhania → reviduj popis → opakuj (max 5 iterácií)
4. Použite **train/validation split** (60/40) aby ste predišli overfittingu



## Klientská podpora

Agent Skills sú podporované širokým spektrom nástrojov:

| Nástroj | Odkaz |
||-|
| **GitHub Copilot** (VS Code) | [docs.github.com](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) |
| **Claude Code** | [code.claude.com](https://code.claude.com/docs/en/skills) |
| **OpenAI Codex** | [developers.openai.com](https://developers.openai.com/codex/skills/) |
| **Cursor** | [cursor.com](https://cursor.com/docs/context/skills) |
| **VS Code** | [code.visualstudio.com](https://code.visualstudio.com/docs/copilot/customization/agent-skills) |
| **Gemini CLI** | [geminicli.com](https://geminicli.com/docs/cli/skills/) |
| **Cline / Roo Code** | [roocode.com](https://docs.roocode.com/features/skills) |
| **Windsurf** | [codeium.com](https://codeium.com/windsurf) |
| **Junie** (JetBrains) | [junie.jetbrains.com](https://junie.jetbrains.com/docs/agent-skills.html) |
| **Goose** | [block.github.io](https://block.github.io/goose/docs/guides/context-engineering/using-skills/) |
| **OpenHands** | [docs.openhands.dev](https://docs.openhands.dev/overview/skills) |
| **Qodo** | [qodo.ai](https://www.qodo.ai/) |
| **Tabnine** | [docs.tabnine.com](https://docs.tabnine.com/main/getting-started/tabnine-cli/features/agent-skills) |



## VS Code Skills — workspace skills

Táto sekcia obsahuje praktické skills pripravené na **okamžité použitie vo VS Code**. Stačí vytvoriť priečinok s `SKILL.md` na správnom mieste a skill je automaticky dostupný.

### Umiestnenie skillov vo VS Code

VS Code hľadá skills v nasledujúcich priečinkoch (relatívne voči koreňu workspace):

| Priečinok | Typ |
|--|--|
| `.github/skills/` | Projektový (odporúčané pre zdieľanie v repozitári) |
| `.claude/skills/` | Projektový (kompatibilné s Claude Code) |
| `.agents/skills/` | Projektový (univerzálne) |
| `~/.copilot/skills/` | Osobný (platí pre všetky projekty) |

Vlastné umiestnenie môžeš nastaviť cez `chat.agentSkillsLocations` v nastaveniach VS Code.

> **Tip:** Po vytvorení skillu ho otestuj príkazom `/skills` v Copilot chat paneli — mal by sa zobraziť v zozname.



### 🎲 Skill: Náhodné dáta (`random-data`)

Generovanie náhodných dát — používateľské mená, emaily, ID, heslá, čísla, dátumy a pod.

**Umiestnenie:** `.github/skills/random-data/SKILL.md`

```markdown

name: random-data
description: Generate random test data — usernames, emails, passwords, IDs, dates, phone numbers, addresses, and dummy content. Use when asked to generate fake data, mock data, test data, random records, or dummy content for development and testing.


## Generate random data

Use Python with `faker` to generate realistic random data. Run the script with the appropriate arguments.

```bash
uv run scripts/generate.py --type <data_type> --count <number>
```

Supported `--type` values:
- `users` — name, email, username, phone, address
- `passwords` — random secure passwords
- `dates` — random dates in a range
- `ids` — UUIDs and numeric IDs
- `mixed` — a combination of all types

### Examples

```bash
# Generate 10 fake users
uv run scripts/generate.py --type users --count 10

# Generate 5 random passwords
uv run scripts/generate.py --type passwords --count 5

# Generate 20 random dates in 2025
uv run scripts/generate.py --type dates --count 20 --year 2025
```

## Script

`scripts/generate.py` uses PEP 723 inline dependencies with `faker`.
```

**Skript:** `.github/skills/random-data/scripts/generate.py`

```python
# /// script
# dependencies = [
#   "faker>=22.0",
# ]
# ///

import argparse
import json
import sys
from datetime import datetime, timedelta
from uuid import uuid4

def main():
    parser = argparse.ArgumentParser(description="Generate random test data")
    parser.add_argument("--type", choices=["users", "passwords", "dates", "ids", "mixed"], required=True)
    parser.add_argument("--count", type=int, default=5)
    args = parser.parse_args()

    if args.count < 1:
        print("Error: --count must be >= 1", file=sys.stderr)
        sys.exit(1)

    from faker import Faker
    fake = Faker()

    results = []
    for _ in range(args.count):
        if args.type == "users":
            results.append({
                "name": fake.name(),
                "email": fake.email(),
                "username": fake.user_name(),
                "phone": fake.phone_number(),
                "address": fake.address().replace("\n", ", "),
            })
        elif args.type == "passwords":
            results.append({
                "password": fake.password(length=16, special_chars=True, digits=True, upper_case=True, lower_case=True),
            })
        elif args.type == "dates":
            results.append({
                "date": fake.date_between(start_date="-1y", end_date="today").isoformat(),
            })
        elif args.type == "ids":
            results.append({
                "uuid": str(uuid4()),
                "numeric_id": fake.random_int(min=1000, max=99999),
            })
        elif args.type == "mixed":
            results.append({
                "id": str(uuid4()),
                "name": fake.name(),
                "email": fake.email(),
                "created_at": fake.date_time_this_year().isoformat(),
                "score": fake.random_int(min=0, max=100),
            })

    print(json.dumps(results, indent=2))

if __name__ == "__main__":
    main()
```

> **Použitie:** `"Generate 10 fake users for testing"` → agent spustí skript a vráti JSON s 10 používateľmi.



### 🔤 Skill: Lingvistická analýza (`text-analysis`)

Analýza textu — počet slov, viet, znakov, frekvenčná analýza, sentiment, detekcia jazyka, kľúčové slová.

**Umiestnenie:** `.github/skills/text-analysis/SKILL.md`

```markdown

name: text-analysis
description: Analyze text — count words, sentences, characters, detect language, extract keywords, analyze sentiment and readability. Use when asked to analyze text, check readability, count words, detect language, or perform linguistic analysis.


## Text analysis

Use the bundled Python script for comprehensive text analysis.

```bash
uv run scripts/analyze_text.py --text "<text>"
```

Or read from a file:
```bash
uv run scripts/analyze_text.py --file "<path>"
```

## What the script analyzes

| Metric | Description |
|--|-|
| Word count | Total words + unique words |
| Character count | With and without spaces |
| Sentence count | Number of sentences |
| Average word length | Mean characters per word |
| Average sentence length | Mean words per sentence |
| Language | Detected language (ISO code) |
| Sentiment | Positive/negative/neutral score |
| Top keywords | Most frequent meaningful words |
| Readability | Flesch reading ease score |

**Skript:** `.github/skills/text-analysis/scripts/analyze_text.py`

```python
# /// script
# dependencies = [
#   "textblob>=0.17",
#   "langdetect>=1.0",
# ]
# ///

import argparse
import json
import re
import sys
from collections import Counter

def main():
    parser = argparse.ArgumentParser(description="Analyze text linguistically")
    parser.add_argument("--text", help="Text to analyze")
    parser.add_argument("--file", help="File to analyze")
    args = parser.parse_args()

    if args.file:
        try:
            with open(args.file, "r", encoding="utf-8") as f:
                text = f.read()
        except FileNotFoundError:
            print(f"Error: File '{args.file}' not found.", file=sys.stderr)
            sys.exit(1)
    elif args.text:
        text = args.text
    else:
        print("Error: Either --text or --file is required.", file=sys.stderr)
        sys.exit(1)

    if not text.strip():
        print("Error: Text is empty.", file=sys.stderr)
        sys.exit(1)

    # Basic stats
    words = re.findall(r"\b\w+\b", text.lower())
    sentences = re.split(r"[.!?]+", text)
    sentences = [s.strip() for s in sentences if s.strip()]
    chars_total = len(text)
    chars_no_spaces = len(text.replace(" ", "").replace("\n", ""))

    result = {
        "word_count": len(words),
        "unique_words": len(set(words)),
        "character_count": chars_total,
        "character_count_no_spaces": chars_no_spaces,
        "sentence_count": len(sentences),
        "avg_word_length": round(sum(len(w) for w in words) / len(words), 2) if words else 0,
        "avg_sentence_length": round(len(words) / len(sentences), 2) if sentences else 0,
    }

    # Top keywords (skip stopwords-like short words)
    stopwords = {"the", "a", "an", "is", "are", "was", "were", "be", "been",
                 "being", "have", "has", "had", "do", "does", "did", "will",
                 "would", "could", "should", "may", "might", "shall", "can",
                 "to", "of", "in", "for", "on", "with", "at", "by", "from",
                 "as", "into", "through", "during", "before", "after", "above",
                 "below", "between", "out", "off", "over", "under", "again",
                 "further", "then", "once", "here", "there", "when", "where",
                 "why", "how", "all", "each", "every", "both", "few", "more",
                 "most", "other", "some", "such", "no", "nor", "not", "only",
                 "own", "same", "so", "than", "too", "very", "just", "because",
                 "and", "but", "or", "if", "while", "that", "this", "these",
                 "those", "it", "its", "i", "me", "my", "we", "you", "he",
                 "she", "they", "them", "his", "her", "their", "our", "your"}

    keyword_counts = Counter(w for w in words if w not in stopwords and len(w) > 2)
    result["top_keywords"] = keyword_counts.most_common(15)

    # Sentiment analysis
    try:
        from textblob import TextBlob
        blob = TextBlob(text)
        result["sentiment"] = {
            "polarity": round(blob.sentiment.polarity, 3),
            "subjectivity": round(blob.sentiment.subjectivity, 3),
            "label": "positive" if blob.sentiment.polarity > 0.1 else "negative" if blob.sentiment.polarity < -0.1 else "neutral"
        }
    except ImportError:
        result["sentiment"] = "textblob not available"

    # Language detection
    try:
        from langdetect import detect
        result["language"] = detect(text)
    except ImportError:
        result["language"] = "langdetect not available"
    except Exception:
        result["language"] = "could not detect"

    # Readability (Flesch Reading Ease approximation)
    if sentences and words:
        syllables = sum(_count_syllables(w) for w in words)
        result["readability"] = {
            "flesch_reading_ease": round(206.835 - 1.015 * (len(words) / len(sentences)) - 84.6 * (syllables / len(words)), 2),
            "note": "Higher = easier to read. 60-70 = plain English."
        }

    print(json.dumps(result, indent=2, ensure_ascii=False))


def _count_syllables(word):
    word = word.lower()
    count = 0
    vowels = "aeiouy"
    if word and word[0] in vowels:
        count += 1
    for i in range(1, len(word)):
        if word[i] in vowels and word[i - 1] not in vowels:
            count += 1
    if word.endswith("e"):
        count -= 1
    if word.endswith("le") and len(word) > 2 and word[-3] not in vowels:
        count += 1
    return max(1, count)


if __name__ == "__main__":
    main()
```

> **Použitie:** `"Analyze this text: 'The quick brown fox jumps over the lazy dog.'"` → agent vráti komplexnú lingvistickú analýzu.


### 🌤️ Skill: Počasie (`weather`)

Zistenie aktuálneho počasia pre zadané mesto pomocou verejného API.

**Umiestnenie:** `.github/skills/weather/SKILL.md`

```markdown

name: weather
description: Get current weather, temperature, humidity, wind speed, and forecast for any city using the wttr.in API. Use when asked about the weather, temperature, forecast, or climate in a specific location.
compatibility: Requires internet access. Uses the free wttr.in API (no API key needed).


## Get weather

Use curl to fetch weather data from wttr.in:

```bash
# Current weather (compact)
curl -s "wttr.in/<city>?format=%C+%t+%h+%w"

# Detailed weather
curl -s "wttr.in/<city>?format=%l:+%C,+%t( feels+like+%f),+humidity+%h,+wind+%w"

# Full 3-day forecast
curl -s "wttr.in/<city>?u&0"
```

Replace `<city>` with the city name (e.g., `London`, `Bratislava`, `New+York`, `Tokyo`).

## Parameters

| Flag | Meaning |
| `?u` | Metric units (default) |
| `?m` | Metric (m/s) |
| `?format=` | Custom output format |
| `&0` | Silent mode (no ASCII art) |

## Format placeholders

- `%C` — Weather condition (e.g., "Clear", "Cloudy", "Rain")
- `%t` — Temperature in °C
- `%f` — Feels like temperature
- `%h` — Humidity percentage
- `%w` — Wind speed
- `%l` — Location name
- `%p` — Precipitation

## Examples

### Current weather in Bratislava
```bash
curl -s "wttr.in/Bratislava?format=%l:+%C,+%t+(feels+like+%f),+humidity+%h,+wind+%w"
```

### 3-day forecast
```bash
curl -s "wttr.in/Bratislava?u&0"
```

## Gotchas

- City names with spaces use `+`: `New+York`, `Los+Angeles`, `Buenos+Aires`
- If the city is not found, wttr.in returns "Unknown location"
- wttr.in rate-limits excessive requests — cache results when possible
- If the user doesn't specify a city, ask for one
```

> **Použitie:** `"What's the weather in Tokyo?"` → agent zavolá `curl -s "wttr.in/Tokyo?format=..."` a vráti aktuálne počasie.



### 🕐 Skill: Čas vo svete (`world-time`)

Zistenie aktuálneho času pre vybrané mesto alebo časovú zónu.

**Umiestnenie:** `.github/skills/world-time/SKILL.md`

```markdown

name: world-time
description: Get the current date and time for any city or timezone worldwide. Use when asked about the time in a specific location, timezone differences, or what time it is somewhere.
compatibility: Requires internet access. Uses the free Time API (worldtimeapi.org) and fallback to timeapi.io.


## Get current time

Use curl to fetch the current time from a public time API:

```bash
# By timezone
curl -s "https://worldtimeapi.org/api/timezone/<timezone>"

# Search by city
curl -s "https://worldtimeapi.org/api/timezone/<continent>/<city>"
```

## Common timezones

| City | Timezone |
||-|
| Bratislava, Prague, Vienna, Berlin, Paris, Madrid, Rome, Stockholm | `Europe/<city>` |
| London, Lisbon, Dublin | `Europe/<city>` |
| New York, Washington, Boston, Miami, Toronto | `America/New_York` |
| Los Angeles, San Francisco, Vancouver, Seattle | `America/Los_Angeles` |
| Tokyo, Seoul | `Asia/Tokyo` |
| Sydney, Melbourne | `Australia/Sydney` |
| Auckland | `Pacific/Auckland` |
| Dubai | `Asia/Dubai` |
| Moscow | `Europe/Moscow` |
| São Paulo | `America/Sao_Paulo` |
| Mexico City | `America/Mexico_City` |

## Examples

```bash
# Time in Bratislava
curl -s "https://worldtimeapi.org/api/timezone/Europe/Bratislava" | python3 -c "import sys,json; d=json.load(sys.stdin); print(f'{d[\"datetime\"]} ({d[\"timezone\"]})')"

# Time in Tokyo
curl -s "https://worldtimeapi.org/api/timezone/Asia/Tokyo" | python3 -c "import sys,json; d=json.load(sys.stdin); print(f'Tokyo: {d[\"datetime\"][:19]} ({d[\"abbreviation\"]})')"
```

## Fallback

If worldtimeapi.org is unreachable, try the alternative API:
```bash
curl -s "https://timeapi.io/api/Time/current/zone?timeZone=Europe/Bratislava"
```

## Gotchas

- Continent and city names are case-sensitive: `Europe/Bratislava` (not `europe/bratislava`)
- Use common timezone names (find them with `timedatectl list-timezones` or check the table above)
- If the timezone is ambiguous, offer the user options
- The API returns ISO 8601 datetime — format it nicely for the user
```

> **Použitie:** `"What time is it in Sydney?"` → agent zavolá API a vráti aktuálny čas aj s časovou zónou.



## Komunitné zdroje

- **GitHub repozitár**: [github.com/agentskills/agentskills](https://github.com/agentskills/agentskills)
- **Discord komunita**: [discord.gg/MKPE9g8aUy](https://discord.gg/MKPE9g8aUy)
- **Príklady skillov**: [github.com/anthropics/skills](https://github.com/anthropics/skills)
- **Validačný nástroj**: `skills-ref validate ./my-skill`



## Quickstart — vytvorte si prvý skill

```bash
# 1. Vytvorte priečinok
mkdir -p .agents/skills/roll-dice

# 2. Vytvorte SKILL.md s obsahom z Príkladu 1 vyššie
cat > .agents/skills/roll-dice/SKILL.md << 'EOF'

name: roll-dice
description: Roll dice using a random number generator.


To roll a die, use:
```bash
echo $((RANDOM % <sides> + 1))
```
EOF

# 3. Overte, že skill je načítaný
#    V Copilot chate napíšte /skills — mal by sa zobraziť roll-dice

# 4. Otestujte: "Roll a d20"
```

> **Validácia:** `skills-ref validate .agents/skills/roll-dice` skontroluje, či je frontmatter v poriadku.



*Dokument vytvorený na základe [https://agentskills.io](https://agentskills.io) — otvoreného štandardu pre rozširovanie schopností AI agentov.*

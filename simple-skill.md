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

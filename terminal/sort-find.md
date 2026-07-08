# Příkazy `find` a `sort` ve Windows CMD

Podrobný průvodce s příklady použití.

## 1. Příkaz `find` — vyhledávání textu v souborech

Příkaz `find` prohledává soubory nebo vstup a vypisuje řádky obsahující zadaný text.

### Syntaxe

```cmd
find [přepínače] "hledaný_text" [cesta_k_souboru]
```

### Přepínače

| Přepínač | Význam |
|----------|--------|
| `/v` | Vypíše řádky, které **neobsahují** hledaný text |
| `/c` | Vypíše pouze **počet** řádků, které text obsahují |
| `/n` | Vypíše čísla řádků |
| `/i` | Ignoruje velikost písmen (**case-insensitive**) |
| `/off[line]` | Nevynechá soubory s nastaveným offline atributem |

### Příklady použití

#### Základní vyhledávání

```cmd
REM Vyhledání textu v souboru
find "ERROR" log.txt

REM S ignorováním velikosti písmen
find /i "error" log.txt

REM S čísly řádků
find /n "Warning" log.txt
```

#### Výstup: `find /n "Warning" log.txt`
```
[5] WARNING: Disk space low
[12] Warning: Timeout detected
[27] WARNING: Connection lost
```

#### Inverzní vyhledávání (řádky **bez** textu)

```cmd
REM Všechny řádky, které neobsahují "INFO"
find /v "INFO" log.txt

REM Odstranění prázdných řádků (řádky neobsahující "")
find /v "" soubor.txt
```

#### Počítání výskytů

```cmd
REM Kolik řádků obsahuje "FAILED"
find /c "FAILED" log.txt
```

Výstup:
```
---------- LOG.TXT: 14
```
(14 řádků obsahuje "FAILED")

#### Kombinace přepínačů

```cmd
REM Počet řádků BEZ "ERROR" (case-insensitive)
find /c /i /v "ERROR" log.txt

REM Řádky neobsahující "DEBUG" s čísly řádků
find /v /n "DEBUG" log.txt
```

#### Použití s pipe (`|`)

```cmd
REM Vyhledání pouze složek (ne souborů)
dir /b | find /i "<DIR>"

REM Najít běžící proces Notepad
tasklist | find /i "notepad"

REM Najít IP adresu v ipconfig
ipconfig | find /i "IPv4"

REM Výpis souborů .txt v aktuálním adresáři
dir /b | find /i ".txt"

REM Najít služby (sc query) obsahující "SQL"
sc query | find /i "SQL"
```

#### Hledání ve více souborech

```cmd
REM Hledání ve všech .log souborech
find /i "error" *.log

REM Hledání v konkrétních souborech
find /i "TODO" *.py *.js *.ts

REM Rekurzivní hledání pomocí dir + find
dir /s /b *.py | find /i "TODO"
```

#### Přesměrování výstupu

```cmd
REM Uložit výsledky do souboru
find /i "ERROR" log.txt > chyby.txt

REM Přidat výsledky na konec souboru
find /i "ERROR" log.txt >> chyby.txt

REM Přesměrovat chybový výstup (pokud soubor neexistuje)
find "text" neexistuje.txt 2> chyba.txt
```

### Návratové kódy `find`

| Kód | Význam |
|-----|--------|
| `0` | Hledaný text byl nalezen |
| `1` | Hledaný text nebyl nalezen |
| `2` | Chybný přepínač nebo soubor nelze otevřít |

Příklad využití v dávkovém skriptu:

```batch
find /i "ERROR" log.txt >nul
if %errorlevel% equ 0 (
    echo Chyby nalezeny!
) else (
    echo Žádné chyby.
)
```

### Omezení `find`

- **Neumí regulární výrazy** — k tomu slouží `findstr`
- Hledá jen **přesný řetězec** (s přepínačem `/i` case-insensitive)
- Neumí vyhledávat rekurzivně — nutno kombinovat s `dir /s`
- Text musí být v **uvozovkách**

### Porovnání: `find` vs `findstr`

| Vlastnost | `find` | `findstr` |
|-----------|--------|-----------|
| Regulární výrazy | ❌ Ne | ✅ Ano |
| Case-insensitive | ✅ `/i` | ✅ `/i` |
| Počítání řádků | ✅ `/c` | ❌ (nutno jinak) |
| Čísla řádků | ✅ `/n` | ✅ `/n` |
| Hledání ve více souborech | ✅ | ✅ |
| Rekurzivní hledání | ❌ | ✅ `/s` |
| Celá slova | ❌ | ✅ `\<slovo\>` |
| Rychlost | Rychlejší | Pomalejší |

---

## 2. Příkaz `sort` — řazení textu

Příkaz `sort` řadí textový vstup (ze souboru nebo pipe) a vypisuje ho abecedně seřazený.

### Syntaxe

```cmd
sort [přepínače] [cesta_k_souboru]
```

### Přepínače

| Přepínač | Význam |
|----------|--------|
| `/r` | Řadí **sestupně** (reverse) — od Z do A |
| `/+n` | Řadí podle sloupce začínajícího na pozici `n` (1-indexované) |
| `/o [výstup]` | Zapíše výsledek do souboru (lze i přes `>`) |

### Příklady použití

#### Základní řazení

```cmd
REM Seřadí obsah souboru vzestupně (A→Z)
REM Vytvořme nejprve ukázkový soubor
echo C:\Users> sort "seznam.txt"

REM Místo toho s přesměrováním:
REM (pokud soubor neexistuje, použijeme type s pipe)
sort < seznam.txt
```

Příklad — mějme soubor `ovoce.txt`:
```
jablko
hruška
banán
třešeň
meruňka
pomeranč
```

```cmd
sort ovoce.txt
```

Výstup:
```
banán
hruška
jablko
meruňka
pomeranč
třešeň
```

#### Sestupné řazení

```cmd
sort /r ovoce.txt
```

Výstup:
```
třešeň
pomeranč
meruňka
jablko
hruška
banán
```

#### Řazení podle konkrétního sloupce

```cmd
REM Mějme soubor zamestnanci.txt:
REM 5  Petr     Manager
REM 2  Jana     Designer
REM 9  Karel    Developer
REM 1  Eva      Tester

REM Řazení podle druhého sloupce (pozice 1+ = sloupec 2)
sort /+2 zamestnanci.txt
```

Výstup (řazeno podle jména od pozice 2):
```
1  Eva      Tester
2  Jana     Designer
9  Karel    Developer
5  Petr     Manager
```

#### Uložení seřazeného výstupu

```cmd
REM Pomocí přepínače /o
sort ovoce.txt /o serazene_ovoce.txt

REM Nebo pomocí přesměrování
sort ovoce.txt > serazene_ovoce.txt
```

#### Použití s pipe (`|`)

```cmd
REM Seřadit výpis adresáře
dir /b | sort

REM Seřadit výpis adresáře sestupně
dir /b | sort /r

REM Seřadit běžící procesy podle názvu
tasklist | sort

REM Seřadit podle PID (čtvrtý slouček přibližně)
tasklist | sort /+30

REM Seřadit IP adresy (jen ukázka — lepší příklad níže)
ipconfig | find /i "IPv4" | sort
```

#### Kombinace `find` a `sort`

```cmd
REM Najít řádky s "ERROR" a seřadit je
find /i "ERROR" log.txt | sort

REM Najít všechny .txt soubory a seřadit podle velikosti
dir *.txt | sort

REM Počítadlo: najít, seřadit, spočítat unikátní výskyty
find /i "ERROR" log.txt | sort | find /v ""
```

#### Pokročilý příklad — četnost výskytů

```batch
@echo off
REM Spočítá četnost jednotlivých chyb v logu
find /i "ERROR" log.txt > chyby.txt
REM Každou chybu dáme na samostatný řádek, seřadíme
(for /f "tokens=*" %%a in (chyby.txt) do echo %%a) | sort
```

#### Příklady s číselnými daty

Mějme soubor `cisla.txt`:
```
42
3
128
55
7
99
```

```cmd
REM Pozor! sort řadí textově (lexikograficky), ne numericky!
sort cisla.txt
```

Výstup (textové řazení — 128 < 3 < 42 < 55 < 7 < 99):
```
128
3
42
55
7
99
```

> **Poznámka:** CMD `sort` vždy řadí **textově**, nikoliv numericky. Pro numerické řazení
> použijte PowerShell: `Get-Content cisla.txt | Sort-Object {[int]$_}`.

### Chování `sort` — důležité detaily

1. **Řazení podle národního prostředí** — `sort` respektuje systémové locale (třídění s diakritikou)
2. **Velikost písmen** — standardně se nerozlišuje (A = a)
3. **Prázdné řádky** — jsou přesunuty na začátek (vzestupně) nebo na konec (sestupně)
4. **Maximální velikost vstupu** — není prakticky omezena

---

## 3. Praktické příklady — `find` + `sort` v akci

### Analýza logovacího souboru

```batch
@echo off
echo === Analyza logu ===

REM 1. Kolik chyb celkem?
find /c /i "ERROR" server.log
echo.

REM 2. Unikátní chybové zprávy (přes find + sort dočasně)
find /i "ERROR" server.log > temp.txt
sort < temp.txt > temp2.txt
echo Unikatni chyby:, temp2.txt
del temp.txt temp2.txt

REM 3. 5 nejcastejsich chyb
REM (zjednodusena ukazka)
find /i "ERROR" server.log | sort
```

### Výpis 10 největších souborů

```cmd
dir /a-d /os | sort /r
```

(Seřadí soubory od největšího po nejmenší.)

### Monitorování procesů

```cmd
REM Pravidelné sledování procesů (stiskni Ctrl+C pro ukončení)
:loop
cls
tasklist | sort
timeout /t 2 >nul
goto loop
```

### Hledání duplicitních řádků

```cmd
REM Najít duplicitní řádky v souboru
sort soubor.txt | findstr /n "^" | findstr /v "stejný"
```

(Ukázkový koncept — přesná detekce duplicit vyžaduje pokročilejší nástroje.)

---

## 4. Shrnutí — rychlá referencia

### `find`

| Účel | Příkaz |
|------|--------|
| Hledat "text" v souboru | `find "text" soubor.txt` |
| Case-insensitive hledání | `find /i "text" soubor.txt` |
| Řádky bez textu | `find /v "text" soubor.txt` |
| Počet řádků s textem | `find /c "text" soubor.txt` |
| S čísly řádků | `find /n "text" soubor.txt` |
| Hledat ve všech *.log | `find /i "chyba" *.log` |
| Hledat ve výstupu příkazu | `dir \| find /i ".py"` |
| Kombinace všeho | `find /c /i /v "DEBUG" log.txt` |

### `sort`

| Účel | Příkaz |
|------|--------|
| Seřadit soubor (A→Z) | `sort soubor.txt` |
| Seřadit sestupně (Z→A) | `sort /r soubor.txt` |
| Uložit do souboru | `sort soubor.txt > vystup.txt` |
| Uložit přes /o | `sort soubor.txt /o vystup.txt` |
| Řadit podle sloupce | `sort /+5 soubor.txt` |
| Seřadit výstup příkazu | `dir \| sort` |
| Kombinace s find | `find "text" log.txt \| sort` |

 `Get-Content data.txt | Sort-Object {[int]$_}` (numerické řazení)  
> `Select-String -Pattern "error" -CaseSensitive:$false *.log` (hledání)

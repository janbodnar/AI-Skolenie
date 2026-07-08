# Windows CoreUtils — GNU nástroje pro Windows

Moderní sada unixových příkazů dostupná ve Windows (přes WSL, Git Bash, BusyBox, GnuWin32 nebo  
nativní porty). Níže je přehled nejužitečnějších nástrojů a jejich ekvivalentů v klasickém  
CMD a PowerShellu.


## 1. Získání CoreUtils pro Windows

### Způsoby instalace

| Metoda | Instalace | Popis |
|--------|-----------|-------|
| **WSL** | `wsl --install` | Plné linuxové prostředí (Ubuntu aj.) |
| **Git Bash** | Stažení [git-scm.com](https://git-scm.com) | Součást Gitu pro Windows — obsahuje MSYS2 coreutils |
| **BusyBox** | `winget install BusyBox` | Jediný executable s mnoha příkazy |
| **GnuWin32** | `winget install GnuWin32.CoreUtils` | Klasický port GNU coreutils |
| **MSYS2** | `winget install MSYS2.MSYS2` | Prostředí podobné Linuxu |
| **Chocolatey** | `choco install coreutils` | Správce balíčků + coreutils |

> **Doporučení:** Pro začátek stačí **Git Bash** (již má většinu nástrojů). Pro plnohodnotné  
prostředí použijte **WSL**.


## 2. Přehled CoreUtils příkazů

### 2.1 Práce se soubory

| Příkaz | Popis | CMD ekvivalent | PowerShell ekvivalent |
|--------|-------|-----------------|----------------------|
| `cat` | Zobrazí obsah souboru / spojí soubory | `type` | `Get-Content` (`gc`, `cat`) |
| `tac` | Zobrazí soubor pozpátku (od konce) | — | `Get-Content \| [Array]::Reverse` |
| `nl` | Očísluje řádky souboru | `find /n` | `Get-Content \| Format-Table -Auto` |
| `od` | Hexadecimální výpis souboru | — | `Format-Hex` |
| `base32` / `base64` | Kódování/dekódování | `certutil -encode` | `[Convert]::ToBase64String` |
| `tee` | Rozdělí výstup do souboru i terminálu | — | `Tee-Object` |

### 2.2 Práce s adresáři

| Příkaz | Popis | CMD ekvivalent | PowerShell ekvivalent |
|--------|-------|-----------------|----------------------|
| `ls` | Vypíše obsah adresáře | `dir` | `Get-ChildItem` (`ls`, `dir`) |
| `mkdir` / `mkdir -p` | Vytvoří adresář (včetně rodičů) | `md` | `New-Item -ItemType Directory` |
| `rmdir` / `rm -r` | Smaže adresář (rekurzivně) | `rd /s` | `Remove-Item -Recurse` |
| `cp` / `cp -r` | Kopíruje soubory/složky | `copy` / `xcopy` | `Copy-Item` |
| `mv` | Přesune/přejmenuje soubor | `move` | `Move-Item` |
| `rm` | Smaže soubor(y) | `del` | `Remove-Item` |
| `ln -s` | Vytvoří symbolický link | `mklink` | `New-Item -ItemType SymbolicLink` |
| `touch` | Vytvoří prázdný soubor / změní čas | `type nul > soubor` | `New-Item` / `Set-ItemProperty` |
| `chmod` | Změní oprávnění (pouze WSL) | `attrib` | — |
| `chown` | Změní vlastníka (pouze WSL) | — | — |

### 2.3 Prohlížení a manipulace s textem

| Příkaz | Popis | CMD ekvivalent | PowerShell ekvivalent |
|--------|-------|-----------------|----------------------|
| `head` | Prvních N řádků souboru | — | `Get-Content -Head` / `Select-Object -First` |
| `tail` | Posledních N řádků / sledování změn | — | `Get-Content -Tail` |
| `less` / `more` | Stránkovaný výstup | `more` | `Out-Host -Paging` |
| `wc` | Počet řádků/slov/znaků | `find /c /v ""` | `Measure-Object` |
| `sort` | Seřadí řádky | `sort` | `Sort-Object` |
| `uniq` | Odstraní duplicitní po sobě jdoucí řádky | — | `Get-Unique` |
| `cut` | Ořízne sloupce z řádků | — | `Select-Object -ExpandProperty` |
| `paste` | Spojí soubory po sloupcích | — | — |
| `join` | Spojí soubory podle společného pole | — | `Join-Object` |
| `tr` | Nahradí/přeloží znaky | — | `-replace` |
| `sed` | Stream editor — nahrazování textu | — | `-replace` |
| `awk` | Zpracování textu po sloupcích | — | `Select-Object` + `Where-Object` |
| `grep` | Hledání textu v souborech | `find` / `findstr` | `Select-String` |
| `strings` | Najde textové řetězce v binárním souboru | — | — |
| `expand` | Rozbalí tabulátory na mezery | — | — |
| `unexpand` | Nahradí mezery tabulátory | — | — |
| `fold` | Zalomení dlouhých řádků | — | — |
| `fmt` | Formátování odstavců | — | — |
| `pr` | Formátuje text pro tisk | — | — |

### 2.4 Vyhledávání a porovnávání

| Příkaz | Popis | CMD ekvivalent | PowerShell ekvivalent |
|--------|-------|-----------------|----------------------|
| `grep` | Hledá text (podporuje regex) | `findstr` | `Select-String` (`sls`) |
| `egrep` | Rozšířené regex | — | `Select-String` |
| `fgrep` | Doslovné hledání (žádný regex) | `find` | `Select-String -SimpleMatch` |
| `diff` | Porovná dva soubory | `fc` | `Compare-Object` |
| `cmp` | Binární porovnání souborů | `fc /b` | — |
| `comm` | Porovná dva seřazené soubory | — | `Compare-Object` |
| `md5sum` / `sha*sum` | Kontrolní součty | `certutil -hashfile` | `Get-FileHash` |
| `find` | Hledá soubory podle jména/data | `dir /s` | `Get-ChildItem -Recurse` |
| `locate` | Rychlé hledání v databázi | — | — |
| `which` | Zjistí cestu k executable | `where` | `Get-Command` |
| `file` | Určí typ souboru | — | — |

### 2.5 Správa systému

| Příkaz | Popis | CMD ekvivalent | PowerShell ekvivalent |
|--------|-------|-----------------|----------------------|
| `ps` | Výpis procesů | `tasklist` | `Get-Process` (`ps`) |
| `kill` | Ukončí proces | `taskkill` | `Stop-Process` (`kill`) |
| `top` / `htop` | Interaktivní monitor procesů | — | `Get-Process \| Sort-Object CPU` |
| `df` | Volné místo na discích | — | `Get-PSDrive` |
| `du` | Velikost adresáře | — | `Get-ChildItem -Recurse \| Measure-Object` |
| `free` | Volná paměť | `systeminfo` | `Get-CimInstance Win32_OperatingSystem` |
| `uname` | Informace o systému | `ver` | `[Environment]::OSVersion` |
| `uptime` | Doba běhu systému | `systeminfo \| find "Boot"` | `(Get-CimInstance Win32_OperatingSystem).LastBootUpTime` |
| `env` | Výpis proměnných prostředí | `set` | `Get-ChildItem Env:` |
| `echo` | Výpis textu | `echo` | `Write-Output` (`echo`) |
| `sleep` | Pauza na N sekund | `timeout` | `Start-Sleep` |
| `date` | Datum a čas | `date` / `time` | `Get-Date` |
| `cal` | Kalendář | — | — |
| `yes` | Opakovaný výpis textu | — | — |
| `seq` | Generování číselné řady | — | `1..10` |
| `xargs` | Spustí příkaz pro každý vstup | — | `ForEach-Object` (`%`) |

---

## 3. Podrobné příklady použití

### 3.1 `cat` — zobrazení a spojování souborů

```bash
# Zobrazení obsahu
cat file.txt
cat -n file.txt          # s čísly řádků

# Spojení více souborů
cat part1.txt part2.txt > complete.txt

# Spojení všech .csv do jednoho
cat *.csv > vsechny.csv

# Vytvoření souboru (Ctrl+D pro ukončení)
cat > novy.txt

# Přidání textu do souboru
cat >> existujici.txt

# Ve Windows (Git Bash) — alias pro cat s con
cat < con                 # čte ze vstupu (méně časté)
```

### 3.2 `ls` — výpis adresáře

```bash
# Základní výpis
ls              # krátký
ls -l           # dlouhý (podrobný)
ls -la          # včetně skrytých souborů
ls -lh          # velikosti v čitelném formátu (KB, MB)
ls -lt          # seřazeno podle času
ls -lS          # seřazeno podle velikosti
ls -ltr         # sestupně podle času (nejnovější dole)
ls -R           # rekurzivně (včetně podadresářů)

# Filtrování
ls *.txt        # jen .txt soubory
ls -d */        # jen adresáře
ls -l | grep "^d"  # jen adresáře (pipe s grep)

# Stromová struktura
ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g'
# Nebo použijte příkaz tree (tree .)
```

**Ukázkový výstup `ls -lh`:**
```
total 28K
drwxr-xr-x 2 user user 4.0K Jul  8 10:30 docs/
-rw-r--r-- 1 user user 2.3K Jul  8 09:15 main.py
-rw-r--r-- 1 user user  856 Jul  8 08:40 README.md
drwxr-xr-x 3 user user 4.0K Jul  7 14:22 src/
-rw-r--r-- 1 user user 1.2K Jul  8 10:00 test_main.py
```

### 3.3 `grep` — vyhledávání textu

```bash
# Základní hledání
grep "ERROR" log.txt
grep -i "error" log.txt          # case-insensitive
grep -r "TODO" src/              # rekurzivně
grep -n "FIXME" *.py             # s čísly řádků
grep -c "FAILED" *.log           # počet výskytů na soubor
grep -v "INFO" log.txt           # inverzní (řádky BEZ textu)

# Regulární výrazy
grep "^ERROR" log.txt            # řádky začínající na ERROR
grep "timeout$" log.txt          # řádky končící na timeout
grep "^[A-Z].*error" log.txt    # začíná velkým písmenem, obsahuje error
grep -E "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" log.txt  # IP adresy

# Kontext
grep -B 2 "ERROR" log.txt        # 2 řádky před
grep -A 3 "ERROR" log.txt        # 3 řádky po
grep -C 2 "ERROR" log.txt        # 2 řádky před i po

# Užitečné kombinace
ps aux | grep python             # najít python procesy
ls -l | grep "^d"                # jen adresáře
cat log.txt | grep -v "^$"       # odstranit prázdné řádky
grep -rL "TODO" src/             # soubory KTERÉ NEobsahují TODO
```

### 3.4 `head` a `tail` — začátek a konec souboru

```bash
# head — první řádky
head -n 10 log.txt               # prvních 10 řádků
head -c 100 file.txt             # prvních 100 bytů
head -20 log.txt                 # prvních 20 (zkrácený zápis)

# tail — poslední řádky
tail -n 10 log.txt               # posledních 10 řádků
tail -f log.txt                  # průběžné sledování (follow)
tail -f -n 50 log.txt            # posledních 50 a sledovat dál
tail -c 200 file.txt             # posledních 200 bytů

# Užitečné kombinace
tail -f access.log | grep "404"  # sledovat 404 chyby v reálném čase
tail -f log.txt | grep -i "error"  # sledovat chyby
cat log.txt | head -100 | tail -20  # řádky 80-100
```

**Ukázka `tail -f` (monitoring logu v reálném čase):**
```
10:30:01 INFO  Server started
10:30:05 WARNING Disk space low
10:30:10 INFO  Request received
10:30:12 ERROR Connection timeout   ← objeví se automaticky
```

### 3.5 `wc` — počítání

```bash
wc -l log.txt                    # počet řádků
wc -w soubor.txt                 # počet slov
wc -c soubor.txt                 # počet bytů
wc -m soubor.txt                 # počet znaků
wc data.txt                      # vše: řádky  slova  byty

# Užitečné kombinace
ls -l | wc -l                    # počet souborů v adresáři (včetně total)
ls -1 | wc -l                    # počet souborů/složek (jen názvy)
cat *.py | wc -l                 # celkový počet řádků Python kódu
grep -r "TODO" src/ | wc -l      # kolik TODO je v projektu
```

### 3.6 `tee` — výstup do souboru i terminálu

```bash
# Uloží do souboru a zároveň zobrazí
ls -la | tee vypis.txt

# Přidá na konec souboru (místo přepsání)
ls -la | tee -a vypis.txt

# S přesměrováním chyb
command 2>&1 | tee log.txt

# V dávkovém zpracování
cat log.txt | grep "ERROR" | tee chyby.txt | wc -l
```

### 3.7 `uniq` — odstranění duplicit

```bash
# Pozor! uniq odstraňuje pouze po sobě jdoucí duplicity
uniq soubor.txt
uniq -c soubor.txt               # spočítá výskyty
uniq -d soubor.txt               # pouze duplicitní řádky
uniq -u soubor.txt               # pouze unikátní řádky (bez duplicit)

# Vždy nejdříve sortovat!
sort soubor.txt | uniq
sort soubor.txt | uniq -c | sort -nr  # četnost výskytů sestupně

# Příklady
cat access.log | awk '{print $1}' | sort | uniq -c | sort -nr | head -10
# 10 nejčastějších IP adres z access logu
```

### 3.8 `cut` — ořezávání sloupců

```bash
# Ořezání podle oddělovače
cat data.csv | cut -d',' -f1      # první sloupec z CSV
cat data.csv | cut -d',' -f1,3   # sloupce 1 a 3
cat data.csv | cut -d',' -f2-5   # sloupce 2 až 5

# Ořezání podle pozice znaků
echo "abcdef" | cut -c1-3        # abc
echo "abcdef" | cut -c2-4        # bcd
echo "abcdef" | cut -c1,3,5      # a c e

# Praktický příklad — jména z /etc/passwd (nebo ekvivalent)
cat /etc/passwd | cut -d: -f1    # uživatelská jména
```

### 3.9 `sort` — pokročilé řazení

```bash
sort -n cisla.txt                # numerické řazení (na rozdíl od CMD sortu)
sort -h soubory.txt              # lidsky čitelné velikosti (2K, 3M, 1G)
sort -r soubor.txt               # sestupně
sort -u soubor.txt               # unikátní řazení (sort + uniq)
sort -k2 data.txt                # podle druhého sloupce
sort -t, -k3 -n data.csv         # CSV podle 3. sloupce numericky

# Příklady
du -sh * | sort -h               # soubory/adresáře podle velikosti
ls -l | sort -k5 -n              # soubory podle velikosti (5. sloupec)
ps aux | sort -nrk 3             # procesy podle CPU (3. sloupec)
```

### 3.10 `sed` — stream editor (nahrazování)

```bash
# Nahrazení textu
sed 's/starý/nový/' soubor.txt      # první výskyt na řádku
sed 's/starý/nový/g' soubor.txt     # všechny výskyty na řádku
sed -i 's/port=8080/port=9090/' config.txt  # přímo v souboru

# Smazání řádků
sed '/^$/d' soubor.txt              # smaže prázdné řádky
sed '/DEBUG/d' log.txt              # smaže řádky s DEBUG
sed '1,10d' soubor.txt              # smaže první 1-10 řádků

# Výběr řádků
sed -n '5,10p' soubor.txt           # vypíše řádky 5-10
sed -n '/ERROR/p' log.txt           # vypíše jen řádky s ERROR
```

### 3.11 `awk` — zpracování textu po sloupcích

```bash
# Základní použití
awk '{print $1}' soubor.txt         # první sloupec
awk '{print $1, $3}' soubor.txt     # první a třetí sloupec
awk -F',' '{print $1}' data.csv     # CSV s oddělovačem čárka

# Podmínky
awk '/ERROR/' log.txt               # řádky obsahující ERROR
awk '$3 > 100' data.txt             # řádky kde 3. sloupec > 100
awk 'NR > 1 {print}' data.csv       # přeskočit hlavičku (řádek 1)

# Formátování
awk '{printf "%-20s %s\n", $1, $2}' data.txt

# Praktické příklady
ps aux | awk '$3 > 50 {print $2, $11}'   # procesy s CPU > 50%
cat access.log | awk '{print $1}' | sort | uniq -c | sort -nr | head -5
# (TOP 5 IP adres — kombinace awk + sort + uniq)
```

### 3.12 `xargs` — spuštění příkazu pro každý vstup

```bash
# Hromadné mazání
find . -name "*.tmp" | xargs rm
find . -name "*.log" -mtime +7 | xargs rm   # starší než 7 dní

# Kopírování
find . -name "*.py" | xargs -I {} cp {} backup/

# Komprimace
ls *.txt | xargs gzip

# S paralelním zpracováním
cat urls.txt | xargs -P 4 -I {} curl -O {}
```

### 3.13 `find` — hledání souborů

```bash
# Hledání podle jména
find . -name "*.py"                    # všechny .py soubory
find . -iname "*.TXT"                  # case-insensitive
find . -name "test_*" -type f          # jen soubory začínající na test_
find . -name "__pycache__" -type d     # jen adresáře

# Podle času
find . -mtime -1                       # změněno za posledních 24h
find . -mmin -30                       # změněno za posledních 30 min
find . -mtime +90 -delete              # starší než 90 dní a smazat

# Podle velikosti
find . -size +10M                      # větší než 10 MB
find . -size -1k                       # menší než 1 kB
find . -size +1G -exec ls -lh {} \;

# S akcemi
find . -name "*.bak" -delete           # smazat všechny .bak
find . -name "*.py" -exec chmod +x {} \;  # přidat executable
find . -name "*.txt" -exec cat {} \; > vse.txt  # spojit všechny txt
```

### 3.14 `diff` — porovnání souborů

```bash
# Základní porovnání
diff file1.txt file2.txt
diff -u file1.txt file2.txt            # unified formát (přehlednější)
diff -y file1.txt file2.txt            # vedle sebe (side-by-side)
diff -r dir1/ dir2/                    # rekurzivně (celé adresáře)
diff -q dir1/ dir2/                    # jen zda se liší (ne výpis)
```

**Ukázka `diff -u`:**
```diff
--- file1.txt   2026-07-08 10:00:00
+++ file2.txt   2026-07-08 11:00:00
@@ -1,5 +1,5 @@
-print("Hello")
+print("Hello World")
 print("How are you?")
 
-for i in range(5):
+for i in range(10):
```

### 3.15 `od` a `hexdump` — hexadecimální výpis

```bash
# Hexadecimální výpis
od -xc soubor.bin
od -A x -t x1z -v soubor.bin         # adresa, hex, ASCII

# xxd (pokud je k dispozici)
xxd soubor.bin
xxd -r hex.txt > soubor.bin           # zpět z hex na binární
```

---

## 4. Dávkové zpracování — praktické skripty

### 4.1 Analyzátor logů

```bash
#!/bin/bash
# Analyza logu pomoci coreutils

LOG="server.log"

echo "=== Analyza logu ==="
echo "Pocet radku:        $(wc -l < $LOG)"
echo "Pocet ERROR:        $(grep -c -i 'ERROR' $LOG)"
echo "Pocet WARNING:      $(grep -c -i 'WARNING' $LOG)"
echo "Pocet INFO:         $(grep -c -i 'INFO' $LOG)"
echo ""
echo "Top 5 chybovych hlasek:"
grep -i "ERROR" $LOG | cut -d' ' -f3- | sort | uniq -c | sort -nr | head -5
echo ""
echo "IP adresy s nejvice pozadavky:"
grep -oE "[0-9]+\.[0-9]+\.[0-9]+\.[0-9]+" $LOG | sort | uniq -c | sort -nr | head -5
```

### 4.2 Zálohování a komprimace

```bash
#!/bin/bash
# Zaloha projektu

BACKUP_DIR="backup_$(date +%Y-%m-%d)"
mkdir -p "$BACKUP_DIR"

# Zkopírovat zdrojové soubory
find src/ -name "*.py" -exec cp {} "$BACKUP_DIR/" \;

# Zabalit
tar -czf "${BACKUP_DIR}.tar.gz" "$BACKUP_DIR"
rm -rf "$BACKUP_DIR"

echo "Zaloha vytvorena: ${BACKUP_DIR}.tar.gz"
```

### 4.3 Sledování adresáře

```bash
#!/bin/bash
# Sledovani adresare — upozorni na nove/změnené soubory

WATCH_DIR="."
SNAPSHOT="/tmp/snapshot.txt"

ls -lR "$WATCH_DIR" > "$SNAPSHOT"

while true; do
    sleep 5
    NEW=$(ls -lR "$WATCH_DIR" | diff - "$SNAPSHOT")
    if [ -n "$NEW" ]; then
        echo "=== Zmena detected: $(date) ==="
        echo "$NEW"
        ls -lR "$WATCH_DIR" > "$SNAPSHOT"
    fi
done
```

---

## 5. Rychlá referencia — nejčastější úkoly

| Úkol | CoreUtils příkaz |
|------|-----------------|
| Zobrazit soubor | `cat file.txt` |
| Zobrazit prvních 10 řádků | `head file.txt` |
| Sledovat log v reálném čase | `tail -f log.txt` |
| Najít text v souborech | `grep -r "text" .` |
| Počítat řádky/slova | `wc -l file.txt` |
| Porovnat soubory | `diff -u file1 file2` |
| Seřadit čísla (numericky) | `sort -n cisla.txt` |
| Unikátní řádky (s počtem) | `sort data \| uniq -c` |
| Hledat soubory podle jména | `find . -name "*.py"` |
| Smazat staré soubory | `find . -mtime +90 -delete` |
| Velikost adresáře | `du -sh .` |
| Volné místo | `df -h .` |
| Spojit CSV soubory | `cat *.csv > vse.csv` |
| Oříznout první sloupec CSV | `cut -d',' -f1 data.csv` |
| Monitorovat procesy | `ps aux \| sort -nrk 3 \| head` |
| Hash souboru | `sha256sum file.bin` |
| Rozdělit výstup (soubor+obrazovka) | `command \| tee log.txt` |

---

## 6. Porovnání: příkazy napříč prostředími

| Úkol | CMD | CoreUtils (Git Bash) | PowerShell |
|------|-----|---------------------|------------|
| Výpis adresáře | `dir` | `ls -la` | `Get-ChildItem` |
| Kopírování | `copy a b` | `cp a b` | `Copy-Item a b` |
| Přesun | `move a b` | `mv a b` | `Move-Item a b` |
| Smazání | `del a` | `rm a` | `Remove-Item a` |
| Vytvořit adresář | `md d` | `mkdir -p d` | `New-Item d -Type Dir` |
| Zobrazit soubor | `type f` | `cat f` | `Get-Content f` |
| Hledat text | `find "t" f` | `grep "t" f` | `Select-String "t" f` |
| Hledat soubory | `dir /s *.py` | `find . -name "*.py"` | `Get-ChildItem -Recurse *.py` |
| Porovnat soubory | `fc a b` | `diff a b` | `Compare-Object a b` |
| Počítat řádky | `find /c /v "" f` | `wc -l f` | `(Get-Content f).Count` |
| Prvních N řádků | — | `head -n 5 f` | `Get-Content f -Head 5` |
| Posledních N řádků | — | `tail -n 5 f` | `Get-Content f -Tail 5` |
| Symbolický link | `mklink` | `ln -s` | `New-Item -ItemType SymbolicLink` |
| Sledování logu | — | `tail -f f` | `Get-Content f -Wait` |
| Zřetězení | `type a b > c` | `cat a b > c` | `Get-Content a,b \| Set-Content c` |


> **Shrnutí:** GNU CoreUtils přinášejí do Windows výkonné nástroje známé z Linuxu. Nejjednodušší cesta k nim je **Git Bash** (součást Gitu pro Windows) nebo **WSL** pro plné linuxové prostředí. CoreUtils jsou ideální pro pokročilou manipulaci s textem, dávkové zpracování a skriptování — zejména `grep`, `sed`, `awk`, `find`, `sort`, `uniq` a `xargs` výrazně rozšiřují možnosti klasického CMD.

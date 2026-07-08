# Základní příkazy Windows CMD

CMD (Command Prompt) je interpret příkazového řádku ve Windows. Níže je přehled nejužitečnějších  
příkazů rozdělených do kategorií.

> **Poznámka:** Příkazy jsou case-insensitive (nezáleží na velikosti písmen). Parametry
>  označené `[ ]` jsou nepovinné.


## 1. Práce se soubory a složkami

| Příkaz | Popis | Příklady |
|--------|-------|----------|
| `dir` | Vypíše obsah aktuálního adresáře | `dir`, `dir C:\Windows`, `dir /p` (stránkování), `dir /s` (včetně podadresářů), `dir /w` (široký výpis) |
| `cd` / `chdir` | Změní aktuální adresář | `cd C:\Users`, `cd ..` (o úroveň výš), `cd /d D:\` (přesun na jiný disk) |
| `md` / `mkdir` | Vytvoří nový adresář | `md složka`, `mkdir "složka s mezerami"`, `mkdir a\b\c` |
| `rd` / `rmdir` | Smaže prázdný adresář | `rd složka`, `rmdir /s složka` (včetně obsahu), `rmdir /s /q složka` (bez potvrzení) |
| `del` / `erase` | Smaže soubor(y) | `del soubor.txt`, `del *.tmp` (všechny .tmp), `del /s *.log` (rekurzivně) |
| `ren` / `rename` | Přejmenuje soubor/složku | `ren starý.txt nový.txt`, `ren *.txt *.bak` |
| `copy` | Kopíruje soubor(y) | `copy zdroj.txt cíl.txt`, `copy *.txt C:\Cíl\`, `copy /y` (přepsat bez dotazu) |
| `xcopy` | Pokročilé kopírování souborů a stromů | `xcopy C:\Zdroj\ C:\Cíl\ /e` (i podadresáře), `/h` (skryté), `/y` (bez dotazu) |
| `robocopy` | Velmi pokročilé kopírování (Vista+) | `robocopy C:\Zdroj C:\Cíl /mir` (zrcadlení), `/copyall`, `/r:1 /w:1` |
| `move` | Přesune soubor/y nebo přejmenuje | `move soubor.txt C:\Cíl\`, `move *.txt C:\Cíl\` |
| `type` | Zobrazí obsah textového souboru | `type soubor.txt`, `type soubor.txt \| more` |
| `find` | Hledá text v souborech | `find "text" soubor.txt`, `find /i "text"` (case-insensitive), `find /v "text"` (řádky bez textu) |
| `fc` | Porovná dva soubory | `fc soubor1.txt soubor2.txt`, `fc /b soubor1.bin soubor2.bin` (binárně) |
| `attrib` | Zobrazí/nastaví atributy souborů | `attrib +r soubor.txt` (read-only), `+h` (skrytý), `+s` (systémový), `attrib -r -h` (odebrání) |

---

## 2. Správa disků a úložiště

| Příkaz | Popis | Příklady |
|--------|-------|----------|
| `chkdsk` | Zkontroluje disk a opraví chyby | `chkdsk C:`, `chkdsk C: /f` (oprava), `/r` (nalezení vadných sektorů) |
| `diskpart` | Správa disků a oddílů (interaktivní) | `diskpart` → `list disk` → `select disk 0` → `list partition` |
| `vol` | Zobrazí jmenovku a sériové číslo disku | `vol C:` |
| `label` | Změní jmenovku disku | `label C: NováJmenovka` |
| `fsutil` | Nástroj pro správu souborového systému | `fsutil volume diskfree C:` (volné místo) |
| `wmic logicaldisk` | Zobrazí informace o discích | `wmic logicaldisk get size,freespace,caption` |

---

## 3. Správa procesů a systému

| Příkaz | Popis | Příklady |
|--------|-------|----------|
| `tasklist` | Vypíše běžící procesy | `tasklist`, `tasklist \| find "notepad"`, `tasklist /v` (podrobně) |
| `taskkill` | Ukončí proces | `taskkill /im notepad.exe`, `taskkill /pid 1234`, `taskkill /f /im chrome.exe` (vynuceně) |
| `shutdown` | Vypne/restartuje počítač | `shutdown /s` (vypnout), `/r` (restart), `/t 60` (za 60s), `/a` (zrušit) |
| `logoff` | Odhlásí aktuálního uživatele | `logoff` |
| `powercfg` | Správa napájecích profilů | `powercfg /hibernate on`, `powercfg /energy` (analýza) |
| `systeminfo` | Zobrazí podrobné informace o systému | `systeminfo`, `systeminfo \| find "OS Name"` |
| `ver` | Zobrazí verzi Windows | `ver` |
| `driverquery` | Vypíše nainstalované ovladače | `driverquery`, `driverquery /v` (podrobně) |
| `sfc` | Zkontroluje chráněné systémové soubory | `sfc /scannow`, `sfc /verifyonly` |
| `msconfig` | Spustí konfiguraci systému | `msconfig` (GUI okno) |

---

## 4. Práce s textem a řetězci

| Příkaz | Popis | Příklady |
|--------|-------|----------|
| `echo` | Vypíše text nebo proměnnou | `echo Ahoj světe!`, `echo %PATH%`, `echo off` / `echo on` |
| `more` | Zobrazí výstup po stránkách | `type velky.txt \| more`, `dir \| more` |
| `sort` | Seřadí vstup | `sort vstup.txt`, `dir \| sort`, `sort /r` (sestupně) |
| `set` | Zobrazí/nastaví proměnné prostředí | `set`, `set JMENO=Hodnota`, `set PATH=%PATH%;C:\Nova` |
| `findstr` | Hledá vzor v textu (regex) | `findstr "error" *.log`, `findstr /i "warning.*timeout"` |

---

## 5. Síťové příkazy

| Příkaz | Popis | Příklady |
|--------|-------|----------|
| `ping` | Otestuje dostupnost hostitele | `ping google.com`, `ping -t` (nepřetržitě), `ping -n 10 8.8.8.8` |
| `ipconfig` | Zobrazí konfiguraci sítě | `ipconfig`, `ipconfig /all`, `ipconfig /release`, `ipconfig /renew`, `ipconfig /flushdns` |
| `tracert` | Zobrazí cestu k cíli | `tracert google.com` |
| `nslookup` | Dotaz na DNS | `nslookup google.com` |
| `netstat` | Zobrazí síťová připojení | `netstat -an`, `netstat -b` (aplikace), `netstat -o` (PID) |
| `netsh` | Pokročilá konfigurace sítě | `netsh wlan show profiles`, `netsh interface show interface` |
| `route` | Zobrazí/upraví směrovací tabulku | `route print`, `route add 10.0.0.0 mask 255.0.0.0 10.0.0.1` |
| `arp` | Zobrazí/spravuje ARP cache | `arp -a` |
| `getmac` | Zobrazí MAC adresy | `getmac`, `getmac /v` |
| `telnet` | Telnet klient | `telnet adresa port` |
| `ssh` | SSH klient (Windows 10 1809+) | `ssh user@host` |

---

## 6. Práce s časem a plánováním

| Příkaz | Popis | Příklady |
|--------|-------|----------|
| `date` | Zobrazí/nastaví datum | `date`, `date 15-03-2025` |
| `time` | Zobrazí/nastaví čas | `time`, `time 14:30` |
| `schtasks` | Správa naplánovaných úloh | `schtasks /create /tn "Nazev" /tr "cesta" /sc daily /st 09:00`, `schtasks /query` |
| `timeout` | Pozastaví provádění na x sekund | `timeout /t 5` (5s pauza), `/nobreak` (nelze přerušit) |
| `sleep` | Pozastaví provádění (starší verze) | `sleep 5` |

---

## 7. Přesměrování a pipy

| Symbol | Popis | Příklad |
|--------|-------|---------|
| `>` | Přesměruje výstup do souboru (přepíše) | `dir > vypis.txt` |
| `>>` | Přesměruje výstup do souboru (přidá) | `echo Nový záznam >> log.txt` |
| `<` | Přesměruje obsah souboru na vstup | `sort < vstup.txt` |
| `\|` | Propojí příkazy (pipe) | `dir \| find "txt"`, `tasklist \| sort` |
| `2>` | Přesměruje chybový výstup | `dir neexistuje 2> chyby.txt` |
| `2>&1` | Sloučí chybový výstup s normálním | `dir > vse.txt 2>&1` |
| `&` | Provádí příkazy za sebou | `dir & ver & echo Hotovo` |
| `&&` | Spustí další příkaz jen pokud předchozí uspěl | `cd složka && dir` |
| `\|\|` | Spustí další příkaz jen pokud předchozí selhal | `cd složka \|\| echo Selhalo` |

---

## 8. Speciální klávesy a triky

| Klávesa | Popis |
|---------|-------|
| `↑` / `↓` | Procházení historie příkazů |
| `F7` | Zobrazí historii příkazů v seznamu |
| `F3` | Zopakuje předchozí příkaz |
| `Tab` | Automatické doplňování názvů souborů/složek |
| `Ctrl+C` | Přeruší běžící příkaz |
| `Ctrl+V` | Vloží text (v moderním CMD) |
| `Alt+F7` | Smaže historii příkazů |
| `cls` | Smaže obrazovku terminálu |
| `exit` | Zavře CMD okno |

---

## 9. Užitečné dávkové konstrukce (Batch)

```batch
@echo off
REM Toto je komentář

REM Proměnné
set jmeno=Petr
echo %jmeno%

REM Podmínka
if exist soubor.txt (
    echo Soubor existuje
) else (
    echo Soubor neexistuje
)

REM Cyklus
for %%i in (*.txt) do (
    echo Zpracovávám %%i
)

REM Parametry skriptu
echo První parametr: %1
echo Druhý parametr: %2
echo Všechny parametry: %*

REM Návratový kód
exit /b 0
```

---

## 10. Užitečné proměnné prostředí

| Proměnná | Popis | Příklad hodnoty |
|----------|-------|-----------------|
| `%USERNAME%` | Jméno přihlášeného uživatele | `Admin` |
| `%USERPROFILE%` | Cesta k profilu uživatele | `C:\Users\Admin` |
| `%SYSTEMROOT%` | Adresář Windows | `C:\Windows` |
| `%TEMP%` / `%TMP%` | Dočasný adresář | `C:\Users\Admin\AppData\Local\Temp` |
| `%PATH%` | Cesty k spustitelným souborům | `C:\Windows\System32;...` |
| `%DATE%` | Aktuální datum | `08.07.2026` |
| `%TIME%` | Aktuální čas | `10:30:45,12` |
| `%CD%` | Aktuální adresář | `C:\Users\Admin` |
| `%RANDOM%` | Náhodné číslo 0–32767 | `15234` |
| `%COMPUTERNAME%` | Název počítače | `PC-JMENO` |

---

## 11. Získání nápovědy

```cmd
help              // Zobrazí seznam všech příkazů
help dir          // Zobrazí nápovědu ke konkrétnímu příkazu
dir /?            // Alternativní způsob nápovědy (u většiny příkazů)
command /?        // Univerzální přepínač pro nápovědu
```

---

## 12. Rychlý přehled — často používané kombinace

```cmd
cls                     // Vyčištění obrazovky
ipconfig /flushdns      // Obnovení DNS cache
sfc /scannow            // Kontrola systémových souborů
chkdsk C: /f            // Kontrola disku C:
powercfg /hibernate off // Vypnutí hibernate
shutdown /r /t 0        // Okamžitý restart
taskkill /f /im program.exe  // Vynucené ukončení programu
ping -t 8.8.8.8         // Průběžný ping (Ctrl+C pro zastavení)
```

---

## 13. Porovnání CMD vs PowerShell vs Bash

| Operace | CMD | PowerShell | Bash (Linux) |
|---------|-----|-----------|--------------|
| Výpis adresáře | `dir` | `Get-ChildItem` (`ls`, `dir`) | `ls` |
| Výpis procesů | `tasklist` | `Get-Process` (`ps`) | `ps aux` |
| Hledání v textu | `find` | `Select-String` | `grep` |
| Hledání souborů | `dir /s` | `Get-ChildItem -Recurse` | `find` |
| Porovnání souborů | `fc` | `Compare-Object` | `diff` |
| Přípona skriptů | `.bat` / `.cmd` | `.ps1` | (žádná / `.sh`) |
| Proměnné | `%VAR%` | `$VAR` | `$VAR` |

---

> **Tip:** CMD je stále užitečné pro rychlé úkoly a starší skripty, ale pro nové projekty zvažte PowerShell, který je výkonnější a modernější. Pro rychlé zopakování syntaxe stačí napsat `název_příkazu /?` nebo `help název_příkazu`.

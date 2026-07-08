# Winget — Správca balíčkov pre Windows

**Winget** (Windows Package Manager) je oficiálny správca balíčkov od Microsoftu, ktorý umožňuje  
inštalovať, aktualizovať a spravovať softvér priamo z príkazového riadku. Je to ekvivalent `apt` 
(Linux), `brew` (macOS) alebo `choco` pre Windows.

## 1. Inštalácia a overenie

### Overenie, či je winget nainštalovaný

```cmd
winget --version
```

Winget je súčasťou **Windows 10 1809+** a **Windows 11**. Ak nie je k dispozícii, nainštalujte ho cez:

- **Microsoft Store:** Vyhľadajte "App Installer"
- **Manuálne:** [github.com/microsoft/winget-cli](https://github.com/microsoft/winget-cli/releases)

### Základná nápoveda

```cmd
winget --help              # všeobecná nápoveda
winget <prikaz> --help     # nápoveda ku konkrétnemu príkazu
```

---

## 2. Základné príkazy — prehľad

| Príkaz | Popis |
|--------|-------|
| `winget search` | Vyhľadá balíček v databáze |
| `winget install` | Nainštaluje balíček |
| `winget show` | Zobrazí podrobnosti o balíčku |
| `winget list` | Zoznam nainštalovaných balíčkov |
| `winget upgrade` | Aktualizuje balíček(y) |
| `winget uninstall` | Odinštaluje balíček |
| `winget source` | Správa zdrojov (repozitárov) |
| `winget export` | Exportuje zoznam nainštalovaných balíčkov |
| `winget import` | Nainštaluje balíčky z exportovaného súboru |
| `winget validate` | Overí manifest balíčka |
| `winget settings` | Otvorí konfiguračný súbor |
| `winget features` | Zobrazí dostupné funkcie |
| `winget hash` | Vypočíta hash inštalačného súboru |

---

## 3. Vyhľadávanie balíčkov

### Základné vyhľadávanie

```cmd
REM Vyhľadanie podľa názvu
winget search firefox
winget search python
winget search vscode
winget search 7zip

REM Vyhľadanie s viacerými slovami
winget search "visual studio code"
winget search "google chrome"
```

**Ukážkový výstup:**
```
Názov                  ID                             Verzia      Zdroj
-----------------------------------------------------------------------
Firefox                Mozilla.Firefox                128.0       winget
Firefox Developer      Mozilla.Firefox.Developer      129.0b5     winget
Firefox ESR            Mozilla.Firefox.ESR            115.12.0    winget
Firefox Nightly        Mozilla.Firefox.Nightly        130.0a1     winget
```

### Filtrovanie

```cmd
REM Filtrovanie podľa zdroja
winget search python --source winget
winget search python --source msstore

REM Filtrovanie podľa značky
winget search --tag "editor"
winget search --tag "browser"
winget search --tag "database"

REM Presné ID
winget search --id Microsoft.VisualStudioCode
winget search --name "Visual Studio Code"
winget search --moniker "nodejs"
```

### Zobrazenie podrobností o balíčku

```cmd
REM Základné informácie
winget show Firefox
winget show Microsoft.VisualStudioCode
winget show 7zip.7zip

REM Zobrazenie všetkých verzií
winget show Firefox --versions
```

**Ukážkový výstup `winget show Firefox`:**
```
Nájsť: Mozilla.Firefox
Verzia: 128.0
Vydavateľ: Mozilla
Moniker: firefox
Popis: Mozilla Firefox je rýchly, ľahký a nenáročný webový prehliadač.
Domovská stránka: https://www.mozilla.org/firefox/
Licencia: Mozilla Public License 2.0
Inštalačná URL: https://download-installer.cdn.mozilla.net/...
```

---

## 4. Inštalácia balíčkov

### Základná inštalácia

```cmd
REM Inštalácia podľa názvu
winget install firefox
winget install python
winget install vlc

REM Inštalácia podľa ID (presnejšie)
winget install --id Mozilla.Firefox
winget install --id Microsoft.VisualStudioCode
winget install --id Git.Git

REM Inštalácia konkrétnej verzie
winget install --id Python.Python --version 3.12.0
winget install NodeJS.NodeJS --version 20.11.0
```

### Dôležité prepínače

```cmd
--exact                     # presný názov (bez doplňovania)
--id                        # inštalácia podľa ID
--name                      # inštalácia podľa názvu
--moniker                   # inštalácia podľa monikeru
--version                   # konkrétna verzia
--source                    # zdroj (winget / msstore)
--accept-package-agreements # automatické prijatie licencie
--accept-source-agreements  # automatické prijatie zdroja
--location                  # vlastná cesta inštalácie
--scope                     # user / machine
--silent                    # tichá inštalácia (bez GUI)
```

### Tichá (silent) inštalácia

```cmd
REM Bez potvrdzovacích dialógov
winget install firefox --silent --accept-package-agreements

REM Inštalácia pre všetkých používateľov
winget install vscode --scope machine --silent

REM Vlastná cesta
winget install git --location "D:\Programy\Git"
```

### Inštalácia viacerých balíčkov naraz

```cmd
REM Jednotlivé príkazy (jeden po druhom)
winget install firefox && winget install vlc && winget install 7zip

REM Pomocou dávkového súboru
```

Príklad dávkového súboru `install-dev-tools.bat`:

```batch
@echo off
echo Inštalujem vývojárske nástroje...

winget install Microsoft.VisualStudioCode --silent --accept-package-agreements
winget install Git.Git --silent --accept-package-agreements
winget install NodeJS.NodeJS --silent --accept-package-agreements
winget install Python.Python --silent --accept-package-agreements
winget install Docker.DockerDesktop --silent --accept-package-agreements
winget install Microsoft.WindowsTerminal --silent --accept-package-agreements
winget install Microsoft.PowerShell --silent --accept-package-agreements

echo Hotovo!
pause
```

---

## 5. Zoznam nainštalovaných balíčkov

```cmd
REM Zoznam všetkých nainštalovaných balíčkov
winget list

REM Filtrovanie
winget list --name python
winget list --id microsoft
winget list --source winget

REM Zoznam iba tých, ktoré má winget v databáze
winget list --include-unknown
```

**Ukážkový výstup:**
```
Názov                   ID                               Verzia       Dostupná
------------------------------------------------------------------------------
7-Zip 24.01             7zip.7zip                        24.01
Git                     Git.Git                          2.45.0
Microsoft Edge          Microsoft.Edge                   126.0.2592.81
Mozilla Firefox         Mozilla.Firefox                  128.0        128.0.1
Notepad++               Notepad++.Notepad++              8.6.5
Obsidian                Obsidian.Obsidian                1.6.5
Python 3.12             Python.Python.3.12               3.12.4       3.12.5
Visual Studio Code      Microsoft.VisualStudioCode       1.91.1
VLC media player        VideoLAN.VLC                     3.0.21
```

> V stĺpci **Dostupná** je uvedená novšia verzia, ak existuje — tieto balíčky možno aktualizovať.

---

## 6. Aktualizácia balíčkov

### Kontrola dostupných aktualizácií

```cmd
REM Zoznam balíčkov s dostupnou aktualizáciou
winget upgrade

REM Alternatívny zápis
winget update
```

**Ukážkový výstup:**
```
Názov                   ID                               Verzia       Dostupná
------------------------------------------------------------------------------
Mozilla Firefox         Mozilla.Firefox                  128.0        128.0.1
Python 3.12             Python.Python.3.12               3.12.4       3.12.5
VLC media player        VideoLAN.VLC                     3.0.21       3.0.22
```

### Aktualizácia jednotlivých balíčkov

```cmd
REM Aktualizácia konkrétneho balíčka
winget upgrade firefox
winget upgrade python
winget upgrade vlc

REM Podľa ID
winget upgrade --id Mozilla.Firefox
```

### Hromadná aktualizácia všetkých balíčkov

```cmd
REM Aktualizácia všetkých balíčkov naraz
winget upgrade --all

REM Tichá aktualizácia všetkého
winget upgrade --all --silent --accept-package-agreements
```

### Vylúčenie balíčkov z aktualizácie

```cmd
REM Aktualizovať všetko okrem Pythonu
winget upgrade --all --exclude Python.Python.3.12
```

---

## 7. Odinštalovanie balíčkov

```cmd
REM Odinštalovanie podľa názvu
winget uninstall firefox
winget uninstall 7zip

REM Odinštalovanie podľa ID
winget uninstall --id Mozilla.Firefox
winget uninstall --id 7zip.7zip
```

---

## 8. Export a import — prenos konfigurácie

### Export zoznamu balíčkov

```cmd
REM Export do JSON súboru
winget export -o balicky.json

REM Export s konkrétnym zdrojom
winget export -o balicky.json --source winget

REM Export iba nepovinných (nie systémových) balíčkov
winget export -o balicky.json --include-versions
```

**Ukážkový súbor `balicky.json`:**
```json
{
  "$schema": "https://aka.ms/winget-packages.schema.2.0.json",
  "Sources": [
    {
      "SourceDetails": {
        "Argument": "https://cdn.winget.microsoft.com/cache",
        "Identifier": "Microsoft.Winget.Source_8wekyb3d8bbwe",
        "Name": "winget",
        "Type": "Microsoft.PreIndexed.Package"
      },
      "Packages": [
        { "PackageIdentifier": "7zip.7zip" },
        { "PackageIdentifier": "Git.Git" },
        { "PackageIdentifier": "Microsoft.VisualStudioCode" },
        { "PackageIdentifier": "Mozilla.Firefox" }
      ]
    }
  ]
}
```

### Import balíčkov z JSON súboru

```cmd
REM Inštalácia všetkých balíčkov z exportu
winget import -i balicky.json

REM Tichý import
winget import -i balicky.json --silent --accept-package-agreements
```

---

## 9. Správa zdrojov (Sources)

### Zobrazenie zdrojov

```cmd
REM Zoznam registrovaných zdrojov
winget source list
```

**Výstup:**
```
Názov      Argument
----------------------------------------------
winget     https://cdn.winget.microsoft.com/cache
msstore    https://storeedgefd.dsx.mp.microsoft.com/v9.0
```

### Pridanie a odstránenie zdroja

```cmd
REM Pridanie vlastného zdroja
winget source add --name myrepo --arg "https://moj-repo.example.com"

REM Odstránenie zdroja
winget source remove --name myrepo

REM Aktualizácia zdrojov
winget source update

Resetovanie zdrojov (obnovenie predvolených)
winget source reset --force
```

---

## 10. Nastavenia (Settings)

```cmd
REM Otvorenie konfiguračného súboru v predvolenom editore
winget settings
```

Ukážka konfigurácie `settings.json`:

```json
{
  "$schema": "https://aka.ms/winget-settings.schema.json",

  // Tiché inštalácie pre všetky balíčky
  "installBehavior": {
    "preferences": {
      "scope": "machine",
      "locale": "sk-SK"
    }
  },

  // Správanie pri aktualizáciách
  "updateBehavior": {
    "enable": true
  },

  // Vizualizácia
  "visual": {
    "progressBar": "accent"
  }
}
```

---

## 11. Praktické príklady podľa kategórií

### Vývojárske nástroje (Dev Tools)

```cmd
REM Jedným príkazom
winget install Microsoft.VisualStudioCode Git.Git NodeJS.NodeJS Python.Python Docker.DockerDesktop Microsoft.WindowsTerminal Microsoft.PowerShell PostgreSQL.PostgreSQL
```

### Internet a komunikácia

```cmd
winget install Mozilla.Firefox Google.Chrome Opera.Opera Brave.Brave Slack.Slack Discord.Discord Zoom.Zoom
```

### Multimédiá

```cmd
winget install VideoLAN.VLC Spotify.Spotify GIMP.GIMP OBSProject.OBSStudio Kodi.Kodi Audacity.Audacity
```

### Kancelárske nástroje

```cmd
winget install 7zip.7zip Notepad++.Notepad++ LibreOffice.LibreOffice PDFsam.PDFsam SumatraPDF.SumatraPDF
```

### Utility a systém

```cmd
winget install Microsoft.PowerToys Microsoft.Sysinternals.Autoruns voidtools.Everything CPUID.CPU-Z CrystalDewWorld.CrystalDiskMark
```

---

## 12. Užitočné tipy a triky

### Skratka `wi` (alias)

Od Windows 11 môžete používať skratku:

```cmd
wi search firefox
wi install firefox
wi list
wi upgrade --all
```

### Hromadná inštalácia s potvrdením

```cmd
REM Zobrazenie iba prvých 5 výsledkov a výber
winget search python | findstr /n "^" | findstr "^[1-5]:"
```

### Zistenie presného ID balíčka

```cmd
REM Rýchle vyhľadanie presného ID
winget search --query firefox --exact
```

### Inštalácia z Microsoft Store

```cmd
REM Niektoré aplikácie sú len v Microsoft Store
winget install "Netflix" --source msstore
winget install "Spotify" --source msstore
winget install "Adobe Acrobat Reader" --source msstore
```

> Pri prvom použití `msstore` zdroja budete vyzvaní na prijatie zmluvných podmienok.


## 13. Porovnanie: Winget vs ostatné správcovia balíčkov

| Vlastnosť | Winget | Chocolatey | Scoop | PowerShell Gallery |
|-----------|--------|------------|-------|-------------------|
| Vývojár | Microsoft | Community | Community | Microsoft |
| Inštalácia | Vstavaný | `choco install` | `scoop install` | `Install-Module` |
| GUI inštalátory | ✅ Áno | ✅ Áno | ❌ Nie | ❌ Nie |
| Portable apps | ❌ Nie | ✅ (--params) | ✅ Áno | ❌ Nie |
| Moduly PowerShell | ❌ Nie | ❌ Nie | ❌ Nie | ✅ Áno |
| Offline zdroje | ❌ Nie | ❌ Nie | ❌ Nie | ❌ Nie |
| Export/Import | ✅ JSON | ✅ (`choco pin`) | ✅ (`scoop export`) | ❌ |
| Rýchlosť | Rýchly | Stredný | Rýchly | Stredný |
| Databáza | winget + msstore | chocolatey.org | github.com | powershellgallery.com |

## 14. Rýchla referencia — najčastejšie príkazy

```cmd
winget search <názov>              # vyhľadanie balíčka
winget install <názov>             # inštalácia
winget install <názov> --silent    # tichá inštalácia
winget show <názov>                # podrobnosti o balíčku
winget list                        # zoznam nainštalovaných
winget upgrade                     # kontrola aktualizácií
winget upgrade --all               # aktualizácia všetkého
winget upgrade --all --silent      # tichá aktualizácia
winget uninstall <názov>           # odinštalovanie
winget export -o baliky.json       # export zoznamu
winget import -i baliky.json       # import/inštalácia dávky
winget source list                 # zoznam zdrojov
winget settings                    # otvorenie nastavení
winget --help                      # nápoveda
```


> **Záver:** Winget je moderný a pohodlný nástroj na správu softvéru vo Windows. Umožňuje inštalovať, aktualizovať a odinštalovať aplikácie z príkazového riadku bez manuálneho sťahovania inštalátorov. Pre bežných používateľov je ideálny na rýchlu inštaláciu známych programov, pre vývojárov na automatizáciu nastavenia prostredia. Kombinácia `winget export` / `winget import` je skvelá na prenos konfigurácie medzi počítačmi alebo pri preinštalovaní systému.

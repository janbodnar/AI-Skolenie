# Nastavenie GTP Luna na VS Code


Tento postup nastaví model GPT-6 Luna vo VS Code cez rozšírenie Continue a OpenAI API. Používanie API sa účtuje samostatne; predplatné ChatGPT Plus ani iné predplatné ChatGPT API kredity nezahŕňa.

## 1. Prihlásenie do OpenAI Platform

1. Otvor [OpenAI Platform](https://platform.openai.com/) a prihlás sa existujúcim OpenAI účtom alebo si vytvor nový účet.
2. Ak ťa platforma vyzve na vytvorenie organizácie alebo doplnenie údajov, postupuj podľa pokynov na stránke.

## 2. Nákup API kreditu

1. Otvor [prehľad fakturácie API](https://platform.openai.com/account/billing).
2. Vyber **Add payment details** a zadaj fakturačné a platobné údaje.
3. Zvoľ sumu kreditu a potvrď nákup. Minimálny prvý nákup je podľa aktuálnych pravidiel 5 USD.
4. Pri nastavovaní skontroluj možnosť **Use auto-reload**. Automatické dobíjanie je pri prvom nastavení predvolene zapnuté; vypni ho, ak chceš kredit dopĺňať iba ručne. Ak ho ponecháš zapnuté, nastav hranicu a limit dobíjania.

Kredit sa odpočítava podľa používania API. Nepoužitý zakúpený kredit spravidla vyprší po jednom roku. Aktuálne podmienky a zostatok skontroluješ v [API Billing](https://platform.openai.com/account/billing).

## 3. Vytvorenie API kľúča

1. Otvor [stránku API kľúčov](https://platform.openai.com/api-keys).
2. Klikni na **Create new secret key**, zadaj názov, napríklad `VS Code Continue`, a vytvor kľúč.
3. Kľúč si hneď bezpečne skopíruj. Celý tajný kľúč sa zobrazí iba pri vytvorení.

API kľúč nikomu neposielaj a nevkladaj ho do zdrojového kódu, snímok obrazovky ani do verejného Git repozitára.

## 4. Inštalácia Continue vo VS Code

1. Vo VS Code otvor panel **Extensions** (`Ctrl+Shift+X`).
2. Vyhľadaj **Continue** od vydavateľa Continue a nainštaluj rozšírenie.
3. Otvor príkazovú paletu (`Ctrl+Shift+P`), vyhľadaj **Continue: Open config** a otvor konfiguračný súbor `config.yaml`.

## 5. Bezpečné uloženie kľúča vo Windows

1. V Prieskumníkovi otvor priečinok `%USERPROFILE%\.continue`. Ak neexistuje, vytvor ho.
2. Vytvor v ňom súbor `.env` (názov súboru je presne `.env`, bez prípony `.txt`).
3. Vlož do súboru tento riadok a nahraď text za `=` svojím API kľúčom:

```text
OPENAI_API_KEY=sem_vloz_svoj_api_kluc
```

Ulož súbor. Kľúč sa tak nebude zapisovať priamo do konfigurácie modelu. Súbor `.env` nikdy nepridávaj do Git repozitára.

## 6. Nastavenie GPT-6 Luna

Do `config.yaml` vlož alebo doplň túto konfiguráciu. Ak už súbor obsahuje iné nastavenia, zachovaj ich a doplň iba položku modelu do zoznamu `models`.

```yaml
name: OpenAI GPT-6 Luna
version: 0.0.1
schema: v1

models:
	- name: GPT-6 Luna
		provider: openai
		model: gpt-6-luna
		apiKey: ${{ secrets.OPENAI_API_KEY }}
		roles:
			- chat
			- edit
			- apply
```

Ulož konfiguráciu. V paneli Continue vyber **GPT-6 Luna** ako model a odošli skúšobnú správu. Model ID `gpt-6-luna` je názov používaný v OpenAI API; dostupnosť modelu sa môže líšiť podľa organizácie alebo účtu. Aktuálny zoznam a ceny nájdeš v [katalógu modelov OpenAI](https://developers.openai.com/api/docs/models) a na stránke [cenníka](https://developers.openai.com/api/docs/pricing).

## Riešenie častých problémov

- **Incorrect API key**: over, či je v `%USERPROFILE%\.continue\.env` správny kľúč, bez úvodzoviek a medzier navyše. Ak si pôvodný kľúč neuložil, vytvor nový.
- **Insufficient quota alebo billing error**: skontroluj zostatok API kreditu a fakturáciu. Predplatné ChatGPT tento zostatok nedopĺňa.
- **Model not found alebo access denied**: skontroluj presný názov `gpt-6-luna` a to, či je model dostupný pre vybranú OpenAI organizáciu.
- **Continue nevidí nové nastavenie**: ulož oba súbory, znova otvor Continue alebo reštartuj VS Code.

## Odkazy

- [OpenAI Platform](https://platform.openai.com/)
- [OpenAI API Billing](https://platform.openai.com/account/billing)
- [OpenAI API keys](https://platform.openai.com/api-keys)
- [Dokumentácia Continue pre OpenAI](https://docs.continue.dev/customize/model-providers/top-level/openai)
- [Bezpečnostné odporúčania pre API kľúče](https://help.openai.com/en/articles/5112595)

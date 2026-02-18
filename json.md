# JSON: Dátový Štandard pre Modernú AI  
Tento dokument vysvetľuje formát JSON a jeho kľúčovú úlohu v ekosystéme umelej  
inteligencie. Cieľom je poskytnúť komplexný prehľad pre vývojárov, data  
engineerov a AI špecialistov pracujúcich so štruktúrovanými dátami.  

## 1. Úvod do formátu JSON  

JSON (JavaScript Object Notation) je ľahký textový formát na výmenu dát,  
ktorý navrhol Douglas Crockford v roku 2001. Je ľahko čitateľný pre ľudí a  
jednoducho spracovateľný pre stroje. Hoci vychádza z JavaScriptu (ECMA-262),  
je úplne nezávislý od programovacieho jazyka a podporujú ho takmer všetky  
moderné technológie a platformy.  

**Prečo JSON dominuje v AI a webovom vývoji?**  
- **Štruktúra:** Narozdiel od voľného textu (Markdown) má JSON striktné  
  pravidlá, ktoré umožňujú programom presne parsovať a validovať odpovede  
  od AI bez ambiguit.  
- **Univerzálnosť:** Je to "lingua franca" pre API volania, mikroslužby a  
  webové služby naprieč všetkými jazykmi (Python, JS, Java, C#, Go, Rust).  
- **Ľahkosť:** Minimálna syntax s nízkym overheadom oproti XML, čo znižuje  
  prenosové nároky a zrýchľuje spracovanie.  
- **Hierarchia:** Podpora vnorených objektov a polí umožňuje reprezentovať  
  komplexné dátové štruktúry prirodzeným spôsobom.  

## 2. Základná Syntax a Typy Dát  

JSON sa skladá z párov **kľúč: hodnota**, kde kľúče sú vždy reťazce v  
dvojitých úvodzovkách a hodnoty môžu byť rôznych typov.  

```json  
{  
  "meno": "AI Asistent",  
  "verzia": 4.0,  
  "je_aktivny": true,  
  "schopnosti": ["text", "kód", "analýza", "obraz"],  
  "meta_data": {  
    "autor": "OpenAI",  
    "rok_vydania": 2024,  
    "licencia": null  
  },  
  "statistiky": {  
    "pouziti": 15420,  
    "priemerny_cas_odpovede_ms": 245.7  
  }  
}  
```  

**Podporované primitívne typy:**  
- **String:** Text v dvojitých úvodzovkách `"text"`; podpora Unicode a  
  escape sekvencií (`\n`, `\t`, `\\`, `\"`, `\uXXXX`).  
- **Number:** Čísla bez rozlíšenia celých/desatinných `123`, `-45.67`,  
  `1.23e-4`; žiadne leading zeros, NaN ani Infinity nie sú platné.  
- **Boolean:** Logické hodnoty `true` / `false` (malými písmenami).  
- **Null:** Prázdna hodnota `null` (nie `"null"` ani `undefined`).  

**Kompozitné typy:**  
- **Array:** Usporiadaný zoznam hodnôt v hranatých zátvorkách `[1, 2, 3]`;  
  môže obsahovať zmiešané typy a vnorené štruktúry.  
- **Object:** Neusporiadaná kolekcia párov kľúč-hodnota v zložených  
  zátvorkách `{"k": "v"}`; kľúče musia byť unikátne reťazce.  

> **Dôležité:** JSON nepodporuje komentáre, funkcie, dátumy ani binárne  
> dáta priamo – tieto sa musia reprezentovať ako reťazce alebo čísla.  

## 3. JSON vs. Iné Formáty  

Výber správneho dátového formátu je kritický pre výkon, udržiavateľnosť a  
spoľahlivosť AI systémov. JSON nie je vždy univerzálne najlepšia voľba –  
každý formát má svoje silné a slabé stránky v závislosti od use case.  
Nasledujúce porovnanie pomáha pri rozhodovaní, kedy použiť JSON a kedy  
zvoliť alternatívu. Pri integrácii AI modelov sa často kombinuje viac  
formátov: JSON pre API komunikáciu, YAML pre konfiguráciu a Protobuf pre  
high-performance interné služby. Kľúčové je pochopiť trade-offs medzi  
čitateľnosťou, výkonom a ekosystémovou podporou.  

| Formát   | Výhody                          | Nevýhody                     | Vhodné pre            |  
| :------- | :------------------------------ | :--------------------------- | :-------------------- |  
| **JSON** | Univerzálny, ľahký, široká podpora | Žiadne komentáre, verbose kľúče | API, AI výstupy, config |  
| **YAML** | Čitateľný, komentáre, menej syntax | Pomalší parsing, indent-sensitive | Konfiguračné súbory   |  
| **XML**  | Schéma, namespace, validácia    | Veľký overhead, komplexný    | Legacy enterprise systémy |  
| **Protobuf** | Kompaktný, rýchly, typovaný   | Binárny, vyžaduje .proto schému | High-performance RPC  |  
| **CSV**  | Jednoduchý, tabuľkový           | Žiadna hierarchia, žiadne typy | Export dát, analytics |  

**Kedy zvoliť JSON:**  
- Pri komunikácii s webovými API a AI službami (OpenAI, Anthropic, Gemini)  
- Keď potrebujete ľudsky čitateľný formát pre debugging a logovanie  
- Pre štruktúrované výstupy z LLM, ktoré budú ďalej spracovávané kódom  
- Pri práci s JavaScript/TypeScript ekosystémom (natívna podpora)  

**Kedy zvoliť alternatívu:**  
- **YAML:** Pre konfiguračné súbory, kde sú komentáre a čitateľnosť kľúčové  
- **Protobuf/gRPC:** Pre high-frequency internú komunikáciu medzi mikroservisami  
- **CSV/Parquet:** Pre batch analytics a veľké tabuľkové datasety  
- **MessagePack/CBOR:** Pre binárnu serializáciu s nižším overheadom v IoT/edge scenároch  

> **Tip:** V AI pipeline sa často používa hybridný prístup: YAML pre  
> konfiguráciu modelu, JSON pre runtime komunikáciu a Protobuf pre  
> vysokovýkonné inferencie. Zvoľte formát podľa fázy a účelu použitia.

## 4. JSON a Umelá Inteligencia (AI)  

V oblasti AI má JSON tri hlavné využitia, ktoré sú kritické pre spoľahlivú  
integráciu modelov do produkčných systémov:  

### A. Štruktúrovaný Výstup (Structured Output)  
Keď integrujete AI do aplikácie, nepotrebujete voľný text, ale strojovo  
čitateľné dáta. Moderné API (ako OpenAI JSON Mode, Anthropic Tools, Gemini  
Structured Outputs) umožňujú vynútiť, aby AI odpovedala výlučne v JSON  
formáte podľa zadanej schémy.  

**Príklad promptu:**  
```  
Analyzuj sentiment recenzie a vráť JSON s nasledujúcou štruktúrou:  
- sentiment_score: číslo 1-10  
- keywords: pole kľúčových slov  
- recommended: boolean  
```  

**Výstup AI:**  
```json  
{  
  "sentiment_score": 8,  
  "keywords": ["rýchly", "spoľahlivý", "drahý", "kvalita"],  
  "recommended": true,  
  "confidence": 0.92  
}  
```  

> **Tip:** Vždy definujte očakávanú štruktúru v prompte alebo použite  
> JSON Schema parameter v API volaní pre maximálnu spoľahlivosť.  

### B. Volanie Funkcií (Function Calling / Tool Use)  
AI modely dnes dokážu autonómne ovládať externé nástroje a API. Model na  
základe intentu používateľa vygeneruje JSON, ktorý obsahuje názov funkcie,  
argumenty a prípadne ID volania pre sledovanie.  

**Scenár:** Používateľ sa pýta: *"Aké bude počasie v Bratislave zajtra?"*  
**AI vygeneruje tool call:**  
```json  
{  
  "tool_call_id": "call_abc123",  
  "function": {  
    "name": "get_weather_forecast",  
    "arguments": {  
      "location": "Bratislava, SK",  
      "date": "2024-02-19",  
      "unit": "metric"  
    }  
  }  
}  
```  

**Výhody JSON pre tool calling:**  
- Jednoznačná identifikácia funkcie a parametrov  
- Jednoduchá validácia vstupov pred vykonaním  
- Možnosť serializácie do logov a audit trail  
- Kompatibilita s väčšinou backend systémov  

### C. Trénovacie a Fine-Tuning Dáta (JSONL)  
Pre trénovanie a fine-tuning AI modelov sa štandardne používa formát  
**JSON Lines (JSONL/NDJSON)**, kde každý riadok súboru je samostatný,  
platný JSON objekt.  

**Príklad datasetu pre inštrukčný fine-tuning:**  
```jsonl  
{"messages": [{"role": "user", "content": "Ahoj"}, {"role": "assistant", "content": "Dobrý deň, ako vám pomôžem?"}]}  
{"messages": [{"role": "user", "content": "Čo je JSON?"}, {"role": "assistant", "content": "JSON je ľahký dátový formát..."}]}  
{"messages": [{"role": "user", "content": "Vypočítaj 2+2"}, {"role": "assistant", "content": "Výsledok je 4."}]}  
```  

**Best practices pre JSONL datasets:**  
- Každý riadok musí byť samostatne platný JSON (žiadne čiarky medzi riadkami)  
- Používajte UTF-8 encoding bez BOM pre maximálnu kompatibilitu  
- Veľké datasety komprimujte gzip (`.jsonl.gz`) pre úsporu miesta  
- Validujte schému každého záznamu pred odoslaním na trénovanie  

## 5. JSON Schema: Definícia a Validácia  

JSON Schema je špecifikácia na popis štruktúry, typov a obmedzení JSON  
dát. Používa sa na validáciu vstupov/výstupov, generovanie dokumentácie a  
ako "kontrakt" medzi AI a aplikáciou.  

**Príklad schémy pre AI výstup:**  
```json  
{  
  "$schema": "https://json-schema.org/draft/2020-12/schema",  
  "$id": "https://example.com/ai-response.schema.json",  
  "title": "AI Analysis Response",  
  "type": "object",  
  "properties": {  
    "id": {  
      "type": "string",  
      "format": "uuid",  
      "description": "Unikátny identifikátor odpovede"  
    },  
    "sentiment_score": {  
      "type": "number",  
      "minimum": 1,  
      "maximum": 10,  
      "description": "Hodnotenie sentimentu od 1 (negatívny) po 10 (pozitívny)"  
    },  
    "keywords": {  
      "type": "array",  
      "items": {"type": "string"},  
      "maxItems": 10,  
      "description": "Zoznam extrahovaných kľúčových slov"  
    },  
    "recommended": {  
      "type": "boolean",  
      "description": "Či je produkt/odporúčanie pozitívne"  
    }  
  },  
  "required": ["id", "sentiment_score", "keywords", "recommended"],  
  "additionalProperties": false  
}  
```  

**Kľúčové vlastnosti JSON Schema:**  
- `type`: Definuje dátový typ (string, number, boolean, array, object, null)  
- `enum`: Obmedzuje hodnoty na preddefinovaný zoznam `["low", "medium", "high"]`  
- `pattern`: Regex validácia pre reťazce `"pattern": "^\\d{4}-\\d{2}-\\d{2}$"`  
- `minLength` / `maxLength`: Obmedzenie dĺžky textu  
- `minimum` / `maximum`: Číselné obmedzenia  
- `required`: Zoznam povinných kľúčov  
- `additionalProperties: false`: Zakáže neočakávané polia (strikná validácia)  

> **Pro tip:** Používajte `$ref` na opakovane použiteľné definície a  
- `allOf`/`oneOf`/`anyOf` pre komplexnejšie logické podmienky v schémach.  

## 6. Bezpečnosť a Robustnosť pri Spracovaní JSON  

Pri práci s JSON z AI modelov alebo externých zdrojov je kritické dodržiavať  
bezpečnostné praktiky:  

### Potenciálne riziká  
- **Neplatný JSON:** AI môže vygenerovať mierne neplatný JSON (chýbajúca  
  čiarka, nesprávne úvodzovky) – vždy používajte tolerantné parsery alebo  
  retry logiku.  
- **JSON Injection:** Ak vkládate používateľský vstup do JSON bez escapovania,  
  môže dôjsť k narušeniu štruktúry alebo RCE v niektorých kontextoch.  
- **Veľké payloady:** AI môže vygenerovať extrémne dlhý JSON – nastavte  
  limity na veľkosť odpovede a timeouty.  
- **Nested depth attacks:** Hlboko vnorené objekty môžu spôsobiť stack  
  overflow pri parsingu – limitujte maximálnu hĺbku.  

### Odporúčané ochranné opatrenia  
1. **Vždy validujte:** Používajte `JSON.parse()` s try-catch alebo  
- špecializované validátory (ajv, jsonschema) pred spracovaním.  
2. **Sanitizujte vstupy:** Escape-ujte používateľské dáta pred vložením do  
- JSON šablón alebo promptov.  
3. **Používajte strict mode:** V nastaveniach AI API zapnite JSON mode a  
- poskytnite JSON Schema pre vynútenie formátu.  
4. **Logujte a monitorujte:** Ukladajte surové AI odpovede pre debugging a  
- detekciu anomálií v štruktúre výstupov.  
5. **Rate limiting:** Obmedzte počet požiadaviek na AI API, aby sa predišlo  
- zneužitiu na generovanie veľkého množstva dát.  

## 7. Praktické Ukážky a Reálne Scenáre  

### Scenár 1: Extrakcia dát z voľného textu  
**Prompt:**  
```  
Extrahuj z nasledujúcej recenzie meno produktu, cenu a hodnotenie:  
"Kúpil som si SuperPhone X za 899 eur a som veľmi spokojný, dávam 5 hviezdičiek!"  
```  

**Očakávaný JSON výstup:**  
```json  
{  
  "product_name": "SuperPhone X",  
  "price": {  
    "amount": 899,  
    "currency": "EUR"  
  },  
  "rating": 5,  
  "sentiment": "positive"  
}  
```  

### Scenár 2: Multi-step workflow s tool calling  
```json  
{  
  "workflow_id": "wf_789",  
  "steps": [  
    {  
      "step": 1,  
      "action": "search_database",  
      "params": {"query": "klienti s dlhom > 1000", "limit": 50}  
    },  
    {  
      "step": 2,  
      "action": "analyze_risk",  
      "params": {"client_ids": ["$result.step1[*].id"], "model": "risk_v2"}  
    },  
    {  
      "step": 3,  
      "action": "generate_report",  
      "params": {"format": "pdf", "include_charts": true}  
    }  
  ]  
}  
```  

### Scenár 3: Batch processing s JSONL  
```jsonl  
{"batch_id": "b001", "task": "classify", "input": "Text A...", "priority": 1}  
{"batch_id": "b001", "task": "classify", "input": "Text B...", "priority": 2}  
{"batch_id": "b001", "task": "classify", "input": "Text C...", "priority": 1}  
```  

## 8. Najlepšie Praktiky pre AI a JSON  

### Pri tvorbe promptov a schém  
- Používajte krátke, deskriptívne kľúče (`"score"` namiesto `"sentiment_analysis_score_value"`)  
  pre úsporu tokenov a lepšiu čitateľnosť.  
- Definujte `enum` pre polia s obmedzenými hodnotami – znižuje halucinácie AI.  
- Pridávajte `description` k poliam v JSON Schema – pomáha modelu pochopiť  
  zámer a kontext každého poľa.  
- Pre komplexné úlohy rozdeľte výstup do vnorených objektov namiesto  
  plochej štruktúry – zlepšuje organizáciu a extenzibilitu.  

### Pri spracovaní výstupov  
- **Vždy parsujte s error handling:** Nikdy nepredpokladajte, že AI vygeneruje  
  100% platný JSON – implementujte fallback logiku.  
- **Normalizujte dáta:** Prevádzajte reťazce na čísla, dátumy na ISO formát,  
  enum hodnoty na lowercase pre konzistentné ďalšie spracovanie.  
- **Odstraňujte nadbytočné polia:** Ak AI pridá `additionalProperties`,  
  filtrujte iba tie, ktoré potrebujete podľa schémy.  
- **Cache-ujte schémy:** Pri častej validácii používajte kompilované JSON  
  Schema objekty namiesto parsovania schémy pri každom volaní.  

### Pre výkon a náklady  
- Minimalizujte hĺbku vnorenia – každý level zvyšuje token count a  
  komplikuje parsing.  
- Používayte `null` namiesto vynechaných voliteľných polí, ak potrebujete  
  explicitnú prítomnosť kľúča v štruktúre.  
- Pre veľké zoznamy zvažujte pagináciu v JSON odpovediach (`"items"`,  
  `"next_cursor"`, `"has_more"`).  
- Komprimujte JSON payloady pri prenose (gzip, brotli) pre úsporu bandwidth.  

## 9. Nástroje a Knihovny  

### Validácia a práca so schémami  
- **Python:** `jsonschema`, `pydantic`, `fastjsonschema`  
- **JavaScript/TS:** `ajv`, `zod`, `joi`  
- **Java:** `json-schema-validator`, `everit-org/json-schema`  
- **CLI:** `ajv-cli`, `jq` pre manipuláciu a query JSON  

### Debugging a vizualizácia  
- **JSONLint:** Online validátor a formátovač  
- **JSON Crack:** Vizualizácia JSON štruktúry ako graf  
- **VS Code:** Built-in JSON validation + schéma IntelliSense  
- **Postman/Insomnia:** Testovanie API s JSON request/response  

### Konverzia a transformácia  
- **jq:** Mocný CLI nástroj na filter/map/transform JSON  
- **JQPlay:** Online playground pre jq príkazy  
- **Pandas (Python):** `read_json()` / `to_json()` pre analýzu  
- **xmllint / yq:** Konverzia medzi JSON, XML, YAML  

## 10. Súhrn Syntax (Cheat Sheet)  

### Základná štruktúra  
```json  
{  
  "string_key": "hodnota",  
  "number_key": 42,  
  "float_key": 3.14,  
  "bool_key": true,  
  "null_key": null,  
  "array_key": [1, "two", false],  
  "object_key": {"nested": "value"}  
}  
```  

### Escape sekvencie v reťazcoch  
- `\"` – dvojitá úvodzovka  
- `\\` – spätné lomítko  
- `\/` – lomítko (voliteľné)  
- `\b` – backspace, `\f` – form feed  
- `\n` – nový riadok, `\r` – carriage return  
- `\t` – tabulátor  
- `\uXXXX` – Unicode znak (napr. `\u0041` = "A")  

### Časté chyby a ako sa im vyhnúť  
| Chyba | Príklad | Oprava |  
| :---- | :------ | :----- |  
| Single quotes | `{'key': 'val'}` | Použi dvojitú: `{"key": "val"}` |  
| Trailing comma | `{"a": 1,}` | Odstráň poslednú čiarku |  
| Comments | `{"a": 1 // comment}` | JSON nepodporuje komentáre |  
| Undefined/NaN | `{"val": NaN}` | Použi `null` alebo string |  
| Leading zero | `{"num": 0123}` | Použi `123` alebo `"0123"` |  

### JSONL formát (každý riadok samostatný JSON)  
```jsonl  
{"id": 1, "event": "click"}  
{"id": 2, "event": "view", "duration_ms": 1500}  
{"id": 3, "event": "purchase", "amount": 29.99}  
```  

> **Poznámka:** V JSONL nesmie byť čiarka medzi objektmi a súbor by mal  
> končiť newline charakterom pre maximálnu kompatibilitu s nástrojmi.  

## 11. Záver a Ďalšie Zdroje  

JSON je fundamentálny stavebný kameň modernej AI architektúry. Jeho  
jednoduchosť, univerzálnosť a strojová čitateľnosť z neho robia ideálny  
most medzi ľudskými promptmi a automatizovanými systémami.  

**Kľúčové takeaways:**  
- Používaj JSON pre štruktúrované AI výstupy a tool calling  
- Validuj každý vstup/výstup pomocou JSON Schema  
- Minimalizuj tokeny krátkymi kľúčmi a plochou štruktúrou  
- Priprav sa na neplatný JSON – implementuj robustný error handling  

**Odporúčané zdroje na ďalšie štúdium:**  
- [JSON.org](https://www.json.org/) – oficiálna špecifikácia a intro  
- [JSON Schema](https://json-schema.org/) – kompletná dokumentácia schém  
- [NDJSON/JSONL spec](http://ndjson.org/) – špecifikácia pre line-delimited JSON  
- [OpenAI Structured Outputs](https://platform.openai.com/docs/guides/structured-outputs) – AI špecifické best practices  
- [AJV Docs](https://ajv.js.org/) – najrýchlejší JSON Schema validátor  

*Tip na záver:* Začni s jednoduchou schémou, iteratívne ju rozširuj podľa  
potrieb a vždy testuj edge cases – AI môže byť kreatívna aj v JSONe!

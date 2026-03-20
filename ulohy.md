# Úlohy


Pomocou AI nástrojov, spľn tieto úlohy:

- nájdi všetky slová týkajúce sa oblečenia a pridaj EN,FR,GER,HU eqvivalenty  
https://www.youtube.com/watch?v=ITs9agntW18

- prelož prvú stranu knihy Jane Eyre
- zosumarizuj knihu Neprebudený
- spočítaj počet iregulárnych podstatných mien v knihe Otec Goriot (English)


https://huggingface.co/spaces/ACE-Step/ACE-Step


## Extrakcia dát

Tu je vzorový životopis. Z tohto životopisu vytiahni: meno, poslednú pozíciu, 3 kľúčové zručnosti.

```
**ŽIVOTOPIS**

**Osobné údaje:**
Meno a priezvisko: Ing. Peter Horský
Bydlisko: Lipová 12, 811 02 Bratislava
Telefón: +421 900 111 222
Email: p.horsky@email.sk

**Pracovné skúsenosti:**

**Senior Projektový Manažér | TechSolutions s.r.o.**
*Január 2019 – Súčasnosť*
* Zodpovednosť za riadenie vývojových tímov (15+ ľudí).
* Implementácia agilných metodík (Scrum, Kanban) do procesov firmy.
* Komunikácia s medzinárodnými klientmi a rozpočtovanie projektov v objeme nad 200 000 €.

**IT Analytik | DataCorp a.s.**
*Marec 2015 – December 2018*
* Analýza biznis požiadaviek a ich transformácia do technických špecifikácií.
* Práca s SQL databázami a vizualizácia dát v nástroji Power BI.

**Zručnosti a kompetencie:**
* **Projektové riadenie:** Certifikácia PRINCE2, hĺbková znalosť metodiky Agile a nástroja Jira.
* **Dátová analýza:** Pokročilá práca s SQL, základy programovacieho jazyka Python a štatistické vyhodnocovanie dát.
* **Cudzí jazyk:** Anglický jazyk na úrovni C1 (slovom aj písmom) – denná komunikácia v zahraničnom tíme.

**Vzdelanie:**
Slovenská technická univerzita v Bratislave
Fakulta informatiky a informačných technológií
Odbor: Informačné systémy (Inžiniersky stupeň)
```

## Očakávaný výsledok

```json
{
  "meno": "Ing. Peter Horský",
  "posledná_pozícia": "Senior Projektový Manažér",
  "kľúčové_zručnosti": [
    "Projektové riadenie (Agile, Scrum, PRINCE2)",
    "Dátová analýza (SQL, Python)",
    "Anglický jazyk (úroveň C1)"
  ]
}
```

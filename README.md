# Kalkulačka provizí

Webová kalkulačka pro rozdělení fee z uzavřeného dealu mezi lidi, holding
a oddělení. Interní nástroj dsp collective s.r.o.

- **Živá verze:** https://jiristehlik.github.io/provize/ (GitHub Pages, větev `main`)
- **Lokální pracovní kopie:** `~/agenti/provize-kalkulacka/`
- **Vlastník:** Jirka

## Jak to spustit

Žádný build, žádné závislosti. Stačí otevřít `index.html` v prohlížeči:

```bash
open index.html
```

## Struktura

Celá aplikace je **jeden soubor** `index.html` — HTML, CSS i JavaScript pohromadě.
Orientační body:

| Část | Kde |
|---|---|
| Styly | `<style>` blok na začátku |
| Ukládání dealů (localStorage) | funkce `loadHistory` / `saveDeal` / `renderHistory` |
| Číselníky (oddělení, lidé, role) | konstanty `DEPARTMENTS`, `BROKERS`, `ROLES` |
| Vlastní výpočet | funkce `calculate()` |
| Vykreslení výsledku | funkce `renderResults()` |

**Uložené dealy žijí jen v `localStorage` prohlížeče** (klíč `provize_history`) —
neukládají se nikam na server a nepřenášejí se mezi počítači ani prohlížeči.
Vymazání dat prohlížeče je nenávratně smaže.

## Změna seznamu lidí

Lidé jsou natvrdo v konstantě `BROKERS`. Každý záznam má oddělení a koeficient,
kterým se řídí, jaká část jeho podílu připadne jemu a jaká jeho oddělení.
Seznam může obsahovat i bývalé členy týmu — kvůli přepočtu historických dealů.

## Nasazení

Push do větve `main` = nasazení. GitHub Pages přegenerují web zpravidla
do minuty, pak stačí ve stránce tvrdý reload (Cmd+Shift+R).

## Kde jsou pravidla

Závazný popis provizního modelu (role, sazby, koeficienty, výjimky oddělení)
je v interní znalostní bázi DSP COLLECTIVE — `reference/cenotvorba-a-provize.md`.
**Při změně výpočtu v kódu je potřeba srovnat i tento dokument**, aby se pravidla
a nástroj nerozešly.

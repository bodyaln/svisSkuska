# Skúškové otázky – tréning

Kvíz na prípravu na skúšku. Statická stránka: `index.html` (aplikácia) + `questions.json` (otázky).

## Spustenie lokálne

Stránka načítava `questions.json` cez `fetch`, preto ju treba otvoriť cez lokálny server, nie dvojklikom:

```
python3 -m http.server 8000
# alebo
npx serve .
```

Potom otvor http://localhost:8000

## Pridanie otázky

Do `questions.json` pridaj jeden riadok (pozor na čiarku za predchádzajúcim riadkom):

```json
{"id": "D36", "lec": "D", "n": 36, "q": "Text otázky?", "o": ["možnosť a", "možnosť b", "možnosť c"], "c": [1], "ex": "Prečo je správne b a ostatné nie."}
```

- `id` – unikátny kľúč (písmeno prednášky + číslo), podľa neho sa ukladá pokrok
- `lec` – písmeno prednášky (A, B, C, D, …)
- `n` – číslo otázky v rámci prednášky (určuje poradie v režime „Po poradí“)
- `o` – možnosti, 3 až 5
- `c` – indexy správnych možností od nuly: `[0]` = a), `[0, 2]` = a) a c)
- `ex` – vysvetlenie (nepovinné)

## Nová prednáška

V `index.html` v objekte `LECS` pridaj riadok, napr. `E:{name:'Názov prednášky', color:'#f43f5e'}`.
Bez toho sa prednáška zobrazí ako „Prednáška E“ so sivou farbou.

## Telefón a offline (PWA)

Po nasadení (GitHub Pages / Vercel) otvor stránku v telefóne:
- iPhone: Safari → Zdieľať → **Pridať na plochu**
- Android: Chrome → ⋮ → **Pridať na plochu / Inštalovať aplikáciu**

Po prvom otvorení funguje aj bez internetu. Pri online otvorení sa vždy stiahne aktuálny `questions.json`.
Ak zmeníš `index.html` a zmena sa neprejaví, zvýš `CACHE` verziu v `sw.js` (`skuska-v2`).

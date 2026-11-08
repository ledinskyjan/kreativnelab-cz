# kreativnelab-cz

Web Kreativně labilní na [kreativnelab.cz](https://kreativnelab.cz). Statické stránky bez buildu, GitHub Pages publikuje větev `main`.

- `index.html` česká verze, `en/index.html` anglická (stejné CSS i skript, liší se jen texty)
- `pravni-informace/`, `ochrana-osobnich-udaju/`, `en/legal/`, `en/privacy/`, `404.html` mají vlastní kopii CSS
- `znacka/` a `en/brand/` jsou stránky se značkou ke stažení (jen na přímý odkaz)

## Homepage

1. **Hero**: logotyp, jedna věta, jedna akce. Řádky jsou zalomené natvrdo (`br-d` počítač, `br-m` telefon), po změně textu je přeměřit.
2. **Ozvěte se nám, když…** (`#jak`, EN `#how`): situace, ve kterých se klient pozná.
3. **Nápad je začátek. Provoz je důkaz.** (`.say`): výrazový předěl.
4. **Kdo za tím je** (`#o-nas`, EN `#about`).
5. **Kontakt** (`#kontakt`, EN `#contact`): tři začátky rozhovoru a formulář (Formspree).

Web nemá obsahovat nic, co vyžaduje průběžnou ruční aktualizaci: žádné přehledy projektů, data stavu ani harmonogramy.

Menu: Kdy se ozvat a Kdo za tím je. Pod 760 px se odkazy schovají pod tlačítko Menu. Stejné odkazy jsou v patičce homepage i podstránek, při změně sekcí je potřeba srovnat je všude.

Tento soubor se na web nepublikuje (`_config.yml`).

## Texty

Čemu se vyhnout: „nezapomenutelné zážitky“, „řešení na míru“, „od A do Z“, „komplexní servis“ a podobně. Bez dlouhých pomlček.

## Dvě vrstvy vizuálu

- **Stabilní**: černé písmo, pevný grid, linky, navigace. Nehýbe se.
- **Labilní**: modrá `#3155FF`. Poznámky (`.ans`, `.ann`), vychýlená písmena (`data-tilt`, úhly z loga), rám `.fr`. Jen tahle vrstva smí z gridu vystoupit.
- Pohupování (`data-labil`) má jen slovo labilní v hero, patičce a na 404.
- Všechno se řídí `prefers-reduced-motion`: bez animací se vrstvy rovnou ukážou v konečné poloze.

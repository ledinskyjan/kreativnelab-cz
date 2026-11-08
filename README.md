# kreativnelab-cz

Web Kreativně labilní na [kreativnelab.cz](https://kreativnelab.cz). Statické stránky bez buildu, GitHub Pages publikuje větev `main`.

- `index.html` česká verze, `en/index.html` anglická (stejné CSS i skript, liší se jen texty)
- `pravni-informace/`, `ochrana-osobnich-udaju/`, `en/legal/`, `en/privacy/`, `404.html` mají vlastní kopii CSS
- `znacka/` a `en/brand/` jsou stránky se značkou ke stažení (jen na přímý odkaz)

## Homepage

1. **Hero**: logotyp, jedna věta, dvě akce. Řádky jsou zalomené natvrdo (`br-d` počítač, `br-m` telefon), po změně textu je přeměřit.
2. **Právě teď v labu** (`#projekty`, EN `#projects`): živý index projektů. Oblast Studio / Originals / Space je sloupec, ne tři služby.
3. **Práce** (`#prace`, EN `#work`): vybrané projekty jako příběhy s produkčním deníkem.
4. **Ozvěte se nám, když…** (`#jak`, EN `#how`): situace, ve kterých se klient pozná.
5. **Kdo za tím je** (`#o-nas`, EN `#about`).
6. **Kontakt** (`#kontakt`, EN `#contact`): tři začátky rozhovoru a formulář (Formspree).

Mezi sekcemi stojí krátké názorové věty (`.say`). Staré kotvy `#jak`, `#o-nas`, `#projekty`, `#kontakt` zůstaly, aby fungovaly dřívější odkazy.

Menu: Práce vede na začátek indexu (`#projekty`), Vlastní a Prostor rovnou otevřou svůj řádek. Pod 980 px se sekce schovají pod tlačítko Menu.

Tento soubor se na web nepublikuje (`_config.yml`).

## Jak aktualizovat „Právě teď v labu“

Každý řádek je jeden `<li class="idx-item">`. Při každé změně přepsat i datum `Stav k …` a udělat totéž v obou jazycích.

| `data-st` | CZ | EN | Vzhled |
|---|---|---|---|
| `live` | živé | live | modrý plný štítek |
| `dev` | ve vývoji | in development | modrý, natočený |
| `prep` | připravujeme | in the works | modrý, natočený |
| `prod` | produkce | in production | modrý, natočený |
| `search` | hledáme | searching | modrý, natočený |
| `secret` | zatím tajné | under wraps | čárkovaný, název začerněný (`.redact`) |
| `done` | dokončeno | done | černý a rovný: hotové je stabilní |

Nový řádek: zkopírovat celý `<li class="idx-item">`, změnit `aria-controls` tlačítka a `id` panelu (musí si odpovídat). Řádek s `id` jde otevřít odkazem, např. `/#vlastni` nebo `/#prostor`. Když panel obsahuje fotku (`<figure class="shot">`), ukáže se na počítači i po najetí myší na řádek.

## Šablona projektu (sekce Práce)

```html
<article class="case" id="nazev-projektu" aria-labelledby="case-nazev">
  <div class="case-meta reveal"><span class="st" data-st="done">dokončeno</span><span>Studio</span></div>
  <h3 id="case-nazev" class="case-name fr reveal">Název</h3>
  <p class="case-line reveal">Jedna věta s měřítkem. Čísla, ne přídavná jména.</p>

  <figure class="shot case-media">
    <img src="/assets/projekty/nazev-projektu/hlavni.webp" width="2000" height="1125" alt="Co je na fotce" loading="lazy" decoding="async" />
    <figcaption><b>19:48</b> · hlavní stage</figcaption>
  </figure>

  <div class="case-grid reveal">
    <div>
      <h4 class="lbl">Co bylo na nás</h4>
      <ul class="roles"><li>produkční vedení</li><li>…</li></ul>
    </div>
    <p class="case-quote">Jedna názorová věta s <span data-tilt>vychýleným</span> slovem.</p>
  </div>

  <div class="diary-wrap reveal">
    <h4 class="lbl">Jeden den v provozu</h4>
    <ol class="diary">
      <li><time>08:40</time><p>prázdný prostor</p></li>
      <!-- 4 až 6 momentů; u každého může být <figure class="shot"> s fotkou -->
      <li class="end"><time>23:10</time><p><span data-tilt>pořád to funguje</span></p></li>
    </ol>
  </div>
</article>
```

Co musí mít každý projekt: název, roli Kreativně labilní, měřítko (lidé, plocha, dny, počet partnerů), jeden konkrétní výsledek a souhlas klienta se zveřejněním. Když název zveřejnit nejde, projekt se popíše anonymně: typ realizace, měřítko a role.

Čemu se v textech vyhnout: „nezapomenutelné zážitky“, „řešení na míru“, „od A do Z“, „komplexní servis“ a podobně. Bez dlouhých pomlček.

## Fotky a video

- Vlastní dokumentární fotky: celky s lidmi, backstage, stavba, prázdný prostor před otevřením, značení, lidé při práci. Žádné fotobanky ani moodové fotky.
- Formát WebP (nebo AVIF), delší strana nejvýš 2000 px, cíl do 350 kB. Vždy `width`, `height`, `alt` a `loading="lazy"` (kromě první fotky na obrazovce).
- Video jen jako krátká smyčka bez zvuku: MP4 (H.264), 6 až 12 s, do 3 MB, `autoplay muted loop playsinline` a `poster`. Při omezeném pohybu se samo nespustí.
- Popisek nese čas, místo nebo stav: `<figcaption><b>15:30</b> · otevíráme dveře</figcaption>`.
- Složka `assets/projekty/<nazev-projektu>/`.

## Dvě vrstvy vizuálu

- **Stabilní**: černé písmo, pevný grid, linky, čísla, časy, fakta, navigace. Nehýbe se.
- **Labilní**: modrá `#3155FF` (na tmavém `#6B85FF`). Statusy, poznámky (`.ans`, `.ann`), vychýlená písmena (`data-tilt`, úhly z loga), rám `.fr`, posun řádku po najetí. Jen tahle vrstva smí z gridu vystoupit.
- Pohupování (`data-labil`) má jen slovo labilní v hero, patičce a na 404.
- Všechno se řídí `prefers-reduced-motion`: bez animací se vrstvy rovnou ukážou v konečné poloze.

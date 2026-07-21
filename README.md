# Krotitelé nábytku — web

Statický web s čistými adresami (bez .html). Struktura:

| Cesta | Co to je |
|---|---|
| `index.html` | úvodní stránka → krotitelenabytku.cz/ |
| `nabytek/`, `renovace/`, `vykup/`, `kontakt/` | podstránky → /nabytek/ atd. |
| `dekujeme/`, `soukromi/` | děkovačka formuláře, ochrana údajů |
| `nabytek.html` … (v kořeni) | přesměrovací pahýly ze starých adres — nemazat |
| `fotky/`, `fonts/` | obrázky a vlastní písma |
| `style.css`, `sitemap.xml`, `robots.txt`, `.nojekyll`, `CNAME` | zázemí |

**Lokální náhled:** web používá absolutní cesty (`/style.css`), takže otevření souboru
napřímo už nestačí. Ve složce spusťte `python3 -m http.server` a otevřete
http://localhost:8000 — nebo koukejte rovnou na živý web.

## Nasazení změn

Obsah této složky = obsah repozitáře (včetně podsložek). Soubor **CNAME
v repozitáři vždy zachovat** (drží doménu; obsahuje řádek `krotitelenabytku.cz`).
Přes Claude Code: „přepiš obsah repozitáře obsahem složky web, zachovej CNAME,
commitni a pushni". Ručně: GitHub → Add file → Upload files → přetáhnout obsah složky.

## Kusy a fotky

- Nový kus = zkopírovat kartu v `nabytek/index.html`. Prodané nemazat,
  jen přepnout štítek na `badge--prodano` — jsou to reference.
- Nová fotka: uložit do `fotky/` a vložit
  `<img src="/fotky/nazev.jpg" alt="popis kusu" class="foto">`.
- Čekající šablony v komentářích: karta stolu (nabytek), společná fotka
  (index, sekce Kdo jsme), fotka z práce (renovace), odkaz na Krotitele
  chaosu (index, patička).

## Po nasazení nové struktury

V Search Console požádat o indexaci čistých adres: `/`, `/nabytek/`,
`/renovace/`, `/vykup/`, `/kontakt/`. Staré .html adresy přesměrovávají
a mají canonical — Google se přelije sám.

## Vzhled a soukromí

Barvy a písma = `:root` v `style.css`. Písma servírujeme vlastní (`fonts/`),
web nemá cookies ani třetí strany → žádná cookie lišta. Případnou analytiku
řešit bezcookies nástrojem a zároveň upravit sekci „Cookies a měření"
v `soukromi/index.html`.

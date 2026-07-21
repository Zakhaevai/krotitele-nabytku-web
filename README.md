# Krotitelé nábytku — web

Statický web, žádné závislosti, žádný build.

| Soubor | Co to je |
|---|---|
| `index.html` | úvodní stránka |
| `nabytek.html` | nabídka kusů — 2 sety + 2 páry + židle + stůl, ceny nastřelené |
| `renovace.html` | renovace na zakázku — ceny „od" nastřelené podle trhu |
| `vykup.html` | výkup a odvoz |
| `kontakt.html` | kontakty + formulář s přílohami (FormSubmit — ⚠️ nutná aktivace, viz komentář v souboru) |
| `dekujeme.html` | děkovací stránka po odeslání formuláře |
| `soukromi.html` | ochrana osobních údajů — kompletní |
| `fonts/` | písma servírovaná z vlastního webu (žádné Google Fonts = žádný přenos IP třetí straně) |
| `style.css` | vzhled webu (barvy a písma v bloku `:root` nahoře) |
| `sitemap.xml`, `robots.txt` | pro vyhledávače — hotové, míří na krotitelenabytku.cz |

**Náhled:** otevřít `index.html` v prohlížeči; soubory musí zůstat pohromadě.

## Stav

**Hotovo:** kontakty (e-mail, telefon, Instagram, Facebook), jména, IČO, doména
propsaná všude (canonical, og:url, og:image, sitemap, robots, strukturovaná data),
funkční formulář (Formspree), fotky kusů ve složce `fotky/` (zmenšené, bez EXIF).

**Zbývá** (nic z toho neblokuje nasazení):
1. **Chybějící fotky:** jídelní stůl (karta má zástupný blok) a společná fotka
   vás dvou do sekce Kdo jsme. Nová fotka = uložit do `fotky/` a vložit
   `<img src="fotky/nazev.jpg" alt="popis kusu" class="foto">`.
2. **Ceny** na kartách i na stránce Renovace jsou nástřel — potvrdit nebo posunout.
3. Volitelně: odkaz na Krotitele chaosu v patičce `index.html` (zakomentovaný řádek).

## Nasazení (GitHub Pages)

1. Veřejný repozitář, **obsah** této složky do kořene (index.html v rootu), push.
2. Settings → Pages → Deploy from a branch → `main` + `/ (root)`.
3. Custom domain: `krotitelenabytku.cz` → Save.
4. DNS u GoDaddy: 4× A záznam `@` → 185.199.108.153 / .109.153 / .110.153 / .111.153,
   CNAME `www` → `tvuj-ucet.github.io`, smazat parkovací A záznam.
5. Po zezelenání DNS kontroly zaškrtnout Enforce HTTPS.

## Po spuštění

- **Search Console** (typ Doména, ověření TXT záznamem) → odeslat `sitemap.xml`.
- **Google Business Profile** — kategorie „renovace nábytku", Radíkovice,
  oblast Hradec Králové + Praha.
- **Firmy.cz** — bezplatný zápis (Seznam + Mapy.cz).
- Nový kus = zkopírovat kartu v `nabytek.html`, přepsat, přidat fotku.
  Prodané kusy nemazat, jen štítek `badge--prodano` — jsou to reference.

## Úprava vzhledu

Barvy a písma = proměnné v `:root` na začátku `style.css`; změna tam se propíše
do celého webu. Design vychází z bruselského stylu: petrolejová, ořech, mosaz,
Zilla Slab. Logo ve stejné barevnosti je v samostatném zipu.

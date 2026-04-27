# Krész Péter — Portfolio

Személyes portfolio oldal, single-file HTML/CSS/JS megoldással, GitHub Pages-en hostolva.

## Fájlok

```
.
├── index.html    # az egész oldal egyetlen fájlban (HTML + CSS + JS)
└── README.md     # ez a fájl
```

Nincs build step, nincs node_modules, nincs konfig — csak az `index.html`.

## Helyi tesztelés

A legegyszerűbb mód: kattints duplán az `index.html`-re, és megnyitja a böngésző.

Ha lokálisan szervert akarsz indítani (pl. mert a CDN font cache-elése egyébként furán viselkedik):

```powershell
# Pythonnal (ha van)
python -m http.server 8000

# vagy Node-dal
npx serve .
```

Aztán: <http://localhost:8000>

## Deploy GitHub Pages-re

### 1. Repó létrehozása

Nyiss egy új repót GitHubon, **publikusként**. Ha azt szeretnéd, hogy az oldal a `https://<felhasználónév>.github.io` címen jelenjen meg, a repó neve **pontosan ez kell legyen**: `<felhasználónév>.github.io` (a te esetedben pl. `pterkrsz.github.io`).

Ha bármilyen más néven hozod létre (pl. `portfolio`), a cím így alakul: `https://<felhasználónév>.github.io/portfolio/`.

### 2. Fájlok feltöltése

Lokálban a portfolio mappában:

```powershell
git init
git add .
git commit -m "initial portfolio"
git branch -M main
git remote add origin https://github.com/<felhasználónév>/<repó-név>.git
git push -u origin main
```

### 3. Pages bekapcsolása

A repón GitHub-on:

1. **Settings → Pages**
2. **Source**: `Deploy from a branch`
3. **Branch**: `main`, mappa: `/ (root)`
4. **Save**

Az oldal 1-2 perc múlva elérhető lesz a megadott URL-en.

### 4. Saját domain (opcionális)

Ha van saját domained:

1. A domain szolgáltatónál állíts be CNAME rekordot a GitHub Pages alapértelmezett URL-jére (`<felhasználónév>.github.io`).
2. A repó **Settings → Pages → Custom domain** mezőbe írd be a domained.
3. Pipáld ki: `Enforce HTTPS`.

## Testreszabás

Az `index.html`-ben a fontosabb dolgok:

- **Színek** — a `:root` blokkban a CSS változók (`--accent`, `--bg`, stb.). A neon zöld akcentszín a `--accent: #00ffa3`.
- **Hero szöveg** — a `<section class="hero">` blokkban.
- **Szolgáltatások** — `<section id="services">`, hat kártya, mindegyik egy `<div class="service">`.
- **Projektek** — `<section id="projects">`, kilenc kártya valós projektekkel.
- **Készségek és tanulmányok** — `<section id="skills">`, a chip-ek és timeline elemek között.
- **Kapcsolat** — `<section id="contact">`, az email/telefon/LinkedIn linkek.

## SEO tippek

- Az `<meta name="description">` és `<meta property="og:...">` mezőket frissítsd, ha változik a profilod.
- Adj hozzá egy `favicon.ico` vagy `favicon.svg` fájlt a gyökérbe.
- Generálhatsz egy `robots.txt`-t és `sitemap.xml`-t is, de egy egyoldalas portfolióhoz nem feltétlenül szükséges.

## Licenc

Az oldal tartalma személyes — a kód szabadon felhasználható (sablonként).

[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Ingyenes felhő böngésző

Használd a GitHub Actions ingyenes Ubuntu virtuális gépét egy böngészőből elérhető felhő asztal indításához, beépített Chrome-mal. Nyiss meg egy weboldalt, és máris van egy internetre csatlakozó felhő PC-d — ha végeztél, kapcsold ki. Teljesen ingyenes.

## ✨ Funkciók

- 🌐 Ubuntu asztal + Chrome böngésző, közvetlenül a böngésződben kezelve
- ⌨️ Beépített fcitx5 kínai beviteli mód (Pinyin), `Ctrl+Space` billentyűvel válthatsz a kínai/angol között
- 📋 A telefonodon másolt kínai szöveg közvetlenül beilleszthető a távoli asztalba
- 🖱️ Asztali jobbklikk menü a beviteli mód váltásához vagy a Chrome egykattintásos újraindításához
- 🌐 Hozzáférés Cloudflare alagúton keresztül — nincs szükség nyilvános IP-re, sem porttovábbításra
- 🖱️ Csatlakozz telefonról, tabletről vagy számítógépről (noVNC web kliens)
- ⏱️ Minden munkamenet legfeljebb ~6 óráig tart, és bármikor megszakíthatod

## 🚀 Használat (forkold és indulj)

### 1. lépés: Forkold ezt a projektet

Kattints a **Fork** gombra az oldal jobb felső sarkában, hogy a projektet a saját GitHub-fiókodba másold. A fork után a `your-username/cloud-browser` tárolóba jutsz.

> 💡 Miért fork? A GitHub Actions csak a saját fiókod alatti tárolókban futhat — a fork megadja a futtatások indításához szükséges jogosultságot.

### 2. lépés: Indítsd el a felhő böngészőt

1. Menj a forkolt tároló oldalára, és kattints felül az **Actions** fülre
2. Keresd meg a bal oldalsávban a **Free Cloud Browser** elemet, és kattints rá
3. Kattints a jobb oldali **Run workflow** gombra — két beviteli mező jelenik meg:

| Paraméter | Leírás |
|-----------|-------------|
| VNC jelszó | A jelszó, amelyet az asztalhoz való csatlakozáskor adsz meg; csak az első 8 karakter érvényes, betűket + számokat használj (pl. `abc12345`), **írd fel**; eldobható jelszó — ne olyat használj, amit máshol is használsz |
| Futási idő | Hány percig marad életben ez a munkamenet; alapértelmezett 300 (5 óra), maximum 350 |

4. Kattints a zöld **Run workflow** gombra a megerősítéshez, és a felhő böngésződ elindul

### 3. lépés: Szerezd meg a hozzáférési URL-t

1. Az Actions oldalon kattints a most indított futásra (a legfelső; a sárga pont azt jelenti, hogy fut)
2. Várj kb. 2–4 percet, amíg a VM befejezi a szoftvertelepítést és az alagút beállítását
3. Kattints az építési lépésre a naplók kibontásához, és görgess lefelé, amíg egy ilyen URL-t nem találsz:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Másold ki ezt az URL-t, és nyisd meg egy böngészőben (a telefonod beépített böngészője is tökéletesen megfelel)

### 4. lépés: Csatlakozz és használd

1. A megnyíló noVNC oldalon kattints a **Connect** gombra
2. Add meg a 2. lépésben beállított VNC jelszót
3. Látni fogod az Ubuntu asztalt és a Chrome-ot — élvezd 🎉

> ⌨️ Beviteli mód: alapértelmezett kínai Pinyin; nyomd meg a **Ctrl+Space** billentyűt a kínai/angol közötti váltáshoz, vagy jobb klikk az asztalon, és válaszd a „Switch Input Method 中/英” lehetőséget.
> 📋 Kínai beillesztése: másolj kínai szöveget a telefonodon, és illeszd be közvetlenül a távoli asztalba.

### 5. lépés: Ne felejtsd el kikapcsolni

- Menj vissza az Actions oldalra, nyisd meg ezt a futást, és kattints jobb felül a **Cancel run** gombra — a VM megsemmisül, az alagút pedig leáll
- A beállított időtartam letelte után automatikusan véget ér, így nem kell aggódnod

## ⚠️ Megjegyzések

- **Az URL minden alkalommal más**: a régi URL-ek érvényüket vesztik, amint az előző futás véget ér — mindig a legutóbbi futás naplóiból származó URL-t használd
- **Semmi sem mentődik**: ha a VM megsemmisül, a böngésző könyvjelzői, a letöltött fájlok és a bejelentkezési munkamenetek mind törlődnek — a fontos fájlokat időben mentsd ki
- **Jelszószabályok**: csak betűk és számok, legfeljebb 8 karakter; ez egy eldobható jelszó, ne olyat használj, amit rendszeresen használsz
- **Ne kattints a Re-run gombra**: új munkamenet indításához kattints a **Run workflow** gombra — a Re-run a régi kódot futtatná
- **Lassú/akadozó kapcsolat**: az alagút a Cloudflare-en keresztül megy, így a Kínából mért sebesség a hálózati körülményeidtől függ — használható, de csodát ne várj

## 🛠️ Szeretnéd magad módosítani?

A munkafolyamat-fájl a `.github/workflows/cloud-browser.yml` címen található — nyisd meg közvetlenül a GitHub webes felületén, szerkeszd, és a változásaid a commit után lépnek érvénybe.

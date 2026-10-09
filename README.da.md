[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Gratis cloud-browser

Brug GitHub Actions' gratis Ubuntu-virtuelle maskine til at starte et cloud-skrivebord, du kan tilgå fra din browser, med Chrome indbygget. Åbn en webside, og du har en cloud-pc med internetforbindelse — luk den ned, når du er færdig. Helt gratis.

## ✨ Funktioner

- 🌐 Ubuntu-skrivebord + Chrome-browser, betjent direkte i din browser
- ⌨️ Indbygget fcitx5 kinesisk inputmetode (Pinyin), skift mellem kinesisk/engelsk med `Ctrl+Space`
- 📋 Kinesisk tekst kopieret på din telefon kan indsættes direkte i det fjernstyrede skrivebord
- 🖱️ Højrekliksmenu på skrivebordet til at skifte inputmetode eller genstarte Chrome med ét klik
- 🌐 Adgang via Cloudflare-tunnel — ingen offentlig IP, ingen portforwarding nødvendig
- 🖱️ Forbind fra telefon, tablet eller computer (noVNC-webklient)
- ⏱️ Hver session kører op til ~6 timer, og du kan annullere når som helst

## 🚀 Sådan bruger du det (fork og kør)

### Trin 1: Fork dette projekt

Klik på knappen **Fork** øverst til højre på denne side for at kopiere projektet til din egen GitHub-konto. Efter forking lander du i depotet `your-username/cloud-browser`.

> 💡 Hvorfor forke? GitHub Actions kan kun køre på depoter under din egen konto — forking giver dig tilladelse til at starte kørsler.

### Trin 2: Start cloud-browseren

1. Gå til din forkede repos side, og klik på fanen **Actions** øverst
2. Find **Free Cloud Browser** i venstre sidepanel, og klik på det
3. Klik på knappen **Run workflow** til højre — to inputfelter dukker op:

| Parameter | Beskrivelse |
|-----------|-------------|
| VNC-adgangskode | Adgangskoden, du indtaster for at oprette forbindelse til skrivebordet; kun de første 8 tegn er effektive, brug bogstaver + tal (f.eks. `abc12345`), **skriv den ned**; engangsadgangskode — brug ikke en, du bruger andre steder |
| Køretid | Hvor mange minutter denne session forbliver oppe; standard 300 (5 timer), maks. 350 |

4. Klik på den grønne **Run workflow** for at bekræfte, og din cloud-browser begynder at starte

### Trin 3: Få adgangs-URL'en

1. På Actions-siden skal du klikke ind i den kørsel, du lige har startet (den øverste; en gul prik betyder, at den kører)
2. Vent ca. 2–4 minutter, mens VM'en er færdig med at installere software og sætte tunnelen op
3. Klik på build-trinnet for at udvide loggene, og rul ned for at finde en URL som denne:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Kopiér denne URL, og åbn den i en browser (din telefons indbyggede browser fungerer fint)

### Trin 4: Forbind og brug

1. På den noVNC-side, der åbnes, skal du klikke på **Connect**
2. Indtast den VNC-adgangskode, du angav i trin 2
3. Du vil se Ubuntu-skrivebordet og Chrome — nyd det 🎉

> ⌨️ Inputmetode: Pinyin-kinesisk som standard; tryk på **Ctrl+Space** for at skifte mellem kinesisk/engelsk, eller højreklik på skrivebordet og vælg "Switch Input Method 中/英".
> 📋 Indsæt kinesisk: kopiér kinesisk tekst på din telefon, og indsæt den direkte i det fjernstyrede skrivebord.

### Trin 5: Husk at lukke den ned

- Gå tilbage til Actions-siden, åbn den kørsel, og klik på **Cancel run** øverst til højre — VM'en ødelægges, og tunnelen holder op med at virke
- Den slutter også automatisk, når den indstillede køretid er gået, så du behøver ikke bekymre dig om, at den kører for evigt

## ⚠️ Bemærkninger

- **URL'en er forskellig hver gang**: gamle URL'er holder op med at virke, når den forrige kørsel slutter — brug altid URL'en fra den seneste kørsels logge
- **Intet gemmes**: når VM'en er ødelagt, slettes browserbogmærker, downloadede filer og login-sessioner — flyt vigtige filer ud i tide
- **Adgangskoderegler**: kun bogstaver og tal, maks. 8 tegn; det er en engangsadgangskode, brug ikke en, du bruger jævnligt
- **Klik ikke på Re-run**: for at starte en ny session skal du klikke på **Run workflow** — Re-run ville køre gammel kode
- **Langsom/hakkende forbindelse**: tunnelen går gennem Cloudflare, så hastigheder fra det kinesiske fastland afhænger af dine netværksforhold — brugbar, men forvent ikke mirakler

## 🛠️ Vil du selv justere det?

Workflow-filen er på `.github/workflows/cloud-browser.yml` — åbn den direkte i GitHubs web-UI, rediger den, og dine ændringer træder i kraft ved commit.

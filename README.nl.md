[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Gratis cloudbrowser

Gebruik de gratis Ubuntu-VM van GitHub Actions om een cloudbureaublad te starten dat je vanuit je browser kunt gebruiken, met ingebouwde Chrome. Open een webpagina en je hebt een cloud-pc met internetverbinding — zet hem uit als je klaar bent. Helemaal gratis.

## ✨ Functies

- 🌐 Ubuntu-bureaublad + Chrome-browser, bediend direct in je browser
- ⌨️ Ingebouwde fcitx5 Chinese invoermethode (Pinyin), schakel tussen Chinees/Engels met `Ctrl+Space`
- 📋 Chinese tekst die op je telefoon is gekopieerd, kan direct in het externe bureaublad worden geplakt
- 🖱️ Rechtsklikmenu op het bureaublad om de invoermethode te wisselen of Chrome met één klik opnieuw te starten
- 🌐 Toegang via Cloudflare-tunnel — geen openbaar IP, geen port forwarding nodig
- 🖱️ Verbind vanaf telefoon, tablet of computer (noVNC-webclient)
- ⏱️ Elke sessie duurt tot ~6 uur, en je kunt hem op elk moment annuleren

## 🚀 Gebruik (fork en ga)

### Stap 1: Fork dit project

Klik op de knop **Fork** rechtsboven op deze pagina om het project naar je eigen GitHub-account te kopiëren. Na het forken kom je in de repository `your-username/cloud-browser`.

> 💡 Waarom forken? GitHub Actions kan alleen draaien in repositories onder je eigen account — forken geeft je toestemming om sessies te starten.

### Stap 2: Start de cloudbrowser

1. Ga naar de pagina van je geforkte repository en klik bovenaan op het tabblad **Actions**
2. Zoek **Free Cloud Browser** in de linkerzijbalk en klik erop
3. Klik rechts op de knop **Run workflow** — er verschijnen twee invoervelden:

| Parameter | Beschrijving |
|-----------|-------------|
| VNC-wachtwoord | Het wachtwoord dat je invoert om met het bureaublad te verbinden; alleen de eerste 8 tekens zijn effectief, gebruik letters + cijfers (bijv. `abc12345`), **schrijf het op**; wegwerpwachtwoord — gebruik geen wachtwoord dat je elders gebruikt |
| Sessieduur | Hoeveel minuten deze sessie actief blijft; standaard 300 (5 uur), maximaal 350 |

4. Klik op de groene knop **Run workflow** om te bevestigen, en je cloudbrowser start op

### Stap 3: Haal de toegangs-URL op

1. Klik op de Actions-pagina op de sessie die je zojuist hebt gestart (de bovenste; een gele stip betekent dat hij draait)
2. Wacht ongeveer 2–4 minuten tot de VM klaar is met het installeren van software en het opzetten van de tunnel
3. Klik op de buildstap om de logs uit te vouwen en scrol naar beneden om een URL zoals deze te vinden:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Kopieer deze URL en open hem in een browser (de ingebouwde browser van je telefoon werkt prima)

### Stap 4: Verbind en gebruik

1. Klik op de noVNC-pagina die opent op **Connect**
2. Voer het VNC-wachtwoord in dat je in stap 2 hebt ingesteld
3. Je ziet het Ubuntu-bureaublad en Chrome — veel plezier 🎉

> ⌨️ Invoermethode: Chinees Pinyin als standaard; druk op **Ctrl+Space** om te schakelen tussen Chinees/Engels, of klik met de rechtermuisknop op het bureaublad en kies "Switch Input Method 中/英".
> 📋 Chinees plakken: kopieer Chinese tekst op je telefoon en plak hem direct in het externe bureaublad.

### Stap 5: Vergeet hem niet uit te zetten

- Ga terug naar de Actions-pagina, open die sessie en klik rechtsboven op **Cancel run** — de VM wordt vernietigd en de tunnel stopt met werken
- Hij stopt ook automatisch zodra de ingestelde duur is verstreken, dus geen zorgen

## ⚠️ Opmerkingen

- **De URL is elke keer anders**: oude URL's stoppen met werken zodra de vorige sessie is beëindigd — gebruik altijd de URL uit de logs van de nieuwste sessie
- **Er wordt niets bewaard**: zodra de VM is vernietigd, worden browserbladwijzers, gedownloade bestanden en aanmeldingssessies allemaal gewist — haal belangrijke bestanden op tijd weg
- **Wachtwoordregels**: alleen letters en cijfers, maximaal 8 tekens; het is een wegwerpwachtwoord, gebruik geen wachtwoord dat je regelmatig gebruikt
- **Klik niet op Re-run**: om een nieuwe sessie te starten klik op **Run workflow** — Re-run zou de oude code draaien
- **Trage/laggende verbinding**: de tunnel loopt via Cloudflare, dus snelheden vanuit het vasteland van China hangen af van je netwerkomstandigheden — bruikbaar, maar verwacht geen wonderen

## 🛠️ Wil je het zelf aanpassen?

Het workflowbestand staat op `.github/workflows/cloud-browser.yml` — open het direct in de GitHub-webinterface, bewerk het, en je wijzigingen zijn van kracht na een commit.

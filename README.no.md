[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Gratis nettleser i skyen

Bruk GitHub Actions' gratis Ubuntu-VM til å starte et skrivebord i skyen du kan bruke fra nettleseren, med Chrome innebygd. Åpne en nettside, så har du en internett-tilkoblet sky-PC — slå den av når du er ferdig. Helt gratis.

## ✨ Funksjoner

- 🌐 Ubuntu-skrivebord + Chrome-nettleser, styrt rett i nettleseren
- ⌨️ Innebygd fcitx5-inndatametode for kinesisk (pinyin), bytt mellom kinesisk/engelsk med `Ctrl+Space`
- 📋 Kinesisk tekst kopiert på telefonen kan limes direkte inn på det eksterne skrivebordet
- 🖱️ Høyreklikkmeny på skrivebordet for å bytte inndatametode eller starte Chrome på nytt med ett klikk
- 🌐 Tilgang via Cloudflare-tunnel — ingen offentlig IP, ingen portvideresending nødvendig
- 🖱️ Koble til fra telefon, nettbrett eller datamaskin (noVNC-nettklient)
- ⏱️ Hver økt varer opptil ~6 timer, og du kan avbryte når som helst

## 🚀 Slik bruker du den (Fork og kjør)

### Trinn 1: Fork dette prosjektet

Klikk på **Fork**-knappen øverst til høyre på denne siden for å kopiere prosjektet til din egen GitHub-konto. Etter forking lander du i depotet `your-username/cloud-browser`.

> 💡 Hvorfor forke? GitHub Actions kan bare kjøre i depoter under din egen konto — forking gir deg tillatelse til å starte kjøringer.

### Trinn 2: Start nettleseren i skyen

1. Gå til siden for det forkede depotet og klikk på **Actions**-fanen øverst
2. Finn **Free Cloud Browser** i sidepanelet til venstre og klikk på den
3. Klikk på **Run workflow**-knappen til høyre — to inndatafelt dukker opp:

| Parameter | Beskrivelse |
|-----------|-------------|
| VNC password | Passordet du skriver inn for å koble til skrivebordet; kun de første 8 tegnene gjelder, bruk bokstaver + tall (f.eks. `abc12345`), **skriv det ned**; engangspassord — ikke bruk et du bruker andre steder |
| Runtime | Hvor mange minutter denne økten holder seg oppe; standard 300 (5 timer), maks 350 |

4. Klikk på den grønne **Run workflow**-knappen for å bekrefte, og nettleseren i skyen begynner å starte

### Trinn 3: Hent tilgangs-URL-en

1. På Actions-siden klikker du inn i kjøringen du nettopp startet (den øverste; en gul prikk betyr at den kjører)
2. Vent omtrent 2–4 minutter mens VM-en installerer programvare og setter opp tunnelen
3. Klikk på byggesteget for å utvide loggene, og bla nedover for å finne en URL som denne:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Kopier denne URL-en og åpne den i en nettleser (telefonens innebygde nettleser fungerer fint)

### Trinn 4: Koble til og bruk

1. På noVNC-siden som åpnes, klikker du **Connect**
2. Skriv inn VNC-passordet du satte i trinn 2
3. Du ser Ubuntu-skrivebordet og Chrome — kos deg 🎉

> ⌨️ Inndatametode: Pinyin-kinesisk som standard; trykk **Ctrl+Space** for å bytte mellom kinesisk/engelsk, eller høyreklikk på skrivebordet og velg «Switch Input Method 中/英».
> 📋 Lime inn kinesisk: kopier kinesisk tekst på telefonen og lim den rett inn på det eksterne skrivebordet.

### Trinn 5: Husk å slå den av

- Gå tilbake til Actions-siden, åpne den kjøringen, og klikk **Cancel run** øverst til høyre — VM-en ødelegges og tunnelen slutter å virke
- Den avsluttes også automatisk når den angitte kjøretiden er over, så du trenger ikke bekymre deg for at den kjører for alltid

## ⚠️ Merknader

- **URL-en er forskjellig hver gang**: gamle URL-er slutter å virke når forrige kjøring avsluttes — bruk alltid URL-en fra den nyeste kjøringens logger
- **Ingenting lagres**: når VM-en ødelegges, slettes nettleserens bokmerker, nedlastede filer og påloggingsøkter — flytt viktige filer ut i tide
- **Passordregler**: kun bokstaver og tall, maks 8 tegn; det er et engangspassord, ikke bruk et du bruker til daglig
- **Ikke klikk Re-run**: for å starte en ny økt, klikk **Run workflow** — Re-run ville kjørt den gamle koden
- **Treg/hakkete tilkobling**: tunnelen går gjennom Cloudflare, så hastigheter fra Fastlands-Kina avhenger av nettverksforholdene dine — brukbart, men ikke forvent mirakler

## 🛠️ Vil du tilpasse den selv?

Arbeidsflytfilen ligger på `.github/workflows/cloud-browser.yml` — åpne den rett i GitHub-nettgrensesnittet, rediger, og endringene trer i kraft ved commit.

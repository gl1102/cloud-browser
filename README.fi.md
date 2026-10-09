[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Ilmainen pilviselain

Käytä GitHub Actionsin ilmaista Ubuntu-virtuaalikonetta käynnistääksesi pilvityöpöydän, jota voit käyttää selaimestasi, sisäänrakennetulla Chromella. Avaa verkkosivu ja sinulla on internetiin yhdistetty pilvitietokone — sammuta se, kun olet valmis. Täysin ilmainen.

## ✨ Ominaisuudet

- 🌐 Ubuntu-työpöytä + Chrome-selain, käytettynä suoraan selaimessasi
- ⌨️ Sisäänrakennettu kiinalainen fcitx5-syöttötapa (Pinyin), vaihda kiinan/englannin välillä näppäimillä `Ctrl+Space`
- 📋 Puhelimessa kopioitu kiinalainen teksti voidaan liittää suoraan etätyöpöytään
- 🖱️ Työpöydän oikean painikkeen valikko syöttötavan vaihtamiseen tai Chromen uudelleenkäynnistämiseen yhdellä napsautuksella
- 🌐 Pääsy Cloudflare-tunnelin kautta — ei julkista IP-osoitetta, ei porttiohjausta tarvita
- 🖱️ Yhdistä puhelimesta, tabletilta tai tietokoneelta (noVNC-verkkosovellus)
- ⏱️ Jokainen istunto kestää jopa ~6 tuntia, ja voit peruuttaa milloin tahansa

## 🚀 Käyttöohje (forkkaa ja aloita)

### Vaihe 1: Forkkaa tämä projekti

Napsauta sivun oikeassa yläkulmassa olevaa **Fork**-painiketta kopioidaksesi projektin omaan GitHub-tiliisi. Forkkauksen jälkeen päädyt repositorioon `your-username/cloud-browser`.

> 💡 Miksi forkata? GitHub Actions voi toimia vain oman tilisi alla olevissa repositorioissa — forkkaus antaa sinulle luvan aloittaa ajoja.

### Vaihe 2: Käynnistä pilviselain

1. Mene forkkaamasi repositorion sivulle ja napsauta ylhäällä **Actions**-välilehteä
2. Etsi vasemmasta sivupalkista **Free Cloud Browser** ja napsauta sitä
3. Napsauta oikealla **Run workflow** -painiketta — kaksi syöttökenttää ponnahtaa esiin:

| Parametri | Kuvaus |
|-----------|-------------|
| VNC-salasana | Salasana, jonka annat yhdistäessäsi työpöytään; vain ensimmäiset 8 merkkiä ovat voimassa, käytä kirjaimia + numeroita (esim. `abc12345`), **kirjoita se muistiin**; kertakäyttöinen salasana — älä käytä sellaista, jota käytät muualla |
| Ajoaika | Kuinka monta minuuttia tämä istunto pysyy käynnissä; oletus 300 (5 tuntia), maksimi 350 |

4. Vahvista napsauttamalla vihreää **Run workflow**-painiketta, ja pilviselaimesi alkaa käynnistyä

### Vaihe 3: Hae käyttöosoite

1. Napsauta Actions-sivulla äsken aloittamaasi ajoa (ylimmäinen; keltainen piste tarkoittaa, että se on käynnissä)
2. Odota noin 2–4 minuuttia, kun virtuaalikone asentaa ohjelmistot ja muodostaa tunnelin loppuun
3. Napsauta build-vaihetta laajentaaksesi lokit ja vieritä alas löytääksesi tällaisen osoitteen:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Kopioi tämä osoite ja avaa se selaimessa (puhelimesi sisäänrakennettu selain toimii hyvin)

### Vaihe 4: Yhdistä ja käytä

1. Napsauta avautuvalla noVNC-sivulla **Connect**
2. Anna vaiheessa 2 asettamasi VNC-salasana
3. Näet Ubuntu-työpöydän ja Chromen — nauti 🎉

> ⌨️ Syöttötapa: oletuksena kiinalainen Pinyin; paina **Ctrl+Space** vaihtaaksesi kiinan/englannin välillä, tai napsauta työpöytää hiiren oikealla ja valitse "Switch Input Method 中/英".
> 📋 Kiinan liittäminen: kopioi kiinalainen teksti puhelimessasi ja liitä se suoraan etätyöpöytään.

### Vaihe 5: Muista sammuttaa

- Palaa Actions-sivulle, avaa kyseinen ajo ja napsauta oikeassa yläkulmassa **Cancel run** — virtuaalikone tuhotaan ja tunneli lakkaa toimimasta
- Se myös päättyy automaattisesti, kun asetettu ajoaika umpeutuu, joten sinun ei tarvitse huolehtia siitä, että se jäisi päälle ikuisiksi ajoiksi

## ⚠️ Huomioitavaa

- **Osoite on erilainen joka kerta**: vanhat osoitteet lakkaavat toimimasta, kun edellinen ajo päättyy — käytä aina uusimman ajon lokeissa olevaa osoitetta
- **Mitään ei tallenneta**: kun virtuaalikone tuhotaan, selaimen kirjanmerkit, ladatut tiedostot ja kirjautumisistunnot pyyhitään kaikki — siirrä tärkeät tiedostot pois ajoissa
- **Salasanasäännöt**: vain kirjaimia ja numeroita, enintään 8 merkkiä; se on kertakäyttöinen salasana, älä käytä sellaista, jota käytät säännöllisesti
- **Älä napsauta Re-run**: aloita uusi istunto napsauttamalla **Run workflow** — Re-run ajaisi vanhaa koodia
- **Hidas/nykinen yhteys**: tunneli kulkee Cloudflaren kautta, joten nopeudet Manner-Kiinasta riippuvat verkkosi kunnosta — käyttökelpoinen, mutta älä odota ihmeitä

## 🛠️ Haluatko säätää itse?

Työnkulkutiedosto on kohdassa `.github/workflows/cloud-browser.yml` — avaa se suoraan GitHubin verkko-UI:ssa, muokkaa, ja muutoksesi astuvat voimaan commitilla.

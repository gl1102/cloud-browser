[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Senpaga Nuba Retumilo

Uzu la senpagan Ubuntu-virtualan maŝinon de GitHub Actions por lanĉi nubolan labortablon alireblan el via retumilo, kun enkonstruita Chrome. Malfermu retpaĝon kaj vi havas interret-konektitan nubolan komputilon — malŝaltu ĝin kiam vi finos. Tute senpage.

## ✨ Ecoj

- 🌐 Ubuntu-labortablo + Chrome-retumilo, funkciigataj rekte en via retumilo
- ⌨️ Enkonstruita ĉina eniga metodo fcitx5 (Pinyin), ŝanĝu inter la ĉina/angla per `Ctrl+Space`
- 📋 Ĉinan tekston kopiitan en via telefono vi povas alglui rekte en la fora labortablon
- 🖱️ Dekstra-klaka menuo sur la labortablo por ŝanĝi la enigan metodon aŭ restartigi Chrome per unu klako
- 🌐 Aliro per Cloudflare-tunelo — neniu publika IP, neniu pordplusendo bezonata
- 🖱️ Konektiĝu el telefono, tablojdo aŭ komputilo (noVNC retkliento)
- ⏱️ Ĉiu sesio funkcias ĝis ~6 horoj, kaj vi povas nuligi iam ajn

## 🚀 Kiel uzi (forku kaj ekiru)

### Paŝo 1: Forku ĉi tiun projekton

Alklaku la butonon **Fork** en la supradekstra angulo de ĉi tiu paĝo por kopii la projekton en vian propran GitHub-konton. Post forko vi alvenos en la deponejon `your-username/cloud-browser`.

> 💡 Kial forki? GitHub Actions povas funkcii nur sur deponejoj sub via propra konto — forko donas al vi permeson startigi rulojn.

### Paŝo 2: Startigu la nubolan retumilon

1. Iru al la paĝo de via forkita deponejo kaj alklaku la langeton **Actions** supre
2. Trovu **Free Cloud Browser** en la maldekstra flanka panelo kaj alklaku ĝin
3. Alklaku la butonon **Run workflow** dekstre — aperas du enigaĵoj:

| Parametro | Priskribo |
|-----------|-------------|
| VNC-pasvorto | La pasvorto, kiun vi enigos por konektiĝi al la labortablo; nur la unuaj 8 signoj estas efektivaj, uzu literojn + ciferojn (ekz. `abc12345`), **skribu ĝin**; forĵetebla pasvorto — ne uzu unu, kiun vi uzas aliloke |
| Funkcidaŭro | Kiom da minutoj tiu sesio restas supre; defaŭlte 300 (5 horoj), maksimume 350 |

4. Alklaku la verdan **Run workflow** por konfirmi, kaj via nuba retumilo komencas lanĉiĝi

### Paŝo 3: Akiru la alir-adreson

1. En la Actions-paĝo, alklaku en la rulon, kiun vi ĵus startigis (la plej supra; flava punkto signifas, ke ĝi funkcias)
2. Atendu ĉirkaŭ 2–4 minutojn dum la VM finas instali programaron kaj agordi la tunelon
3. Alklaku la konstruan paŝon por malfaldi la protokolojn, kaj rulumu malsupren por trovi adreson kiel ĉi tiu:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Kopiu tiun adreson kaj malfermu ĝin en retumilo (la enkonstruita retumilo de via telefono funkcias bone)

### Paŝo 4: Konektiĝu kaj uzu

1. En la malfermita noVNC-paĝo, alklaku **Connect**
2. Enigu la VNC-pasvorton, kiun vi agordis en Paŝo 2
3. Vi vidos la Ubuntu-labortablon kaj Chrome — ĝuu 🎉

> ⌨️ Eniga metodo: ĉina Pinyin defaŭlte; premu **Ctrl+Space** por ŝanĝi inter la ĉina/angla, aŭ dekstra-klaku la labortablon kaj elektu "Switch Input Method 中/英".
> 📋 Algluado de la ĉina: kopiu ĉinan tekston en via telefono kaj algluu ĝin rekte en la foran labortablon.

### Paŝo 5: Memoru malŝalti ĝin

- Reiru al la Actions-paĝo, malfermu tiun rulon, kaj alklaku **Cancel run** supradekstre — la VM estas detruita kaj la tunelo ĉesas funkcii
- Ĝi ankaŭ finiĝas aŭtomate post kiam la agordita funkcidaŭro pasas, do ne necesas zorgi pri senfina funkciado

## ⚠️ Notoj

- **La adreso estas malsama ĉiufoje**: malnovaj adresoj ĉesas funkcii tuj kiam la antaŭa rulo finiĝas — ĉiam uzu la adreson el la protokoloj de la plej nova rulo
- **Nenio estas konservita**: post detruo de la VM, retumilaj legosignoj, elŝutitaj dosieroj, kaj ensalutaj sesioj estas ĉiuj forviŝitaj — movu gravajn dosierojn eksteren ĝustatempe
- **Pasvortaj reguloj**: nur literoj kaj ciferoj, maksimume 8 signoj; ĝi estas forĵetebla pasvorto, ne uzu unu, kiun vi uzas regule
- **Ne alklaku Re-run**: por startigi novan sesion alklaku **Run workflow** — Re-run funkciigus malnovan kodon
- **Malrapida/tremetanta konekto**: la tunelo iras tra Cloudflare, do rapidecoj el kontinenta Ĉinio dependas de viaj retaj kondiĉoj — uzebla, sed ne atendu miraklojn

## 🛠️ Ĉu vi volas ĝustigi ĝin mem?

La laborflua dosiero estas ĉe `.github/workflows/cloud-browser.yml` — malfermu ĝin rekte en la GitHub-reta interfaco, redaktu, kaj viaj ŝanĝoj efektiviĝas per commit.

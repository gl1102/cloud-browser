[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Bezplatný cloudový prohlížeč

Pomocí bezplatného virtuálního stroje Ubuntu v GitHub Actions si rozjedete cloudovou plochu přístupnou z prohlížeče, s vestavěným Chrome. Otevřete webovou stránku a máte cloudový počítač připojený k internetu — až skončíte, vypněte ho. Zcela zdarma.

## ✨ Funkce

- 🌐 Plocha Ubuntu + prohlížeč Chrome, ovládané přímo ve vašem prohlížeči
- ⌨️ Vestavěná čínská metoda zadávání fcitx5 (Pinyin), přepínání mezi čínštinou/angličtinou pomocí `Ctrl+Space`
- 📋 Čínský text zkopírovaný na telefonu můžete vložit přímo do vzdálené plochy
- 🖱️ Kontextová nabídka na ploše pro přepnutí metody zadávání nebo restart Chrome jedním kliknutím
- 🌐 Přístup přes tunel Cloudflare — není potřeba veřejná IP adresa ani přesměrování portů
- 🖱️ Připojte se z telefonu, tabletu nebo počítače (webový klient noVNC)
- ⏱️ Každá relace běží až ~6 hodin a můžete ji kdykoli zrušit

## 🚀 Jak používat (forkněte a jedeme)

### Krok 1: Forkněte tento projekt

Klikněte na tlačítko **Fork** v pravém horním rohu této stránky a zkopírujte projekt do svého účtu GitHub. Po forku se ocitnete v repozitáři `your-username/cloud-browser`.

> 💡 Proč fork? GitHub Actions mohou běžet jen na repozitářích pod vaším účtem — forknutím získáte oprávnění spouštět.

### Krok 2: Spusťte cloudový prohlížeč

1. Přejděte na stránku svého forknutého repozitáře a klikněte nahoře na kartu **Actions**
2. V levém postranním panelu najděte **Free Cloud Browser** a klikněte na něj
3. Klikněte vpravo na tlačítko **Run workflow** — objeví se dvě vstupní pole:

| Parametr | Popis |
|-----------|-------------|
| Heslo VNC | Heslo, které zadáte pro připojení k ploše; účinných je jen prvních 8 znaků, použijte písmena + čísla (např. `abc12345`), **poznamenejte si ho**; heslo na jedno použití — nepoužívejte takové, které používáte jinde |
| Doba běhu | Kolik minut tato relace zůstane aktivní; výchozí 300 (5 hodin), maximum 350 |

4. Klikněte na zelené tlačítko **Run workflow** pro potvrzení a cloudový prohlížeč se začne spouštět

### Krok 3: Získejte přístupovou URL

1. Na stránce Actions klikněte na spuštění, které jste právě spustili (nejhornější; žlutá tečka znamená, že běží)
2. Počkejte asi 2–4 minuty, než virtuální stroj dokončí instalaci softwaru a nastavení tunelu
3. Klikněte na krok sestavení pro rozbalení logů a sjeďte dolů, abyste našli URL podobnou této:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Tuto URL zkopírujte a otevřete v prohlížeči (vestavěný prohlížeč v telefonu funguje dobře)

### Krok 4: Připojte se a používejte

1. Na otevřené stránce noVNC klikněte na **Connect**
2. Zadejte heslo VNC, které jste nastavili v kroku 2
3. Uvidíte plochu Ubuntu a Chrome — užívejte 🎉

> ⌨️ Metoda zadávání: výchozí je čínský Pinyin; stisknutím **Ctrl+Space** přepínáte mezi čínštinou/angličtinou, nebo klikněte pravým tlačítkem na plochu a vyberte „Switch Input Method 中/英".
> 📋 Vkládání čínštiny: čínský text zkopírovaný na telefonu vložte rovnou do vzdálené plochy.

### Krok 5: Nezapomeňte vypnout

- Vraťte se na stránku Actions, otevřete dané spuštění a klikněte vpravo nahoře na **Cancel run** — virtuální stroj se zničí a tunel přestane fungovat
- Skončí také automaticky po uplynutí nastavené doby běhu, takže se nemusíte bát, že poběží věčně

## ⚠️ Poznámky

- **URL je pokaždé jiná**: staré URL přestanou fungovat, jakmile skončí předchozí spuštění — vždy používejte URL z logů nejnovějšího spuštění
- **Nic se neukládá**: jakmile je virtuální stroj zničen, záložky prohlížeče, stažené soubory a přihlášené relace jsou všechny smazány — důležité soubory si včas přeneste ven
- **Pravidla pro heslo**: pouze písmena a čísla, maximálně 8 znaků; heslo na jedno použití, nepoužívejte takové, které používáte běžně
- **Neklikejte na Re-run**: pro spuštění nové relace klikněte na **Run workflow** — Re-run by spustil starý kód
- **Pomalé/zasekávající se připojení**: tunel prochází přes Cloudflare, takže rychlosti z pevninské Číny závisí na stavu vaší sítě — použitelné, ale nečekejte zázraky

## 🛠️ Chcete si to upravit sami?

Soubor workflow je v `.github/workflows/cloud-browser.yml` — otevřete ho přímo ve webovém rozhraní GitHubu, upravte a změny se projeví po commitu.

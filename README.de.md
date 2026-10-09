[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Kostenloser Cloud-Browser

Nutze die kostenlose Ubuntu-VM von GitHub Actions, um einen Cloud-Desktop mit eingebautem Chrome zu starten, auf den du vom Browser aus zugreifen kannst. Öffne eine Webseite und du hast einen Cloud-PC mit Internetzugang — fahr ihn herunter, wenn du fertig bist. Komplett kostenlos.

## ✨ Funktionen

- 🌐 Ubuntu-Desktop + Chrome-Browser, direkt in deinem Browser bedient
- ⌨️ Eingebaute chinesische fcitx5-Eingabemethode (Pinyin), mit `Ctrl+Space` zwischen Chinesisch/Englisch wechseln
- 📋 Auf dem Handy kopierter chinesischer Text lässt sich direkt in den Remote-Desktop einfügen
- 🖱️ Rechtsklickmenü auf dem Desktop zum Wechseln der Eingabemethode oder Neustarten von Chrome mit einem Klick
- 🌐 Zugriff über Cloudflare-Tunnel — keine öffentliche IP, kein Port-Forwarding nötig
- 🖱️ Von Handy, Tablet oder Computer verbinden (noVNC-Webclient)
- ⏱️ Jede Sitzung läuft bis zu ~6 Stunden, und du kannst jederzeit abbrechen

## 🚀 So geht's (forken und los)

### Schritt 1: Forke dieses Projekt

Klicke oben rechts auf dieser Seite auf den **Fork**-Button, um das Projekt in dein eigenes GitHub-Konto zu kopieren. Nach dem Forken landest du im Repository `your-username/cloud-browser`.

> 💡 Warum forken? GitHub Actions kann nur auf Repositories unter deinem eigenen Konto laufen — durch das Forken erhältst du die Berechtigung zum Starten von Läufen.

### Schritt 2: Starte den Cloud-Browser

1. Gehe auf die Seite deines geforkten Repos und klicke oben auf den **Actions**-Tab
2. Finde **Free Cloud Browser** in der linken Seitenleiste und klicke darauf
3. Klicke rechts auf den **Run workflow**-Button — zwei Eingabefelder erscheinen:

| Parameter | Beschreibung |
|-----------|-------------|
| VNC-Passwort | Das Passwort, das du zur Verbindung mit dem Desktop eingibst; nur die ersten 8 Zeichen sind wirksam, verwende Buchstaben + Zahlen (z. B. `abc12345`), **notiere es dir**; Wegwerfpasswort — verwende keines, das du anderswo nutzt |
| Laufzeit | Wie viele Minuten diese Sitzung aktiv bleibt; Standard 300 (5 Stunden), max. 350 |

4. Klicke zur Bestätigung auf den grünen **Run workflow**-Button, und dein Cloud-Browser startet

### Schritt 3: Hol dir die Zugriffs-URL

1. Klicke auf der Actions-Seite in den Lauf, den du gerade gestartet hast (der oberste; ein gelber Punkt bedeutet, dass er läuft)
2. Warte etwa 2–4 Minuten, bis die VM die Softwareinstallation und Tunneleinrichtung abgeschlossen hat
3. Klicke auf den Build-Schritt, um die Logs aufzuklappen, und scrolle nach unten, um eine URL wie diese zu finden:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Kopiere diese URL und öffne sie in einem Browser (der eingebaute Browser deines Handys funktioniert einwandfrei)

### Schritt 4: Verbinden und nutzen

1. Klicke auf der geöffneten noVNC-Seite auf **Connect**
2. Gib das VNC-Passwort ein, das du in Schritt 2 festgelegt hast
3. Du siehst den Ubuntu-Desktop und Chrome — viel Spaß 🎉

> ⌨️ Eingabemethode: Standardmäßig chinesisches Pinyin; mit **Ctrl+Space** zwischen Chinesisch/Englisch wechseln, oder rechtsklicke auf den Desktop und wähle „Switch Input Method 中/英".
> 📋 Chinesisch einfügen: Kopiere chinesischen Text auf deinem Handy und füge ihn direkt in den Remote-Desktop ein.

### Schritt 5: Denk ans Herunterfahren

- Gehe zurück auf die Actions-Seite, öffne diesen Lauf und klicke oben rechts auf **Cancel run** — die VM wird zerstört und der Tunnel funktioniert nicht mehr
- Er endet auch automatisch, sobald die eingestellte Laufzeit abgelaufen ist, also keine Sorge, dass er ewig läuft

## ⚠️ Hinweise

- **Die URL ist jedes Mal anders**: Alte URLs funktionieren nicht mehr, sobald der vorherige Lauf endet — verwende immer die URL aus den Logs des neuesten Laufs
- **Nichts wird gespeichert**: Sobald die VM zerstört ist, werden Browser-Lesezeichen, heruntergeladene Dateien und Anmeldesitzungen alle gelöscht — bringe wichtige Dateien rechtzeitig in Sicherheit
- **Passwortregeln**: Nur Buchstaben und Zahlen, max. 8 Zeichen; es ist ein Wegwerfpasswort, verwende keines, das du regelmäßig nutzt
- **Klicke nicht auf Re-run**: Um eine neue Sitzung zu starten, klicke auf **Run workflow** — Re-run würde alten Code ausführen
- **Langsame/ruckelnde Verbindung**: Der Tunnel läuft über Cloudflare, daher hängen die Geschwindigkeiten vom chinesischen Festland von deinen Netzwerkbedingungen ab — nutzbar, aber erwarte keine Wunder

## 🛠️ Willst du es selbst anpassen?

Die Workflow-Datei ist unter `.github/workflows/cloud-browser.yml` — öffne sie direkt in der GitHub-Weboberfläche, bearbeite sie, und deine Änderungen werden mit dem Commit wirksam.

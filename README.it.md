[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Browser cloud gratuito

Usa la macchina virtuale Ubuntu gratuita di GitHub Actions per avviare un desktop cloud accessibile dal browser, con Chrome integrato. Apri una pagina web e avrai un PC cloud connesso a Internet — spegnilo quando hai finito. Completamente gratuito.

## ✨ Funzionalità

- 🌐 Desktop Ubuntu + browser Chrome, controllato direttamente nel browser
- ⌨️ Metodo di input cinese fcitx5 (Pinyin) integrato, passa tra cinese/inglese con `Ctrl+Space`
- 📋 Il testo cinese copiato sul telefono può essere incollato direttamente nel desktop remoto
- 🖱️ Menu contestuale del desktop per cambiare metodo di input o riavviare Chrome con un clic
- 🌐 Accesso tramite tunnel Cloudflare — niente IP pubblico, niente port forwarding necessario
- 🖱️ Connettiti da telefono, tablet o computer (client web noVNC)
- ⏱️ Ogni sessione dura fino a ~6 ore, e puoi annullarla in qualsiasi momento

## 🚀 Come usarlo (fork e via)

### Passo 1: Fai il fork di questo progetto

Clicca sul pulsante **Fork** in alto a destra di questa pagina per copiare il progetto nel tuo account GitHub. Dopo il fork, arriverai nel repository `your-username/cloud-browser`.

> 💡 Perché il fork? GitHub Actions può essere eseguito solo nei repository del tuo account — il fork ti dà il permesso di avviare le sessioni.

### Passo 2: Avvia il browser cloud

1. Vai alla pagina del tuo repository forkato e clicca sulla scheda **Actions** in alto
2. Trova **Free Cloud Browser** nella barra laterale sinistra e cliccaci sopra
3. Clicca sul pulsante **Run workflow** a destra — appariranno due campi di input:

| Parametro | Descrizione |
|-----------|-------------|
| Password VNC | La password che inserirai per connetterti al desktop; sono efficaci solo i primi 8 caratteri, usa lettere + numeri (es. `abc12345`), **segnala**; password usa e getta — non usare una password che usi altrove |
| Durata sessione | Quanti minuti questa sessione rimane attiva; predefinito 300 (5 ore), massimo 350 |

4. Clicca sul pulsante verde **Run workflow** per confermare, e il tuo browser cloud inizia l'avvio

### Passo 3: Ottieni l'URL di accesso

1. Nella pagina Actions, clicca sulla sessione appena avviata (quella in alto; il pallino giallo significa che è in esecuzione)
2. Attendi circa 2–4 minuti affinché la VM finisca di installare il software e configuri il tunnel
3. Clicca sullo step di build per espandere i log, e scorri verso il basso per trovare un URL come questo:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Copia questo URL e aprilo in un browser (va bene anche il browser integrato del telefono)

### Passo 4: Connettiti e usa

1. Nella pagina noVNC che si apre, clicca su **Connect**
2. Inserisci la password VNC impostata al Passo 2
3. Vedrai il desktop Ubuntu e Chrome — buon divertimento 🎉

> ⌨️ Metodo di input: Pinyin cinese di default; premi **Ctrl+Space** per passare tra cinese/inglese, oppure fai clic destro sul desktop e scegli "Switch Input Method 中/英".
> 📋 Incollare il cinese: copia il testo cinese sul telefono e incollalo direttamente nel desktop remoto.

### Passo 5: Ricordati di spegnerlo

- Torna alla pagina Actions, apri quella sessione e clicca su **Cancel run** in alto a destra — la VM viene distrutta e il tunnel smette di funzionare
- Termina anche automaticamente una volta trascorsa la durata impostata, quindi nessun problema

## ⚠️ Note

- **L'URL è diverso ogni volta**: i vecchi URL smettono di funzionare non appena la sessione precedente termina — usa sempre l'URL dai log dell'ultima sessione
- **Non viene salvato nulla**: una volta distrutta la VM, i segnalibri del browser, i file scaricati e le sessioni di accesso vengono tutti cancellati — sposta in tempo i file importanti
- **Regole password**: solo lettere e numeri, massimo 8 caratteri; è una password usa e getta, non usare una password che usi abitualmente
- **Non cliccare Re-run**: per avviare una nuova sessione clicca su **Run workflow** — Re-run eseguirebbe il vecchio codice
- **Connessione lenta/lag**: il tunnel passa attraverso Cloudflare, quindi le velocità dalla Cina continentale dipendono dalle tue condizioni di rete — utilizzabile, ma non aspettarti miracoli

## 🛠️ Vuoi modificarlo da solo?

Il file di workflow si trova in `.github/workflows/cloud-browser.yml` — aprilo direttamente nell'interfaccia web di GitHub, modificalo, e le tue modifiche avranno effetto al commit.

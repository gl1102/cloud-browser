[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Free Cloud Browser

Use GitHub Actions' free Ubuntu virtual machine to spin up a cloud desktop you can access from your browser, with Chrome built in. Open a webpage and you've got an internet-connected cloud PC — shut it down when you're done. Completely free.

## ✨ Features

- 🌐 Ubuntu desktop + Chrome browser, operated right in your browser
- ⌨️ Built-in fcitx5 Chinese input method (Pinyin), switch between Chinese/English with `Ctrl+Space`
- 📋 Chinese text copied on your phone can be pasted directly into the remote desktop
- 🖱️ Desktop right-click menu to switch the input method or restart Chrome with one click
- 🌐 Access via Cloudflare tunnel — no public IP, no port forwarding needed
- 🖱️ Connect from phone, tablet, or computer (noVNC web client)
- ⏱️ Each session runs up to ~6 hours, and you can cancel anytime

## 🚀 How to Use (Fork and Go)

### Step 1: Fork This Project

Click the **Fork** button in the top-right corner of this page to copy the project into your own GitHub account. After forking, you'll land in the `your-username/cloud-browser` repository.

> 💡 Why fork? GitHub Actions can only run on repositories under your own account — forking gives you permission to start runs.

### Step 2: Start the Cloud Browser

1. Go to your forked repository page and click the **Actions** tab at the top
2. Find **Free Cloud Browser** in the left sidebar and click it
3. Click the **Run workflow** button on the right — two input fields will pop up:

| Parameter | Description |
|-----------|-------------|
| VNC password | The password you'll enter to connect to the desktop; only the first 8 characters are effective, use letters + numbers (e.g. `abc12345`), **write it down**; throwaway password — don't use one you use elsewhere |
| Runtime | How many minutes this session stays up; default 300 (5 hours), max 350 |

4. Click the green **Run workflow** to confirm, and your cloud browser starts launching

### Step 3: Get the Access URL

1. On the Actions page, click into the run you just started (the top one; a yellow dot means it's running)
2. Wait about 2–4 minutes for the VM to finish installing software and setting up the tunnel
3. Click the build step to expand the logs, and scroll down to find a URL like this:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Copy this URL and open it in a browser (your phone's built-in browser works fine)

### Step 4: Connect and Use

1. On the noVNC page that opens, click **Connect**
2. Enter the VNC password you set in Step 2
3. You'll see the Ubuntu desktop and Chrome — enjoy 🎉

> ⌨️ Input method: Pinyin Chinese by default; press **Ctrl+Space** to switch between Chinese/English, or right-click the desktop and choose "Switch Input Method 中/英".
> 📋 Pasting Chinese: copy Chinese text on your phone and paste it straight into the remote desktop.

### Step 5: Remember to Shut It Down

- Go back to the Actions page, open that run, and click **Cancel run** in the top-right — the VM is destroyed and the tunnel stops working
- It also ends automatically once the set runtime elapses, so no need to worry about it running forever

## ⚠️ Notes

- **The URL is different every time**: old URLs stop working once the previous run ends — always use the URL from the latest run's logs
- **Nothing is saved**: once the VM is destroyed, browser bookmarks, downloaded files, and login sessions are all wiped — move any important files out in time
- **Password rules**: letters and numbers only, max 8 characters; it's a throwaway password, don't use one you use regularly
- **Don't click Re-run**: to start a new session click **Run workflow** — Re-run would run the old code
- **Slow/laggy connection**: the tunnel goes through Cloudflare, so speeds from mainland China depend on your network conditions — usable, but don't expect miracles

## 🛠️ Want to Tweak It Yourself?

The workflow file is at `.github/workflows/cloud-browser.yml` — open it right in the GitHub web UI, edit, and your changes take effect on commit.

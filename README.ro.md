[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Browser gratuit în cloud

Folosește mașina virtuală Ubuntu gratuită din GitHub Actions pentru a porni un desktop în cloud accesibil din browser, cu Chrome integrat. Deschide o pagină web și ai un PC în cloud conectat la internet — închide-l când ai terminat. Complet gratuit.

## ✨ Funcționalități

- 🌐 Desktop Ubuntu + browser Chrome, operate chiar în browserul tău
- ⌨️ Metodă integrată de introducere chineză fcitx5 (Pinyin), comutare chineză/engleză cu `Ctrl+Space`
- 📋 Textul chinezesc copiat pe telefon poate fi lipit direct pe desktopul la distanță
- 🖱️ Meniu cu clic dreapta pe desktop pentru a comuta metoda de introducere sau a reporni Chrome cu un clic
- 🌐 Acces prin tunel Cloudflare — fără IP public, fără redirecționare de porturi
- 🖱️ Conectează-te de pe telefon, tabletă sau computer (client web noVNC)
- ⏱️ Fiecare sesiune durează până la ~6 ore și o poți anula oricând

## 🚀 Cum se folosește (Fork și gata)

### Pasul 1: Fă fork la acest proiect

Apasă butonul **Fork** din colțul din dreapta sus al acestei pagini pentru a copia proiectul în contul tău GitHub. După fork, vei ajunge în depozitul `your-username/cloud-browser`.

> 💡 De ce fork? GitHub Actions poate rula doar în depozite din contul tău — fork-ul îți dă permisiunea să pornești rulări.

### Pasul 2: Pornește browserul în cloud

1. Mergi la pagina depozitului tău cu fork și apasă fila **Actions** din partea de sus
2. Găsește **Free Cloud Browser** în bara laterală din stânga și apasă pe el
3. Apasă butonul **Run workflow** din dreapta — apar două câmpuri de intrare:

| Parametru | Descriere |
|-----------|-------------|
| VNC password | Parola pe care o vei introduce pentru a te conecta la desktop; doar primele 8 caractere sunt efective, folosește litere + cifre (ex. `abc12345`), **noteaz-o**; parolă de unică folosință — nu folosi una pe care o folosești în altă parte |
| Runtime | Câte minute rămâne activă această sesiune; implicit 300 (5 ore), maximum 350 |

4. Apasă butonul verde **Run workflow** pentru a confirma, iar browserul în cloud începe să pornească

### Pasul 3: Obține URL-ul de acces

1. Pe pagina Actions, intră în rularea pe care tocmai ai pornit-o (cea de sus; un punct galben înseamnă că rulează)
2. Așteaptă aproximativ 2–4 minute ca mașina virtuală să termine instalarea software-ului și configurarea tunelului
3. Apasă pe pasul de build pentru a extinde logurile și derulează în jos pentru a găsi un URL ca acesta:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Copiază acest URL și deschide-l într-un browser (browserul nativ al telefonului merge bine)

### Pasul 4: Conectează-te și folosește

1. Pe pagina noVNC care se deschide, apasă **Connect**
2. Introdu parola VNC setată la Pasul 2
3. Vei vedea desktopul Ubuntu și Chrome — bucură-te 🎉

> ⌨️ Metodă de introducere: chineză Pinyin implicit; apasă **Ctrl+Space** pentru a comuta între chineză/engleză sau apasă clic dreapta pe desktop și alege „Switch Input Method 中/英”.
> 📋 Lipire chineză: copiază text chinezesc pe telefon și lipește-l direct pe desktopul la distanță.

### Pasul 5: Nu uita să-l închizi

- Întoarce-te pe pagina Actions, deschide acea rulare și apasă **Cancel run** în colțul din dreapta sus — mașina virtuală este distrusă și tunelul nu mai funcționează
- Se încheie și automat odată ce durata setată expiră, deci nu-ți face griji că ar rula la nesfârșit

## ⚠️ Note

- **URL-ul este diferit de fiecare dată**: URL-urile vechi nu mai funcționează odată ce rularea anterioară se încheie — folosește întotdeauna URL-ul din logurile celei mai recente rulări
- **Nimic nu se salvează**: odată ce mașina virtuală este distrusă, marcajele browserului, fișierele descărcate și sesiunile de autentificare sunt șterse — mută fișierele importante la timp
- **Reguli de parolă**: doar litere și cifre, maximum 8 caractere; este o parolă de unică folosință, nu folosi una pe care o folosești regulat
- **Nu apăsa Re-run**: pentru a porni o sesiune nouă, apasă **Run workflow** — Re-run ar rula codul vechi
- **Conexiune lentă/sacadată**: tunelul trece prin Cloudflare, deci vitezele din China continentală depind de condițiile rețelei tale — utilizabil, dar nu te aștepta la minuni

## 🛠️ Vrei să-l personalizezi singur?

Fișierul de workflow se află în `.github/workflows/cloud-browser.yml` — deschide-l chiar în interfața web GitHub, editează-l, iar modificările intră în vigoare la commit.

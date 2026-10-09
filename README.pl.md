[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Darmowa przeglądarka chmurowa

Użyj darmowej maszyny wirtualnej Ubuntu z GitHub Actions, aby uruchomić pulpit chmurowy dostępny z przeglądarki, z wbudowanym Chrome. Otwórz stronę internetową i masz komputer chmurowy połączony z internetem — wyłącz go, gdy skończysz. Całkowicie za darmo.

## ✨ Funkcje

- 🌐 Pulpit Ubuntu + przeglądarka Chrome, obsługiwane bezpośrednio w przeglądarce
- ⌨️ Wbudowana chińska metoda wprowadzania fcitx5 (pinyin), przełączanie chiński/angielski za pomocą `Ctrl+Space`
- 📋 Chiński tekst skopiowany w telefonie można wkleić bezpośrednio na zdalny pulpit
- 🖱️ Menu pulpitu pod prawym przyciskiem myszy, aby przełączyć metodę wprowadzania lub zrestartować Chrome jednym kliknięciem
- 🌐 Dostęp przez tunel Cloudflare — bez publicznego IP, bez przekierowywania portów
- 🖱️ Połącz się z telefonu, tabletu lub komputera (klient webowy noVNC)
- ⏱️ Każda sesja trwa do ~6 godzin i możesz ją anulować w dowolnym momencie

## 🚀 Jak używać (Sforkuj i działaj)

### Krok 1: Sforkuj ten projekt

Kliknij przycisk **Fork** w prawym górnym rogu tej strony, aby skopiować projekt na własne konto GitHub. Po zrobieniu forka znajdziesz się w repozytorium `your-username/cloud-browser`.

> 💡 Po co fork? GitHub Actions może działać tylko w repozytoriach pod Twoim kontem — fork daje Ci uprawnienia do uruchamiania.

### Krok 2: Uruchom przeglądarkę chmurową

1. Przejdź do strony swojego sforknowanego repozytorium i kliknij zakładkę **Actions** u góry
2. Znajdź **Free Cloud Browser** na lewym pasku bocznym i kliknij
3. Kliknij przycisk **Run workflow** po prawej — wyskoczą dwa pola wejściowe:

| Parametr | Opis |
|-----------|-------------|
| VNC password | Hasło, które wpiszesz, aby połączyć się z pulpitem; skuteczne jest tylko pierwszych 8 znaków, używaj liter + cyfr (np. `abc12345`), **zapisz je**; hasło jednorazowe — nie używaj takiego, którego używasz gdzie indziej |
| Runtime | Ile minut ta sesja pozostanie aktywna; domyślnie 300 (5 godzin), maksymalnie 350 |

4. Kliknij zielony przycisk **Run workflow**, aby potwierdzić, i przeglądarka chmurowa zaczyna się uruchamiać

### Krok 3: Pobierz adres URL dostępu

1. Na stronie Actions kliknij uruchomienie, które właśnie rozpocząłeś (to najwyższe; żółta kropka oznacza, że działa)
2. Odczekaj około 2–4 minut, aż maszyna wirtualna zakończy instalację oprogramowania i konfigurację tunelu
3. Kliknij krok kompilacji, aby rozwinąć logi, i przewiń w dół, aby znaleźć adres URL podobny do tego:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Skopiuj ten adres URL i otwórz go w przeglądarce (wbudowana przeglądarka telefonu działa dobrze)

### Krok 4: Połącz się i używaj

1. Na otwartej stronie noVNC kliknij **Connect**
2. Wpisz hasło VNC ustawione w kroku 2
3. Zobaczysz pulpit Ubuntu i Chrome — ciesz się 🎉

> ⌨️ Metoda wprowadzania: domyślnie pinyin chiński; naciśnij **Ctrl+Space**, aby przełączać się między chińskim a angielskim, lub kliknij pulpit prawym przyciskiem myszy i wybierz „Switch Input Method 中/英”.
> 📋 Wklejanie chińskiego: skopiuj chiński tekst w telefonie i wklej go prosto na zdalny pulpit.

### Krok 5: Pamiętaj o wyłączeniu

- Wróć na stronę Actions, otwórz to uruchomienie i kliknij **Cancel run** w prawym górnym rogu — maszyna wirtualna zostanie zniszczona, a tunel przestanie działać
- Zakończy się również automatycznie po upływie ustawionego czasu, więc nie musisz się martwić, że będzie działać bez końca

## ⚠️ Uwagi

- **Adres URL jest za każdym razem inny**: stare adresy przestają działać, gdy poprzednie uruchomienie się zakończy — zawsze używaj adresu z logów najnowszego uruchomienia
- **Nic nie jest zapisywane**: po zniszczeniu maszyny wirtualnej zakładki przeglądarki, pobrane pliki i sesje logowania zostaną wyczyszczone — przenieś ważne pliki na czas
- **Zasady hasła**: tylko litery i cyfry, maksymalnie 8 znaków; to hasło jednorazowe, nie używaj takiego, którego używasz regularnie
- **Nie klikaj Re-run**: aby rozpocząć nową sesję, kliknij **Run workflow** — Re-run uruchomiłby stary kod
- **Wolne/klatkujące połączenie**: tunel przechodzi przez Cloudflare, więc prędkości z Chin kontynentalnych zależą od warunków Twojej sieci — używalne, ale nie oczekuj cudów

## 🛠️ Chcesz dostosować samodzielnie?

Plik przepływu pracy znajduje się w `.github/workflows/cloud-browser.yml` — otwórz go bezpośrednio w interfejsie internetowym GitHub, edytuj, a zmiany zaczną obowiązywać po commicie.

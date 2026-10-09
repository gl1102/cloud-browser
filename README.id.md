[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Browser Cloud Gratis

Gunakan VM Ubuntu gratis dari GitHub Actions untuk menjalankan desktop cloud yang bisa diakses dari browser, dengan Chrome bawaan. Buka halaman web dan Anda punya PC cloud yang terhubung internet — matikan setelah selesai. Sepenuhnya gratis.

## ✨ Fitur

- 🌐 Desktop Ubuntu + browser Chrome, dioperasikan langsung di browser Anda
- ⌨️ Metode input bahasa Mandarin fcitx5 (Pinyin) bawaan, beralih antara Mandarin/Inggris dengan `Ctrl+Space`
- 📋 Teks Mandarin yang disalin di ponsel bisa langsung ditempel ke desktop jarak jauh
- 🖱️ Menu klik kanan desktop untuk mengganti metode input atau me-restart Chrome dengan sekali klik
- 🌐 Akses via tunnel Cloudflare — tanpa IP publik, tanpa perlu port forwarding
- 🖱️ Terhubung dari ponsel, tablet, atau komputer (klien web noVNC)
- ⏱️ Setiap sesi berjalan hingga ~6 jam, dan bisa dibatalkan kapan saja

## 🚀 Cara Penggunaan (Fork lalu Jalan)

### Langkah 1: Fork Proyek Ini

Klik tombol **Fork** di kanan atas halaman ini untuk menyalin proyek ke akun GitHub Anda sendiri. Setelah di-fork, Anda akan masuk ke repositori `your-username/cloud-browser`.

> 💡 Kenapa fork? GitHub Actions hanya bisa berjalan di repositori di bawah akun Anda sendiri — fork memberi Anda izin untuk memulai sesi.

### Langkah 2: Mulai Browser Cloud

1. Buka halaman repositori hasil fork Anda dan klik tab **Actions** di atas
2. Temukan **Free Cloud Browser** di bilah sisi kiri dan klik
3. Klik tombol **Run workflow** di kanan — dua kolom input akan muncul:

| Parameter | Deskripsi |
|-----------|-------------|
| Kata sandi VNC | Kata sandi yang akan Anda masukkan untuk terhubung ke desktop; hanya 8 karakter pertama yang berlaku, gunakan huruf + angka (mis. `abc12345`), **catat**; kata sandi sekali pakai — jangan gunakan kata sandi yang Anda pakai di tempat lain |
| Durasi sesi | Berapa menit sesi ini tetap berjalan; default 300 (5 jam), maks 350 |

4. Klik tombol hijau **Run workflow** untuk mengonfirmasi, dan browser cloud Anda mulai diluncurkan

### Langkah 3: Dapatkan URL Akses

1. Di halaman Actions, klik sesi yang baru Anda mulai (yang paling atas; titik kuning berarti sedang berjalan)
2. Tunggu sekitar 2–4 menit hingga VM selesai menginstal perangkat lunak dan menyiapkan tunnel
3. Klik langkah build untuk membuka log, dan gulir ke bawah untuk menemukan URL seperti ini:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Salin URL ini dan buka di browser (browser bawaan ponsel juga bisa)

### Langkah 4: Terhubung dan Gunakan

1. Di halaman noVNC yang terbuka, klik **Connect**
2. Masukkan kata sandi VNC yang Anda atur di Langkah 2
3. Anda akan melihat desktop Ubuntu dan Chrome — nikmati 🎉

> ⌨️ Metode input: Pinyin Mandarin secara default; tekan **Ctrl+Space** untuk beralih antara Mandarin/Inggris, atau klik kanan desktop dan pilih "Switch Input Method 中/英".
> 📋 Menempel bahasa Mandarin: salin teks Mandarin di ponsel Anda dan tempel langsung ke desktop jarak jauh.

### Langkah 5: Jangan Lupa Mematikannya

- Kembali ke halaman Actions, buka sesi tersebut, dan klik **Cancel run** di kanan atas — VM dihancurkan dan tunnel berhenti berfungsi
- Sesi juga berakhir otomatis setelah durasi yang ditetapkan berlalu, jadi tidak perlu khawatir

## ⚠️ Catatan

- **URL berbeda setiap kali**: URL lama berhenti berfungsi begitu sesi sebelumnya berakhir — selalu gunakan URL dari log sesi terbaru
- **Tidak ada yang tersimpan**: setelah VM dihancurkan, bookmark browser, file yang diunduh, dan sesi login semuanya terhapus — pindahkan file penting tepat waktu
- **Aturan kata sandi**: huruf dan angka saja, maks 8 karakter; ini kata sandi sekali pakai, jangan gunakan kata sandi yang biasa Anda pakai
- **Jangan klik Re-run**: untuk memulai sesi baru klik **Run workflow** — Re-run akan menjalankan kode lama
- **Koneksi lambat/ngelag**: tunnel melewati Cloudflare, jadi kecepatan dari Tiongkok daratan tergantung kondisi jaringan Anda — bisa dipakai, tapi jangan berharap keajaiban

## 🛠️ Ingin Mengubah Sendiri?

File workflow ada di `.github/workflows/cloud-browser.yml` — buka langsung di UI web GitHub, edit, dan perubahan Anda berlaku setelah commit.

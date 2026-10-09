[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Ücretsiz Bulut Tarayıcı

GitHub Actions'ın ücretsiz Ubuntu sanal makinesini kullanarak tarayıcıdan erişilebilen, içinde Chrome bulunan bir bulut masaüstü başlatın. Bir web sayfası açın ve internete bağlı bir bulut PC'niz olsun — işiniz bitince kapatın. Tamamen ücretsiz.

## ✨ Özellikler

- 🌐 Ubuntu masaüstü + Chrome tarayıcı, doğrudan tarayıcınızda çalıştırılır
- ⌨️ Yerleşik fcitx5 Çince giriş yöntemi (Pinyin), `Ctrl+Space` ile Çince/İngilizce arasında geçiş
- 📋 Telefonunuzda kopyaladığınız Çince metin doğrudan uzak masaüstüne yapıştırılabilir
- 🖱️ Giriş yöntemini değiştirmek veya Chrome'u tek tıkla yeniden başlatmak için masaüstü sağ tık menüsü
- 🌐 Cloudflare tüneli ile erişim — genel IP yok, port yönlendirmeye gerek yok
- 🖱️ Telefondan, tabletten veya bilgisayardan bağlanın (noVNC web istemcisi)
- ⏱️ Her oturum ~6 saate kadar sürer ve istediğiniz zaman iptal edebilirsiniz

## 🚀 Nasıl kullanılır (Fork'layın ve kullanın)

### Adım 1: Bu projeyi fork'layın

Projeyi kendi GitHub hesabınıza kopyalamak için bu sayfanın sağ üst köşesindeki **Fork** düğmesine tıklayın. Fork'ladıktan sonra `your-username/cloud-browser` deposuna ulaşırsınız.

> 💡 Neden fork? GitHub Actions yalnızca kendi hesabınızdaki depolarda çalışabilir — fork, çalıştırma başlatma izni verir.

### Adım 2: Bulut tarayıcıyı başlatın

1. Fork'ladığınız deponun sayfasına gidin ve üstteki **Actions** sekmesine tıklayın
2. Soldaki kenar çubuğunda **Free Cloud Browser**'ı bulun ve tıklayın
3. Sağdaki **Run workflow** düğmesine tıklayın — iki giriş alanı açılır:

| Parametre | Açıklama |
|-----------|-------------|
| VNC password | Masaüstüne bağlanmak için gireceğiniz parola; yalnızca ilk 8 karakter geçerli, harf + rakam kullanın (örn. `abc12345`), **not edin**; tek kullanımlık parola — başka yerde kullandığınız bir parolayı kullanmayın |
| Runtime | Bu oturumun kaç dakika açık kalacağı; varsayılan 300 (5 saat), en fazla 350 |

4. Onaylamak için yeşil **Run workflow** düğmesine tıklayın ve bulut tarayıcınız açılmaya başlar

### Adım 3: Erişim URL'sini alın

1. Actions sayfasında az önce başlattığınız çalıştırmaya tıklayın (en üstteki; sarı nokta çalışıyor demek)
2. Sanal makinenin yazılım kurulumunu ve tünel yapılandırmasını bitirmesi için yaklaşık 2–4 dakika bekleyin
3. Günlükleri genişletmek için derleme adımına tıklayın ve aşağı kaydırarak şuna benzer bir URL bulun:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Bu URL'yi kopyalayın ve bir tarayıcıda açın (telefonunuzun yerleşik tarayıcısı gayet iyi çalışır)

### Adım 4: Bağlanın ve kullanın

1. Açılan noVNC sayfasında **Connect**'e tıklayın
2. Adım 2'de belirlediğiniz VNC parolasını girin
3. Ubuntu masaüstünü ve Chrome'u göreceksiniz — keyfini çıkarın 🎉

> ⌨️ Giriş yöntemi: varsayılan olarak Pinyin Çince; Çince/İngilizce arasında geçiş için **Ctrl+Space**'e basın veya masaüstüne sağ tıklayıp "Switch Input Method 中/英" seçin.
> 📋 Çince yapıştırma: telefonunuzda Çince metni kopyalayın ve doğrudan uzak masaüstüne yapıştırın.

### Adım 5: Kapatmayı unutmayın

- Actions sayfasına dönün, o çalıştırmayı açın ve sağ üstteki **Cancel run** düğmesine tıklayın — sanal makine yok edilir ve tünel çalışmayı bırakır
- Belirlenen süre dolduğunda da otomatik olarak sona erer, sonsuza kadar çalışacağından endişelenmenize gerek yok

## ⚠️ Notlar

- **URL her seferinde farklıdır**: önceki çalıştırma bittikten sonra eski URL'ler çalışmayı bırakır — her zaman en son çalıştırmanın günlüklerindeki URL'yi kullanın
- **Hiçbir şey kaydedilmez**: sanal makine yok edildiğinde tarayıcı yer imleri, indirilen dosyalar ve oturum açma oturumları silinir — önemli dosyaları zamanında taşıyın
- **Parola kuralları**: yalnızca harf ve rakam, en fazla 8 karakter; tek kullanımlık bir paroladır, düzenli kullandığınız bir parolayı kullanmayın
- **Re-run'a tıklamayın**: yeni bir oturum başlatmak için **Run workflow**'a tıklayın — Re-run eski kodu çalıştırır
- **Yavaş/takılan bağlantı**: tünel Cloudflare üzerinden geçiyor, bu nedenle Çin ana karasından hızlar ağ koşullarınıza bağlı — kullanılabilir, ancak mucize beklemeyin

## 🛠️ Kendiniz düzenlemek ister misiniz?

İş akışı dosyası `.github/workflows/cloud-browser.yml` konumunda — doğrudan GitHub web arayüzünde açın, düzenleyin ve değişiklikleriniz commit'te geçerli olur.

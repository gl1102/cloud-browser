[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Trình duyệt đám mây miễn phí

Dùng máy ảo Ubuntu miễn phí của GitHub Actions để dựng một máy tính đám mây truy cập từ trình duyệt, tích hợp sẵn Chrome. Mở một trang web là bạn có ngay một chiếc PC đám mây kết nối internet — tắt đi khi dùng xong. Hoàn toàn miễn phí.

## ✨ Tính năng

- 🌐 Máy tính Ubuntu + trình duyệt Chrome, vận hành ngay trong trình duyệt của bạn
- ⌨️ Bộ gõ tiếng Trung fcitx5 tích hợp sẵn (Pinyin), chuyển giữa tiếng Trung/tiếng Anh bằng `Ctrl+Space`
- 📋 Văn bản tiếng Trung sao chép trên điện thoại có thể dán trực tiếp vào máy tính từ xa
- 🖱️ Menu chuột phải trên màn hình để chuyển phương thức nhập liệu hoặc khởi động lại Chrome chỉ bằng một cú nhấp
- 🌐 Truy cập qua tunnel Cloudflare — không cần IP công cộng, không cần mở port
- 🖱️ Kết nối từ điện thoại, máy tính bảng hoặc máy tính (ứng dụng web noVNC)
- ⏱️ Mỗi phiên kéo dài tới ~6 giờ, và bạn có thể hủy bất cứ lúc nào

## 🚀 Cách dùng (Fork là dùng ngay)

### Bước 1: Fork dự án này

Nhấn nút **Fork** ở góc trên bên phải trang này để sao chép dự án về tài khoản GitHub của bạn. Sau khi fork, bạn sẽ ở trong kho `your-username/cloud-browser`.

> 💡 Vì sao phải fork? GitHub Actions chỉ chạy được trên các kho thuộc tài khoản của bạn — fork giúp bạn có quyền khởi động các lần chạy.

### Bước 2: Khởi động trình duyệt đám mây

1. Vào trang kho đã fork của bạn và nhấn tab **Actions** ở trên cùng
2. Tìm **Free Cloud Browser** ở thanh bên trái và nhấn vào
3. Nhấn nút **Run workflow** ở bên phải — hai ô nhập hiện ra:

| Tham số | Mô tả |
|-----------|-------------|
| VNC password | Mật khẩu bạn sẽ nhập để kết nối tới máy tính; chỉ 8 ký tự đầu có hiệu lực, dùng chữ cái + số (ví dụ `abc12345`), **hãy ghi lại**; mật khẩu dùng một lần — đừng dùng mật khẩu bạn dùng ở nơi khác |
| Runtime | Phiên này sẽ duy trì trong bao nhiêu phút; mặc định 300 (5 giờ), tối đa 350 |

4. Nhấn nút xanh **Run workflow** để xác nhận, và trình duyệt đám mây bắt đầu khởi động

### Bước 3: Lấy URL truy cập

1. Trên trang Actions, nhấn vào lần chạy bạn vừa khởi động (cái trên cùng; dấu chấm vàng nghĩa là đang chạy)
2. Đợi khoảng 2–4 phút để máy ảo hoàn tất cài đặt phần mềm và thiết lập tunnel
3. Nhấn vào bước build để mở rộng logs và cuộn xuống để tìm một URL như thế này:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Sao chép URL này và mở trong trình duyệt (trình duyệt tích hợp của điện thoại hoạt động tốt)

### Bước 4: Kết nối và sử dụng

1. Trên trang noVNC vừa mở, nhấn **Connect**
2. Nhập mật khẩu VNC bạn đã đặt ở Bước 2
3. Bạn sẽ thấy màn hình Ubuntu và Chrome — tận hưởng 🎉

> ⌨️ Phương thức nhập liệu: mặc định là Pinyin tiếng Trung; nhấn **Ctrl+Space** để chuyển giữa tiếng Trung/tiếng Anh, hoặc nhấn chuột phải trên màn hình và chọn "Switch Input Method 中/英".
> 📋 Dán tiếng Trung: sao chép văn bản tiếng Trung trên điện thoại và dán thẳng vào máy tính từ xa.

### Bước 5: Nhớ tắt đi

- Quay lại trang Actions, mở lần chạy đó và nhấn **Cancel run** ở góc trên bên phải — máy ảo bị hủy và tunnel ngừng hoạt động
- Nó cũng tự kết thúc khi hết thời gian đã đặt, nên bạn không lo nó chạy mãi

## ⚠️ Lưu ý

- **URL khác nhau mỗi lần**: các URL cũ ngừng hoạt động khi lần chạy trước kết thúc — luôn dùng URL từ logs của lần chạy mới nhất
- **Không lưu gì cả**: khi máy ảo bị hủy, dấu trang trình duyệt, các tệp đã tải và phiên đăng nhập đều bị xóa — hãy di chuyển các tệp quan trọng ra kịp thời
- **Quy tắc mật khẩu**: chỉ chữ cái và số, tối đa 8 ký tự; đây là mật khẩu dùng một lần, đừng dùng mật khẩu bạn dùng thường xuyên
- **Đừng nhấn Re-run**: để bắt đầu phiên mới, hãy nhấn **Run workflow** — Re-run sẽ chạy mã cũ
- **Kết nối chậm/giật**: tunnel đi qua Cloudflare, nên tốc độ từ Trung Quốc đại lục phụ thuộc vào điều kiện mạng của bạn — dùng được, nhưng đừng kỳ vọng điều kỳ diệu

## 🛠️ Muốn tự tùy chỉnh?

Tệp workflow nằm ở `.github/workflows/cloud-browser.yml` — mở trực tiếp trong giao diện web GitHub, chỉnh sửa, và thay đổi của bạn có hiệu lực khi commit.

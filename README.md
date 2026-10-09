[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — 免费云浏览器

用 GitHub Actions 的免费 Ubuntu 虚拟机，打造一个可以通过浏览器远程访问的云桌面，内置 Chrome 浏览器。打开网页就能用一台能上网的云电脑，不用时关掉就行，全程免费。

## ✨ 功能

- 🌐 Ubuntu 桌面 + Chrome 浏览器，浏览器里直接操作
- ⌨️ 内置 fcitx5 中文输入法（拼音），`Ctrl+Space` 中/英切换
- 📋 手机上复制中文可直接粘贴进远程桌面
- 🖱️ 桌面右键菜单可一键切换输入法、重启 Chrome
- 🌐 通过 Cloudflare 隧道访问，免公网 IP、免内网穿透
- 🖱️ 手机、平板、电脑都能连（noVNC 网页客户端）
- ⏱️ 单次最长运行约 6 小时，可随时取消

## 🚀 使用方法（fork 后即用）

### 第 1 步：Fork 本项目

点击本页面右上角的 **Fork** 按钮，把项目复制到你自己的 GitHub 账号下。Fork 完成后你会进入 `你的用户名/cloud-browser` 这个仓库。

> 💡 为什么要 fork？GitHub Actions 只能运行在你自己账号下的仓库里，fork 后你才有权限点运行。

### 第 2 步：启动云浏览器

1. 进入你 fork 后的仓库页面，点击顶部 **Actions** 标签页
2. 左侧找到 **Free Cloud Browser**，点击它
3. 点击右侧 **Run workflow** 按钮，会弹出两个输入框：

| 参数 | 说明 |
|------|------|
| VNC 密码 | 连接桌面时要输入的密码，最多 8 位有效，用英文+数字（比如 `abc12345`），**记下来**；用完即弃，别用常用密码 |
| 运行时长 | 本次云桌面保持运行的分钟数，默认 300（5 小时），最多填 350 |

4. 点绿色的 **Run workflow** 确认，云浏览器就开始启动了

### 第 3 步：获取访问地址

1. 在 Actions 页面点进刚才那次运行（最上面那条，黄色圆点表示正在运行）
2. 等待约 2～4 分钟，让虚拟机装好软件、建好隧道
3. 点击构建步骤展开日志，往下翻找到类似这样的地址：

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. 复制这个地址，用浏览器打开（手机自带浏览器就行）

### 第 4 步：连接使用

1. 在打开的 noVNC 页面点 **Connect**
2. 输入第 2 步设置的 VNC 密码
3. 看到 Ubuntu 桌面和 Chrome 了，开始用吧 🎉

> ⌨️ 输入法：默认拼音中文，按 **Ctrl+Space** 在中/英之间切换；也可以在桌面点右键选"切换输入法 中/英"。
> 📋 粘贴中文：在手机上复制好中文，直接粘贴进远程桌面即可。

### 第 5 步：用完记得关

- 回到 Actions 页面，点进那次运行，右上角 **Cancel run** 取消，虚拟机销毁，隧道失效
- 超过设定的运行时长会自动结束，不用担心一直跑

## ⚠️ 注意事项

- **每次运行地址都不一样**：旧地址在上一次运行结束后就失效了，一定要用最新一次运行日志里的地址
- **数据不保存**：虚拟机销毁后，浏览器书签、下载文件、登录状态全部清空，重要文件及时传出来
- **密码规则**：只用英文和数字，8 位以内；这是临时密码，别用你常用的密码
- **别点 Re-run**：要开新的请点 **Run workflow**，Re-run 会用旧代码跑
- **连接慢/卡**：隧道走 Cloudflare，国内访问速度看网络情况，凑合能用

## 🛠️ 想自己改？

工作流文件在 `.github/workflows/cloud-browser.yml`，直接在 GitHub 网页上点进去就能编辑，改完提交即生效。

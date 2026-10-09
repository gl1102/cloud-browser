[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Navegador gratuito na nuvem

Use a máquina virtual Ubuntu gratuita do GitHub Actions para rodar uma área de trabalho na nuvem acessível pelo navegador, com o Chrome integrado. Abra uma página da web e você tem um PC na nuvem conectado à internet — desligue quando terminar. Totalmente grátis.

## ✨ Recursos

- 🌐 Área de trabalho Ubuntu + navegador Chrome, operados direto no seu navegador
- ⌨️ Método de entrada em chinês fcitx5 integrado (Pinyin), alterne entre chinês/inglês com `Ctrl+Space`
- 📋 Texto em chinês copiado no celular pode ser colado diretamente na área de trabalho remota
- 🖱️ Menu de clique com o botão direito na área de trabalho para trocar o método de entrada ou reiniciar o Chrome com um clique
- 🌐 Acesso via túnel Cloudflare — sem IP público, sem necessidade de redirecionamento de portas
- 🖱️ Conecte-se pelo celular, tablet ou computador (cliente web noVNC)
- ⏱️ Cada sessão dura até ~6 horas, e você pode cancelar a qualquer momento

## 🚀 Como usar (faça fork e pronto)

### Etapa 1: Faça um fork deste projeto

Clique no botão **Fork** no canto superior direito desta página para copiar o projeto para a sua conta do GitHub. Depois do fork, você estará no repositório `your-username/cloud-browser`.

> 💡 Por que fazer fork? O GitHub Actions só pode ser executado em repositórios da sua própria conta — o fork dá a você permissão para iniciar execuções.

### Etapa 2: Inicie o navegador na nuvem

1. Acesse a página do seu repositório com fork e clique na aba **Actions** no topo
2. Encontre **Free Cloud Browser** na barra lateral esquerda e clique nele
3. Clique no botão **Run workflow** à direita — dois campos de entrada aparecem:

| Parâmetro | Descrição |
|-----------|-------------|
| VNC password | A senha que você vai digitar para se conectar à área de trabalho; apenas os primeiros 8 caracteres são efetivos, use letras + números (ex.: `abc12345`), **anote-a**; senha descartável — não use uma que você usa em outros lugares |
| Runtime | Por quantos minutos esta sessão ficará ativa; padrão 300 (5 horas), máximo 350 |

4. Clique no botão verde **Run workflow** para confirmar, e o navegador na nuvem começa a iniciar

### Etapa 3: Obtenha o URL de acesso

1. Na página Actions, entre na execução que você acabou de iniciar (a de cima; um ponto amarelo significa que está rodando)
2. Aguarde cerca de 2–4 minutos para a VM terminar de instalar o software e configurar o túnel
3. Clique na etapa de build para expandir os logs e role para baixo para encontrar um URL como este:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Copie este URL e abra-o em um navegador (o navegador nativo do celular funciona bem)

### Etapa 4: Conecte-se e use

1. Na página do noVNC que abrir, clique em **Connect**
2. Digite a senha VNC que você definiu na Etapa 2
3. Você verá a área de trabalho Ubuntu e o Chrome — aproveite 🎉

> ⌨️ Método de entrada: chinês Pinyin por padrão; pressione **Ctrl+Space** para alternar entre chinês/inglês, ou clique com o botão direito na área de trabalho e escolha "Switch Input Method 中/英".
> 📋 Colando chinês: copie texto em chinês no celular e cole diretamente na área de trabalho remota.

### Etapa 5: Lembre-se de desligar

- Volte para a página Actions, abra essa execução e clique em **Cancel run** no canto superior direito — a VM é destruída e o túnel para de funcionar
- Ela também termina automaticamente quando o tempo definido acaba, então não se preocupe com ela rodando para sempre

## ⚠️ Observações

- **O URL é diferente a cada vez**: URLs antigos param de funcionar quando a execução anterior termina — use sempre o URL dos logs da execução mais recente
- **Nada é salvo**: quando a VM é destruída, favoritos do navegador, arquivos baixados e sessões de login são apagados — mova arquivos importantes a tempo
- **Regras de senha**: apenas letras e números, máximo de 8 caracteres; é uma senha descartável, não use uma que você usa regularmente
- **Não clique em Re-run**: para iniciar uma nova sessão, clique em **Run workflow** — o Re-run executaria o código antigo
- **Conexão lenta/travando**: o túnel passa pela Cloudflare, então as velocidades da China continental dependem das condições da sua rede — utilizável, mas não espere milagres

## 🛠️ Quer personalizar por conta própria?

O arquivo de workflow está em `.github/workflows/cloud-browser.yml` — abra-o direto na interface web do GitHub, edite, e as mudanças entram em vigor no commit.

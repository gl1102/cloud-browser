[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Navegador en la nube gratuito

Usa la máquina virtual gratuita de Ubuntu de GitHub Actions para crear un escritorio en la nube que puedes controlar desde el navegador, con Chrome integrado. Abre una página web y tendrás un PC en la nube con internet; apágalo cuando termines. Totalmente gratis.

## ✨ Características

- 🌐 Escritorio Ubuntu + navegador Chrome, todo dentro del navegador
- ⌨️ Método de entrada en chino fcitx5 (pinyin) integrado, cambia entre chino/inglés con `Ctrl+Space`
- 📋 El texto chino copiado en tu móvil se puede pegar directamente en el escritorio remoto
- 🖱️ Menú de clic derecho en el escritorio para cambiar el método de entrada o reiniciar Chrome con un clic
- 🌐 Acceso mediante túnel de Cloudflare — sin IP pública ni apertura de puertos
- 🖱️ Conéctate desde móvil, tableta u ordenador (cliente web noVNC)
- ⏱️ Cada sesión dura hasta ~6 horas y puedes cancelarla en cualquier momento

## 🚀 Cómo usar (haz fork y listo)

### Paso 1: Haz un fork del proyecto

Pulsa el botón **Fork** en la esquina superior derecha de esta página para copiar el proyecto a tu cuenta de GitHub. Al terminar, entrarás en el repositorio `tu-nombre-de-usuario/cloud-browser`.

> 💡 ¿Por qué hacer fork? GitHub Actions solo puede ejecutarse en repositorios de tu propia cuenta; al hacer fork obtienes permiso para lanzar ejecuciones.

### Paso 2: Inicia el navegador en la nube

1. Entra en tu repositorio tras el fork y pulsa la pestaña **Actions** de arriba
2. En la barra lateral izquierda busca **Free Cloud Browser** y haz clic
3. Pulsa el botón **Run workflow** a la derecha — aparecerán dos campos:

| Parámetro | Descripción |
|-----------|-------------|
| Contraseña VNC | La contraseña para conectar al escritorio; solo los primeros 8 caracteres son efectivos, usa letras + números (p. ej. `abc12345`), **anótala**; es una contraseña desechable, no uses una que uses en otros sitios |
| Duración | Minutos que esta sesión se mantiene activa; por defecto 300 (5 horas), máximo 350 |

4. Pulsa el botón verde **Run workflow** para confirmar y el navegador en la nube empezará a arrancar

### Paso 3: Obtén la dirección de acceso

1. En la página de Actions, entra en la ejecución que acabas de lanzar (la de arriba del todo; el punto amarillo indica que está en curso)
2. Espera unos 2–4 minutos a que la máquina virtual instale el software y cree el túnel
3. Haz clic en el paso de construcción para desplegar los registros y baja hasta encontrar una dirección como esta:

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Copia esta dirección y ábrela en un navegador (el navegador integrado de tu móvil vale)

### Paso 4: Conéctate y úsalo

1. En la página de noVNC que se abre, pulsa **Connect**
2. Introduce la contraseña VNC que configuraste en el paso 2
3. Verás el escritorio de Ubuntu y Chrome — a disfrutar 🎉

> ⌨️ Método de entrada: chino pinyin por defecto; **Ctrl+Space** alterna entre chino e inglés, o haz clic derecho en el escritorio y elige «Cambiar método de entrada 中/英».
> 📋 Pegar chino: copia el texto chino en tu móvil y pégalo directamente en el escritorio remoto.

### Paso 5: Apágalo al terminar

- Vuelve a la página de Actions, entra en esa ejecución y pulsa **Cancel run** arriba a la derecha — la máquina virtual se destruye y el túnel deja de funcionar
- También termina automáticamente al cumplirse la duración configurada, así que no te preocupes de que siga ejecutándose

## ⚠️ Notas

- **La dirección cambia cada vez**: las direcciones antiguas dejan de funcionar al terminar la ejecución anterior — usa siempre la dirección de los registros de la última ejecución
- **Los datos no se guardan**: al destruirse la máquina virtual, los marcadores del navegador, los archivos descargados y las sesiones iniciadas se borran por completo — saca a tiempo los archivos importantes
- **Reglas de la contraseña**: solo letras y números, máximo 8 caracteres; es una contraseña temporal, no uses la que usas habitualmente
- **No pulses Re-run**: para abrir una nueva sesión pulsa **Run workflow** — Re-run ejecutaría el código antiguo
- **Conexión lenta o con cortes**: el túnel pasa por Cloudflare, así que la velocidad desde China depende de tu red — funciona aceptablemente

## 🛠️ ¿Quieres personalizarlo?

El archivo del workflow está en `.github/workflows/cloud-browser.yml`; puedes abrirlo y editarlo directamente en la web de GitHub, y los cambios se aplican al hacer commit.

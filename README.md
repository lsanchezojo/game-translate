# game-translate

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Release](https://img.shields.io/github/v/release/lsanchezojo/game-translate)
![Build](https://github.com/lsanchezojo/game-translate/actions/workflows/build.yml/badge.svg)

Traductor de juegos (y de cualquier cosa en pantalla) **en tiempo real** para
**Wayland/Hyprland**. Selecciona una región, hace **OCR** con Tesseract y la **traduce**
con el endpoint gratuito de Google Translate (sin clave). Muestra el resultado en una
**notificación** (texto corto) o en un **popup desplazable** (texto largo), y lo copia al
portapapeles.

Pensado para juegos por Steam/Proton o nativos: captura a nivel del compositor, así que
funciona con cualquier ventana. **No usa WebKit ni servicios en segundo plano.**

## ✨ Características

- 🎯 OCR de una región, de la pantalla completa, o de una imagen ya guardada.
- 🌐 Traducción gratuita sin API key ni cuenta.
- 🔤 Multilingüe: por defecto inglés→español, configurable a japonés, francés, etc.
- 🪟 Resultado en notificación (corto) o popup `zenity` desplazable (largo), flotante y
  centrado en Hyprland.
- 📋 Copia la traducción al portapapeles automáticamente.
- 🪶 Ligero: shell + grim + tesseract + curl. Sin demonios ni navegadores embebidos.

## 📦 Instalación (Arch / CachyOS)

**Desde el binario** (Release):

```sh
sudo pacman -U game-translate-1.0.0-1-any.pkg.tar.zst
```

**Compilando desde el código** (resuelve dependencias solo):

```sh
git clone https://github.com/lsanchezojo/game-translate
cd game-translate && makepkg -si
```

## ⌨️ Uso

```sh
game-translate translate   # seleccionar región -> traducir
game-translate ocr         # seleccionar región -> solo OCR (copia)
game-translate full        # traducir la pantalla completa
game-translate translate IMAGEN.png   # traducir una imagen ya guardada
```

Lo normal es asignarlo a atajos de teclado. Ejemplo para Hyprland (ver
`hyprland.conf.example`, instalado en `/usr/share/doc/game-translate/`):

```conf
bind = ALT, C, exec, game-translate translate
bind = ALT, X, exec, game-translate ocr
bind = ALT SHIFT, C, exec, game-translate full
```

## ⚙️ Configuración

Por defecto traduce **inglés → español**. Para cambiar idiomas crea
`~/.config/game-translate/config`:

```sh
SL=ja          # idioma origen (código Google Translate)
TL=es          # idioma destino
OCR_LANG=jpn   # idioma del OCR (código Tesseract; instala tesseract-data-<idioma>)
THRESHOLD=300  # nº de caracteres a partir del cual usa el popup en vez de la notificación
```

> El código del OCR (Tesseract) no es el mismo que el de la traducción: inglés es
> `eng`/`en`, japonés `jpn`/`ja`, etc. Instala el paquete `tesseract-data-<idioma>` del
> idioma **origen**. También se puede usar por variables de entorno
> `GAME_TRANSLATE_SL`, `GAME_TRANSLATE_TL`, `GAME_TRANSLATE_OCR_LANG`,
> `GAME_TRANSLATE_THRESHOLD`.

## 🖼️ Capturas

<!-- Sustituye estos huecos por capturas/GIF reales (arrástralos al editar el README en GitHub):
![Notificación](docs/captura-notificacion.png)
![Popup texto largo](docs/captura-popup.png)
-->
_(pendiente de añadir capturas/GIF de ejemplo)_

## 🧩 Dependencias

`grim`, `slurp`, `tesseract` (+ datos del idioma origen), `curl`, `python`, `libnotify`,
`wl-clipboard`, `zenity`. Opcional: `hyprland` (para flotar/centrar el popup
automáticamente).

## 📄 Licencia

MIT — ver [LICENSE](LICENSE).

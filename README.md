# game-translate

Traductor de juegos (y de cualquier cosa en pantalla) **en tiempo real** para
Wayland/Hyprland. Selecciona una región, hace **OCR** con Tesseract y la **traduce**
con el endpoint gratuito de Google Translate (sin clave). Muestra el resultado en una
**notificación** (texto corto) o en un **popup desplazable** (texto largo), y lo copia
al portapapeles. No usa WebKit ni servicios en segundo plano.

## Instalación (Arch / CachyOS)

```sh
makepkg -si          # construye e instala con sus dependencias
# o, si ya está construido:
sudo pacman -U game-translate-1.0.0-1-any.pkg.tar.zst
```

## Uso

```sh
game-translate translate   # seleccionar región -> traducir
game-translate ocr         # seleccionar región -> solo OCR (copia)
game-translate full        # traducir la pantalla completa
game-translate translate IMAGEN.png   # traducir una imagen ya guardada
```

Lo normal es asignarlo a atajos de teclado: ver `hyprland.conf.example`
(instalado en `/usr/share/doc/game-translate/`).

## Configuración

Por defecto traduce **inglés → español**. Para cambiar idiomas, crea
`~/.config/game-translate/config`:

```sh
SL=ja          # idioma origen (código Google Translate)
TL=es          # idioma destino
OCR_LANG=jpn   # idioma del OCR (código Tesseract; instala tesseract-data-<idioma>)
```

(También se puede usar por variables de entorno `GAME_TRANSLATE_SL`,
`GAME_TRANSLATE_TL`, `GAME_TRANSLATE_OCR_LANG`, `GAME_TRANSLATE_THRESHOLD`.)

Recuerda que **el código del OCR (Tesseract) no es el mismo que el de la traducción**:
inglés es `eng`/`en`, japonés `jpn`/`ja`, etc., y necesitas el paquete
`tesseract-data-<idioma>` correspondiente.

## Dependencias

grim, slurp, tesseract (+ datos del idioma origen), curl, python, libnotify,
wl-clipboard, zenity. Opcional: hyprland (para flotar/centrar el popup automáticamente).

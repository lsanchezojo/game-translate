# Maintainer: Luis Sánchez <lsanchezojo@gmail.com>
pkgname=game-translate
pkgver=1.0.0
pkgrel=1
pkgdesc="Traductor de juegos en tiempo real: OCR de una región de pantalla + traducción (Wayland/Hyprland)"
arch=('any')
url="https://local/game-translate"
license=('MIT')
depends=('grim' 'slurp' 'tesseract' 'tesseract-data-eng' 'curl' 'python' 'libnotify' 'wl-clipboard' 'zenity')
optdepends=('hyprland: flotado y centrado automático del popup de texto largo'
            'tesseract-data-spa: OCR de texto en español'
            'tesseract-data-jpn: OCR de texto en japonés')
backup=()
source=('game-translate'
        'game-translate.desktop'
        'hyprland.conf.example'
        'README.md')
sha256sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP')

package() {
  install -Dm755 "$srcdir/game-translate"          "$pkgdir/usr/bin/game-translate"
  install -Dm644 "$srcdir/game-translate.desktop"  "$pkgdir/usr/share/applications/game-translate.desktop"
  install -Dm644 "$srcdir/hyprland.conf.example"   "$pkgdir/usr/share/doc/$pkgname/hyprland.conf.example"
  install -Dm644 "$srcdir/README.md"               "$pkgdir/usr/share/doc/$pkgname/README.md"
}

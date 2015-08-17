# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-after-syntax-vim-git
pkgver=20110706
pkgrel=1
pkgdesc="Extended syntax highlighting rules for Vimscript"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/trapd00r/vim-after-syntax-vim"
license=('BSD')
source=(git+https://github.com/trapd00r/vim-after-syntax-vim)
sha256sums=('SKIP')
provides=('vim-after-syntax-vim')
conflicts=('vim-after-syntax-vim')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing docs...'
  install -Dm 644 README.md "$pkgdir/usr/share/doc/vim-after-syntax-vim/README.md"

  msg 'Installing dirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _dir in after; do
    cp -R $_dir "$pkgdir/usr/share/vim/vimfiles/$_dir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}

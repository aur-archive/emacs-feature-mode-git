# Contributor: Philip Mueller <mail at philip.in-aachen dot net>
pkgname=emacs-feature-mode-git
pkgver=20120625
pkgrel=3
pkgdesc="An emacs mode for editing cucumber feature files"
arch=("any")
url="http://cukes.info/"
license=('GPL')
makedepends=('git')
provides=(emacs-feature-mode, emacs-cucumber-mode)
install=emacs-feature-mode-git.install

_gitname="cucumber.el"
_gitroot="git://github.com/michaelklishin/$_gitname.git"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"

  cd "$srcdir/$_gitname-build"

  mkdir -p $startdir/pkg/$pkgname/usr/share/emacs/site-lisp/
  install -Dm644 feature-mode.el $startdir/pkg/$pkgname/usr/share/emacs/site-lisp/
} 

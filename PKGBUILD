# Maintainer: Alan Bunbury
pkgname=flybots
pkgver=0.6.0
pkgrel=1
pkgdesc="A three-dimensional clone of the classic bsd-robots game."
arch=('any')
url="https://github.com/bunburya/FlyingRobots"
license=('MIT')
depends=('python' 'tk')
makedepends=('git')
options=(!emptydirs)
conflicts=(flybots-git)

# We don't use the development directive _gitroot and _gitname
# here, as we don't want makepkg's automatic version numbering
git_root='git://github.com/bunburya/FlyingRobots.git'
git_name=FlyingRobots

build() {
  cd "${srcdir}"

  # Download/update library
  msg "Attempting to fetch files from GitHub repository..."
  if [[ -d "${git_name}" ]]; then
    (cd "${git_name}" && git pull origin)
    msg "Local repository updated."
  else
    git clone "${git_root}" "${git_name}"
    msg "Cloned repository from GitHub."
  fi

  cd "${git_name}"
  python setup.py install --root="${pkgdir}/" --optimize=1
  ls
  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:

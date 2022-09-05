#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-defcon/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-defcon/discussions>

_langname="python"
_relname="defcon"

pkgname="${_langname}-${_relname}"
pkgver=0.10.1
pkgrel=1
pkgdesc="A set of UFO based objects for use in font editing applications"
arch=(
  "any"
)
url="https://github.com/robotools/defcon"
license=(
  "MIT"
)
depends=(
  "python"
  "python-fonttools"
  # For fonttools [ufo]
  "python-fs" 
  "python-unicodedata2"
)
makedepends=(
  "python-build"
  "python-installer"
  "python-setuptools-scm"
  "python-wheel"
)
checkdepends=(
	"python-pytest"
	)
optdepends=(
	"python-fontpens"
  "python-lxml: enables faster UFO parsing"
	)
_zipname="${_relname}-${pkgver}"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_zipname}.zip"
)
sha512sums=(
  "33fdb2c0b5d5e8ec5f442eb1d46eb9cc362b157974ae4f95cd8a22aa0accf6f86caa269c5914e9ac80e93eb9f2a383233c85a59033410bfd94bdd2f053cd8404"
)

build() {

  cd "$_zipname"

  python -m build -wn
}

check() {
  cd "$_zipname"

  PYTHONPATH=Lib pytest Lib/defcon/test
}

package() {

  cd "$_zipname"

  python -m installer -d "${pkgdir}" dist/*.whl

  install -Dm0644 -t "${pkgdir}/usr/share/licenses/${pkgname}/" License.txt
}

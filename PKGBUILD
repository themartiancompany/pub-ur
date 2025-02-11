# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$( \
  uname \
    -o)"
_offline="false"
_evmfs="true"
_git="false"
_proj="hip"
pkgname=pub
pkgver="0.0.0.0.0.0.0.0.0.0.0.0.1.1"
_commit="5a363e8195f654675a417d7080c1fda3deb41b68"
pkgrel=1
_pkgdesc=(
  "Ur reference publishing tool."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
group=(
 "${_proj}"
)
license=(
  'AGPL3'
)
depends=(
  "aspe"
  "fur"
  "git"
  "gnupg"
  "gpg-key-info"
  "lur"
  "libcrash-bash"
  "rsync"
  "ur-contracts"
)
optdepends=(
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  optdepends+=(
  )
fi
makedepends=(
  'make'
)
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
validpgpkeys=(
)
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b"
_evmfs_sum='6835202b2217a244c8660fc8d6fad12fd4800cd39bbfe9f112be5b5332f16182'
_evmfs_uri="evmfs://${_evmfs_network}/${_evmfs_ns}/${_evmfs_sum}"
_evmfs_src="${_tarname}.zip::${_evmfs_uri}"
_evmfs_sig_sum="67dbc17ea8c6304d50d4103f36e401e3c3cb0e2f47e319c0f680960c5afeae17"
_evmfs_sig_uri="evmfs://${_evmfs_network}/${_evmfs_ns}/${_evmfs_sig_sum}"
_evmfs_sig_src="${_tarname}.zip.sig::${_evmfs_uri}"
if [[ "${_evmfs}" == true ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_src}"
  _sum="${_evmfs_sum}"
  source+=(
    "${_evmfs_sig_src}"
  )
  sha256sums+=(
    "${_evmfs_sig_sum}"
  )
elif [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
  validpgpkeys+=(
    # Truocolo <truocolo@aol.com>
    '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
    # Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
    'F690CBC17BD1F53557290AF51FC17D540D0ADEED'
  )
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum='b245547bdcdbfeb09f400305a4b515b6d49635be90f560a39302761fc2688571'
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="${_evmfs_sum}"
  fi
fi
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et

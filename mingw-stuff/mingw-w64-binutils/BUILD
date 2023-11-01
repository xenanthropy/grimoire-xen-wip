local _targets
if [[ "${SMGL_COMPAT_ARCHS[1]}" == "x86_64" || "${SMGL_COMPAT_ARCHS[1]}" == "em64t" ]]; then
  _targets="i686-w64-mingw32 x86_64-w64-mingw32"
else
  _targets="i686-w64-mingw32"
fi &&

local _target
for _target in $_targets; do
  mkdir -p "${SOURCE_DIRECTORY}/binutils-${_target}" &&
  cd "${SOURCE_DIRECTORY}/binutils-${_target}" &&
  "${SOURCE_DIRECTORY}/configure" --prefix="${INSTALL_ROOT}/usr" \
     --target=${_target} \
     --program-prefix=${_target}- \
     --infodir="${INSTALL_ROOT}/usr/share/info/${_target}" \
     --enable-lto --enable-plugins \
     --enable-deterministic-archives \
     --disable-multilib --disable-nls \
     --disable-werror \
     --enable-ld=default \
     --disable-default-execstack \
     --disable-gprofng \
     --disable-internal-libiberty \
     --disable-shared \
     --with-mmap \
     --with-system-zlib
  make -O
done

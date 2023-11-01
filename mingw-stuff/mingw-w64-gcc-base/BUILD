local _targets
if [[ "${SMGL_COMPAT_ARCHS[1]}" == "x86_64" || "${SMGL_COMPAT_ARCHS[1]}" == "em64t" ]]; then
  _targets="i686-w64-mingw32 x86_64-w64-mingw32"
else
  _targets="i686-w64-mingw32"
fi &&

local _target
for _target in $_targets; do
  mkdir -p "${SOURCE_DIRECTORY}/gcc-${_target}" &&
  cd "${SOURCE_DIRECTORY}/gcc-${_target}" &&
  "${SOURCE_DIRECTORY}/configure" --prefix="${INSTALL_ROOT}/usr" \
    --program-prefix=$_target- \
    --target=$_target \
    --disable-dw2-exceptions \
    --disable-multilib \
    --disable-ns \
    --enable-checking=release \
    --enable-languages=c,lto \
    --enable-static \
    --enable-version-specific-runtime-libs \
    --with-bugurl="https://bugs.sourcemage.org" \
    --with-system-zlib &&
  make all-gcc
done

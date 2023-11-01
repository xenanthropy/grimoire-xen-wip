local _targets
if [[ "${SMGL_COMPAT_ARCHS[1]}" == "x86_64" || "${SMGL_COMPAT_ARCHS[1]}" == "em64t" ]]; then
  _targets="i686-w64-mingw32 x86_64-w64-mingw32"
else
  _targets="i686-w64-mingw32"
fi &&

local _target
for _target in $_targets; do
#  if [[ "${_target}" == "i686-w64-mingw32" ]]; then
#    CFLAGS=${CFLAGS/-m64/-m32}
#    CXXFLAGS=${CXXFLAGS/-m64/-m32}
#  else
#    CFLAGS=${CFLAGS/-m32/-m64}
#    CXXFLAGS=${CXXFLAGS/-m32/-m64}
#  fi &&

  mkdir -p "${SOURCE_DIRECTORY}/gcc-${_target}" &&
  cd "${SOURCE_DIRECTORY}/gcc-${_target}" &&
  "${SOURCE_DIRECTORY}/configure" --prefix="${INSTALL_ROOT}/usr" \
    --target=${_target} \
    --libexecdir="${INSTALL_ROOT}/usr/libexec" \
    --disable-dw2-exceptions \
    --disable-multilib \
    --disable-nls \
    --disable-sjlj-exceptions \
    --disable-werror \
    --enable-checking=release \
    --enable-cloog-backend=isl \
    --enable-fully-dynamic-string \
    --enable-languages=c,lto,c++ \
    --enable-libgomp \
    --enable-libstdcxx-time=yes \
    --enable-lto \
    --enable-threads=posix \
    --enable-static \
    --enable-shared \
    --enable-version-specific-runtime-libs \
    --with-bugurl="https://bugs.sourcemage.org" \
    --with-system-zlib &&
  make
done

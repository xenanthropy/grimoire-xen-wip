local _targets
if [[ "${SMGL_COMPAT_ARCHS[1]}" == "x86_64" || "${SMGL_COMPAT_ARCHS[1]}" == "em64t" ]]; then
  _targets="i686-w64-mingw32 x86_64-w64-mingw32"
else
  _targets="i686-w64-mingw32"
fi &&

local _target
for _target in ${_targets}; do
  if [[ "$_target" == "i686-w64-mingw32" ]]; then
    CFLAGS=${CFLAGS/-m64/-m32}
  else
    CFLAGS=${CFLAGS/-m32/-m64}
  fi &&
  mkdir -p "${SOURCE_DIRECTORY}/winpthreads-build-${_target}" &&
  cd "${SOURCE_DIRECTORY}/winpthreads-build-${_target}" &&
  "${SOURCE_DIRECTORY}/mingw-w64-libraries/winpthreads/configure" \
      --prefix="${INSTALL_ROOT}/usr/${_target}" --host=${_target} \
      --enable-static --enable-shared CC=${_target}-gcc &&
  make
done

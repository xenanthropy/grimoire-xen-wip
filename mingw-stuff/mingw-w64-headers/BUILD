local _targets
if [[ "${SMGL_COMPAT_ARCHS[1]}" == "x86_64" || "${SMGL_COMPAT_ARCHS[1]}" == "em64t" ]]; then
  _targets="i686-w64-mingw32 x86_64-w64-mingw32"
else
  _targets="i686-w64-mingw32"
fi &&

for _target in ${_targets}; do
  mkdir -p "${SOURCE_DIRECTORY}/headers-${_target}" &&
  cd "${SOURCE_DIRECTORY}/headers-${_target}" &&
  "${SOURCE_DIRECTORY}/mingw-w64-headers/configure" \
   --prefix="${INSTALL_ROOT}/usr/${_target}" --enable-sdk=all --host=${_target}
done

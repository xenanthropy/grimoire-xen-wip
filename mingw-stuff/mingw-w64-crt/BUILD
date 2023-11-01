local _targets
if [[ "${SMGL_COMPAT_ARCHS[1]}" == "x86_64" || "${SMGL_COMPAT_ARCHS[1]}" == "em64t" ]]; then
  _targets="i686-w64-mingw32 x86_64-w64-mingw32"
else
  _targets="i686-w64-mingw32"
fi &&

local _target
for _target in ${_targets}; do
    local _crt_configure_args
    if [[ ${_target} == "i686-w64-mingw32" ]]; then
        _crt_configure_args="--disable-lib64 --enable-lib32"
        CFLAGS=${CFLAGS/-m64/-m32}
    elif [[ ${_target} == "x86_64-w64-mingw32" ]]; then
        _crt_configure_args="--disable-lib32 --enable-lib64"
        CFLAGS=${CFLAGS/-m32/-m64}
    fi &&
    mkdir -p "${SOURCE_DIRECTORY}/crt-${_target}" &&
    cd "${SOURCE_DIRECTORY}/crt-${_target}" &&
    "${SOURCE_DIRECTORY}/mingw-w64-crt/configure" \
        --prefix="${INSTALL_ROOT}/usr/${_target}" \
        --host=${_target} --enable-wildcard \
        --target=${_target} \
        ${_crt_configure_args} \
        CC=${_target}-gcc &&
    make
done

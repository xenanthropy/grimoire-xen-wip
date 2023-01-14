cd $SOURCE_DIRECTORY &&
cp ./js/src/configure.in ./js/src/configure &&
chmod +x ./js/src/configure &&
mkdir -p builddir &&
cd builddir &&

disable_stack_clash_protection &&

# do aout-of-tree build
OPTS+=" --enable-linker=gold --disable-tests --enable-strip --disable-jemalloc" &&
$SOURCE_DIRECTORY/js/src/configure --prefix=${INSTALL_ROOT}/usr $OPTS &&
make

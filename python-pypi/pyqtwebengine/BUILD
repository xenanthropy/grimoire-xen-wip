cd "${SOURCE_DIRECTORY}" &&
QMAKEPATH="QT5DIR/bin"   &&
#python3 ./configure.py -j $MAKE_NJOBS --qmake=$QT5DIR/bin/qmake $OPTS &&
#make
sip-build --verbose --build-dir="${SOURCE_DIRECTORY}" --qmake=$QT5DIR/bin/qmake &&
make

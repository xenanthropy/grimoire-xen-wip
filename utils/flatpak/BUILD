if [[ "${FLATPAK_BRANCH}" == "pre-release" ]]; then
OPTS+=" tests=false" &&
default_build
else
autoreconf -f -i &&
default_build
fi

OPTS+=" battery_detection=$BATTERY charset_detection=$CHAR generic_media_extractor=$EXTRACT" &&

if [[ $EXTRACT == "gstreamer" ]]; then
  OPTS+=" gstreamer_backend=$BACKEND"
fi &&

OPTS="miner_rss=false functional_tests=false extract=true $OPTS" &&
meson_build

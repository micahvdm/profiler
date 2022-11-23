# profiler

sudo apt install -y libxcb1-dev libxcb-util-dev libxcb-icccm4-dev libcairo2-dev libpixman-1-dev libfontconfig1-dev libfreetype6-dev libpng-dev libxcb-shm0-dev libxcb-render0-dev libxrender-dev libx11-dev libxext-dev zlib1g-dev libbsd-dev libexpat1-dev libfftw3-dev libboost-all-dev lv2-dev ladspa-sdk libzita-resampler-dev libzita-convolver-dev faust meson

Run meson build and then ninja -C build in the source directory.
Run ninja -C build
Run meson build --reconfigure -Dlv2dir=.lv2 --prefix $HOME and then ninja -C build install.

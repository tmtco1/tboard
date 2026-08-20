# tboard

**tboard** is an independent keyboard application currently under development.

tboard is based on [eta-keyboard](https://github.com/pardus/eta-keyboard), with the goal of providing an independently developed and extended virtual keyboard experience.
>

> [!IMPORTANT]
> tboard is currently under development and is not ready for use yet.

### Build

1. Clone the project
```bash
git clone https://github.com/tmtco1/tboard
```

2. Install build dependencies
```bash
sudo apt install build-essential libc6 libgcc1 libgl1-mesa-glx libgl1 \
    libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5qml5 \
    libqt5quick5 libqt5svg5-dev libqt5widgets5 libqt5x11extras5-dev \
    libstdc++6 libx11-6 libx11-xcb-dev libxcb-xkb-dev libxcb1-dev \
    libxkbcommon-x11-0 libxkbcommon-x11-dev libxkbcommon0 libxkbcommon-dev \
    libxkbfile-dev libxtst-dev qtdeclarative5-dev
```

3. Build
```bash
cd tboard
mkdir build
cd build
qmake ../
make
```

4. Install Runtime dependencies
```bash
sudo apt install libqt5svg5 qml-module-qtquick-controls \
    qml-module-qtquick-window2 qml-module-qtquick2
```

### Usage

Run the keyboard:
```bash
./tboard show
```

### Debian Packaging

```bash
cd tboard
sudo apt install build-essential debmake debhelper git-buildpackage
sudo mk-build-deps -ir
gbp buildpackage --git-export-dir=/tmp/build-area -b -us -uc
cd /tmp/build-area
```
Test remote calling:
```bash
sudo apt install qdbus-qt5
qdbus org.tmtco.virtualkeyboard /VirtualKeyboard org.tmtco.virtualkeyboard.toggle
```
### Make Pardus Greeter Use tboard

The Pardus Greeter uses eta-keyboard by default. To change this behavior and make it start tboard instead:

```bash
sudo sed -i 's/eta-keyboard show/tboard show/' /etc/pardus/greeter.conf.d/00-etap.conf
```


## License

tboard contains code derived from **Pardus eta-keyboard**.

The applicable portions of the project are licensed under the **GNU Lesser General Public License v3.0**.

See [`LICENSE`](LICENSE) for the full license text.

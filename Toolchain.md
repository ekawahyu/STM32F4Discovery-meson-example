# Toolchain Installation (Ubuntu and derviates)

First you have to install the `arm-none-eabi-gcc` toolchain.
On Ubuntu :

      sudo apt-get install binutils-arm-none-eabi gcc-arm-none-eabi gdb-arm-none-eabi  libnewlib-arm-none-eabi libnewlib-arm-none-eabi

## LLVM

Also we want to install llvm:

      wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key|sudo apt-key add -
      sudo add-apt-repository -y 'deb http://apt.llvm.org/xenial/ llvm-toolchain-xenial main'
      sudo add-apt-repository -y 'deb-src http://apt.llvm.org/xenial/ llvm-toolchain-xenial main'

      sudo apt-get update
      sudo apt-get -y install clang llvm lld

## Python3 / Meson / Ninja

And of course meson-build

      sudo apt-get -y install python3 python3-pip python3-setuptools ninja-build
      sudo pip3 install --upgrade pip
      sudo pip3 install meson

## git

      sudo apt-get -y install git

## openocd

      sudo apt-get install openocd

You maybe have to add the so called udev rules.
(They should get installed with the openocd package).
After updateing the udev rules use this command to reload the new configs

      sudo udevadm control --reload-rules

### newer version
Maybe you need a newer version of openocd.

You have to go to the openocd website [http://openocd.org/](http://openocd.org/)
and download the current version.

As an example I took version 0.10

    cd ~
    wget https://sourceforge.net/projects/openocd/files/openocd/0.10.0/openocd-0.10.0.zip/download
    unzip download -d ~/openocd
    rm download
    cd openocd/openocd-0.10.0
    ./configure
    make
    sudo make install

this installs version 0.10 besides your current openocd installation.
you have to call `/usr/local/bin/openocd` instead of just `openocd` to use the newer version

# Toolchain Installation (macOS with brew)

Before installing packages with brew, you may want to install Python 3.x with Miniconda. Detail instruction can be found from [here](https://docs.conda.io/en/latest/miniconda.html)

    brew install gcc-arm-embedded
    brew install llvm
    brew install openocd
    brew install meson
    brew install ninja

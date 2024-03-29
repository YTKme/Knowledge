# Python Install

## Prerequisite

```bash
# Install cURL
sudo apt install curl
```

```bash
# Install Wget
sudo apt install wget
```

```bash
# Install OpenSSL
sudo apt install openssl
```

```bash
# Install Clang
sudo apt install clang
```

```bash
# Instal LLVM
sudo apt install llvm
```
* For `--with-lto` flag, mainly used for Clang and ARM?

```bash
sudo apt-get install build-essential gdb lcov pkg-config \
    libbz2-dev libffi-dev libgdbm-dev libgdbm-compat-dev liblzma-dev \
    libncurses5-dev libreadline6-dev libsqlite3-dev libssl-dev \
    lzma lzma-dev tk-dev uuid-dev zlib1g-dev
```

## Configure

### Linux

```bash
./configure \
    --prefix=/opt/python/3.11/ \
    --enable-shared \
    --enable-optimizations \
    --with-lto=full \
    --with-ensurepip=install \
    LDFLAGS=-Wl,-rpath=/opt/python/3.11/lib/

# ./configure \
#     --prefix=/opt/python/3.11/ \
#     --enable-shared \
#     --enable-optimizations \
#     --with-lto=full \
#     --enable-pystats \
#     --enable-profiling \
#     --with-ensurepip=install \
#     LDFLAGS=-Wl,-rpath=/opt/python/3.11/lib/
```

### macOS ARM64

#### Python 3.11
```bash
GDBM_CFLAGS="-I$(brew --prefix gdbm)/include" \
GDBM_LIBS="-L$(brew --prefix gdbm)/lib -lgdbm" \
./configure \
    --prefix=/opt/python/3.11.5/ \
    --enable-shared \
    --enable-optimizations \
    --with-lto \
    --with-ensurepip=install \
    --with-openssl="$(brew --prefix openssl@3)"
```

#### Python 3.8 through 3.10
```bash
CFLAGS="-I$(brew --prefix gdbm)/include -I$(brew --prefix xz)/include" \
LDFLAGS="-L$(brew --prefix gdbm)/lib -I$(brew --prefix xz)/lib" \
PKG_CONFIG_PATH="$(brew --prefix tcl-tk)/lib/pkgconfig" \
./configure \
    --prefix=/opt/python/3.11.3/ \
    --enable-shared \
    --enable-optimizations \
    --with-ensurepip=install \
    --with-openssl="$(brew --prefix openssl@1.1)" \
    --with-tcltk-libs="$(pkg-config --libs tcl tk)" \
    --with-tcltk-includes="$(pkg-config --cflags tcl tk)"
```

#### Old
```bash
CFLAGS="-I$(brew --prefix gdbm)/include -I$(brew --prefix xz)/include" \
LDFLAGS="-L$(brew --prefix gdbm)/lib -I$(brew --prefix xz)/lib" \
PKG_CONFIG_PATH="$(brew --prefix tcl-tk)/lib/pkgconfig" \
./configure \
    --prefix=/opt/python/3.11.3/ \
    --enable-shared \
    --enable-optimizations \
    --with-ensurepip=install \
    --with-openssl="$(brew --prefix openssl@1.1)" \
    --with-pydebug # Optional

# Universal (Work in Progress)
# CFLAGS="-I$(brew --prefix gdbm)/include -I$(brew --prefix xz)/include" \
# LDFLAGS="-L$(brew --prefix gdbm)/lib -I$(brew --prefix xz)/lib" \
# PKG_CONFIG_PATH="$(brew --prefix tcl-tk)/lib/pkgconfig" \
# ./configure \
#     --prefix=/opt/python/3.11.3/ \
#     --enable-shared \
#     --enable-optimizations \
#     --with-ensurepip=install \
#     --with-pydebug \
#     --enable-universalsdk --with-universal-archs=universal2 \
#     --with-openssl="$(brew --prefix openssl@1.1)"
#     --with-openssl-rpath=auto
```

## Build

### Linux

```bash
make -j "$(nproc)"
#sudo make -j "$(nproc)"
```

```bash
#
sudo make altinstall
```

```bash
#
sudo make install
```

### macOS ARM64

```bash
arch -arm64 make -j"$(sysctl -n hw.logicalcpu)"
```

```bash
arch -arm64 make altinstall
```

```bash
arch -arm64 make install
```

## Reference
* [Setup and Building](https://devguide.python.org/getting-started/setup-building/)
* [Python 3 Installation & Setup Guide](https://realpython.com/installing-python/)
    * [How to Build Python From Source Code](https://realpython.com/installing-python/#how-to-build-python-from-source-code)
* [Configure Python](https://docs.python.org/dev/using/configure.html)
* [Build, Compile and Install Python from Source Code](https://www.build-python-from-source.com/)
* [How to Build Python from Source](https://www.devdungeon.com/content/how-build-python-source)
* [Posit - Install Python From Source](https://docs.posit.co/resources/install-python-source/)

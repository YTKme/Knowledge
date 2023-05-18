# Python Install

```python
# Install cURL
sudo apt install curl
```

```python
# Install Wget
sudo apt install wget
```

```python
# Install OpenSSL
sudo apt install openssl
```

```python
# Install Clang
sudo apt install clang
```

```python
# Instal LLVM
sudo apt install llvm
```
* For `--with-lto` flag, mainly used for Clang and ARM?

```python
sudo apt-get install build-essential gdb lcov pkg-config \
    libbz2-dev libffi-dev libgdbm-dev libgdbm-compat-dev liblzma-dev \
    libncurses5-dev libreadline6-dev libsqlite3-dev libssl-dev \
    lzma lzma-dev tk-dev uuid-dev zlib1g-dev
```

```python
wget https://www.python.org/ftp/python/3.11.3/Python-3.11.3.tgz
```

```python
tar xvf Python-3.11.3.tgz
cd Python-3.11.3
```

```python
./configure \
    --prefix=/opt/python/3.11.3/ \
    --enable-shared \
    --enable-optimizations \
    --with-lto=full \
    --with-ensurepip=install \
    LDFLAGS=-Wl,-rpath=/opt/python/3.11.3/lib/

# ./configure \
#     --prefix=/opt/python/3.11.3/ \
#     --enable-shared \
#     --enable-optimizations \
#     --with-lto=full \
#     --enable-pystats \
#     --enable-profiling \
#     --with-ensurepip=install \
#     LDFLAGS=-Wl,-rpath=/opt/python/3.11.3/lib/
```

```python
make -j "$(nproc)"
#sudo make -j "$(nproc)"
```

```python
sudo make altinstall
```

## Reference
* [Setup and Building](https://devguide.python.org/getting-started/setup-building/)
* [Python 3 Installation & Setup Guide](https://realpython.com/installing-python/)
    * [How to Build Python From Source Code](https://realpython.com/installing-python/#how-to-build-python-from-source-code)
* [Configure Python](https://docs.python.org/dev/using/configure.html)
* [Build, Compile and Install Python from Source Code](https://www.build-python-from-source.com/)
* [How to Build Python from Source](https://www.devdungeon.com/content/how-build-python-source)
* [Posit - Install Python From Source](https://docs.posit.co/resources/install-python-source/)

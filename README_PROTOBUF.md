# Install protobuf version 3.20.1 and make default

```bash
sudo apt-get install autoconf automake libtool git libz-dev
git clone https://github.com/protocolbuffers/protobuf.git
cd protobuf
git checkout v3.20.1
git submodule update --init --recursive
./autogen.sh
./configure CFLAGS="-fPIC" CXXFLAGS="-fPIC" LDFLAGS="-latomic" --prefix=/usr/local
make -j$(npeoc) && make check
make install
ldconfig
```
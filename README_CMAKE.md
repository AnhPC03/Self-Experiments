# Install cmake version 3.23.1 and make default

```bash
sudo apt-get install build-essential libssl-dev wget
wget https://github.com/Kitware/CMake/releases/download/v3.23.1/cmake-3.23.1.tar.gz
tar -xzf cmake-3.23.1.tar.gz
cd cmake-3.23.1
sudo apt install make
./configure
make -j$(nproc) && make install
```

Check again with command (the output should be version 3.23.1)
```bash
cmake --version
```
# Install opencv make default

## Install dependencies
```bash
sudo apt install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev \
    python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev python3-pip python3-numpy
```

## Install
1. Clone the repository
```bash
VERSION=4.5.5
git clone https://github.com/opencv/opencv.git -b $VERSION --depth 1
```

2. If you'd like to install the extra modules please clone the following project.
```bash
VERSION=4.5.5
git clone https://github.com/opencv/opencv_contrib.git -b $VERSION --depth 1
```

3. Configure the project
```bash
cd opencv
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D BUILD_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D INSTALL_C_EXAMPLES=OFF \
-D PYTHON_EXECUTABLE=$(which python2) \
-D BUILD_opencv_python2=OFF \
-D PYTHON3_EXECUTABLE=$(which python3) \
-D PYTHON3_INCLUDE_DIR=$(python3 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
-D PYTHON3_PACKAGES_PATH=$(python3 -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())") \
 ..
 ```

 4. If you decide to also build the contrib extra modules, append the following configuration before `..` notation:
 ```bash
 -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules/ \
 ```
- **Note**: make sure `opencv_contrib` folder is the same folder with `opencv` folder<br><br>
5. Append the following configuration if build on armv7l chip for running faster
 ```bash
 -D ENABLE_NEON=ON \
-D ENABLE_VFPV3=ON \
```
6. Build the project
```bash
make -j$(nproc)
```
7. Install the project
```bash
sudo make install
sudo ldconfig
```
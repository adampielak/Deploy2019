check: https://www.learnopencv.com/install-opencv3-on-ubuntu/

ffmpeg -version
if not installed: sudo apt install ffmpeg

sudo apt-get update
sudo apt-get -y remove x264 libx264-dev
sudo apt-get -y install build-essential checkinstall cmake pkg-config yasm gfortran git
sudo apt-get -y install libjpeg8-dev libpng12-dev

sudo apt-get install -y libboost-dev ocl-icd-libopencl1 mesa-common-dev libglu1-mesa-dev
sudo apt-get install -y git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install -y python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev  libdc1394-22-dev 
sudo apt-get install -y x264 v4l-utils
sudo apt-get install -y libopencore-amrnb-dev libopencore-amrwb-dev
sudo apt-get install -y libvorbis-dev libxvidcore-dev
sudo apt-get install -y libatlas-base-dev
sudo apt-get install -y libprotobuf-dev protobuf-compiler
sudo apt-get install -y libatk-adaptor

for libjasper-dev:

echo "deb http://us.archive.ubuntu.com/ubuntu/ yakkety universe" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install -y libjasper-dev

compile CMake now.

download stable open cv 3.3: 
wget --content-disposition https://github.com/opencv/opencv/archive/3.3.0.tar.gz
wget --content-disposition https://github.com/opencv/opencv_contrib/archive/3.3.0.zip

untar:
tar -xvf opencv-3.3.0.tar.gz
unzip opencv_contrib-3.3.0.zip

remove dnn_modern folder due to protobuf issues /home/tudi/Downloads/opencv_contrib-3.3.0/modules/dnn_modern
rm -rf ./opencv_contrib-3.3.0/modules/dnn_modern

cd ~
mkdir opencvbuild
cd opencvbuild

with contributions:
cmake -D OPENCV_EXTRA_MODULES_PATH=/home/tudi/Downloads/opencv_contrib-3.3.0/modules /home/tudi/Downloads/opencv-3.3.0
cmake -D CMAKE_BUILD_TYPE=RELEASE -D OPENCV_EXTRA_MODULES_PATH=/home/tudi/opencv_contrib-3.3.0/modules /home/tudi/opencv-3.3.0

if succesfull: configuration done message

make -j4 # runs several jobs in parallel
sudo make install

http://download.qt.io/official_releases/online_installers/qt-unified-linux-x64-online.run

add configuration:
sudo touch /etc/ld.so.conf.d/opencv.conf
sudo vi /etc/ld.so.conf.d/opencv.conf

add:  /usr/local/lib  or what is needed based on cat install_manifest | grep highgui or other error

reload config:  sudo ldconfig

run:
https://help.ubuntu.com/community/OpenCV

download image:
wget --content-disposition http://qube.pentaclethevbs.com/ext/install/splash.png

#include <opencv2/highgui/highgui.hpp>
using namespace cv;

int main()
{

    Mat img = imread("/home/tudi/Downloads/splash.png",CV_LOAD_IMAGE_COLOR);
    imshow("opencvtest",img);
    waitKey(0);

    return 0;
}

g++ -ggdb `pkg-config --cflags opencv` -o `basename test.cpp .cpp` test.cpp `pkg-config --libs opencv`
g++ -ggdb `pkg-config --cflags opencv` -o `basename version.cpp .cpp` version.cpp `pkg-config --libs opencv`
g++ -ggdb `pkg-config --cflags opencv` -o `basename main.cpp .cpp` main.cpp `pkg-config --libs opencv`

g++ vehicle_detection.cpp -o main $(pkg-config --cflags --libs opencv)


get opencv info:   printf("OpenCV: %s", cv::getBuildInformation().c_str());

see:  https://help.ubuntu.com/community/OpenCV

use in codelite linker: `pkg-config --cflags --libs opencv` 

gcc -v or gcc --version
cmake --version

try to fix broken packages: sudo apt-get -f install, by default libraries are installed in /usr/lib and header files will be in /usr/include
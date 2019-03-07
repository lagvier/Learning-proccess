### Pre-requisites
#### Install developer tools:
``` sudo apt-get install build-essential cmake unzip pkg-config```
#### Install image processing tools
``` sudo apt-get install libjpeg-dev libpng-dev libtiff-dev```
#### Video packages
``` sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev```
``` sudo apt-get install libxvidcore-dev libx264-dev```
#### GTK
``` sudo apt-get install libgtk-3-dev```
#### OpenCV optimizing tools
``` sudo apt-get install libatlas-base-dev gfortran```
#### Install OpenCV
```sudo apt-get install python3-dev```
#### Install OpenCV official
``` 
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/3.4.4.zip
wget -O opencv.zip https://github.com/opencv/opencv/archive/3.4.4.zip
unzip opencv.zip
unzip opencv_contrib.zip
mv opencv-3.4.4 opencv
mv opencv_contrib-3.4.4 opencv_contrib
```
#### Configure your Python 3 environment
```
wget https://bootstrap.pypa.io/get-pip.py
sudo python3 get-pip.py
sudo pip install virtualenv virtualenvwrapper
sudo rm -rf ~/get-pip.py ~/.cache/pip
```
Add the following lines to ~/.bashrc the run ```source ~/.bashrc```
```
    # virtualenv and virtualenvwrapper
    export WORKON_HOME=$HOME/.virtualenvs
    export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
    source /usr/local/bin/virtualenvwrapper.sh
```
Experiment by creating a virtual environment, call it cv and try to access it 
```
mkvirtualenv cv -p python3
workon cv
```

#### Configure OpenCV with CMake
```
cd ~/opencv
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D INSTALL_C_EXAMPLES=OFF \
    -D OPENCV_ENABLE_NONFREE=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
    -D PYTHON_EXECUTABLE=~/.virtualenvs/cv/bin/python \
    -D BUILD_EXAMPLES=ON ..
```

#### Installing and verifying OpenCV
```
sudo make install
sudo ldconfig
pkg-config --modversion opencv
ls /usr/local/python/cv2/python-3.6
cd /usr/local/python/cv2/python-3.6
cd ~/.virtualenvs/cv/lib/python3.6/site-packages/
ln -s /usr/local/python/cv2/python-3.6/cv2.so cv2.so
```
#### Test OpenCV installation
```
cd ~
workon cv
python
```

If everything works well you can then safely delete the opencv folders from your home directory
```
cd ~
rm opencv.zip opencv_contrib.zip
rm -rf opencv opencv_contrib
```

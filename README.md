# openalpr

**Warning: this repository has been reverted back to March 2015, one month before OpenALPR went commercial and the code quality began to deteriorate.**

OpenALPR is an open source *Automatic License Plate Recognition* library written in C++ with bindings in C#, Java, and Python.  The library analyzes images and identifies license plates.  The output is the text representation of any license plate characters found in the image.

## User Guide

OpenALPR includes a command line utility.  Simply typing "alpr [image file path]" is enough to get started recognizing license plate images.

```sh
user@linux:~/openalpr$ alpr ./samplecar.png

plate0: top 10 results -- Processing Time = 58.1879ms.
    - PE3R2X     confidence: 88.9371
    - PE32X      confidence: 78.1385
    - PE3R2      confidence: 77.5444
    - PE3R2Y     confidence: 76.1448
    - P63R2X     confidence: 72.9016
    - FE3R2X     confidence: 72.1147
    - PE32       confidence: 66.7458
    - PE32Y      confidence: 65.3462
    - P632X      confidence: 62.1031
    - P63R2      confidence: 61.5089

```

## Compiling (Linux)

```sh
sudo apt-get install libopencv-dev libtesseract-dev git cmake build-essential libleptonica-dev liblog4cplus-dev libcurl3-dev
# If using the daemon, install beanstalkd
sudo apt-get install beanstalkd
git clone git@github.com:stanislawowski/openalpr.git
mkdir -p openalpr/src/build
cd openalpr/src/build
cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -DCMAKE_INSTALL_SYSCONFDIR:PATH=/etc ..
make
sudo make install
```

## Docker

```sh
docker build -t openalpr https://github.com/openalpr/openalpr.git
wget http://plates.openalpr.com/h786poj.jpg
docker run -it --rm -v $(pwd):/data:ro openalpr -c eu h786poj.jpg
```

## License

Affero GPLv3
http://www.gnu.org/licenses/agpl-3.0.html

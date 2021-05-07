openalpr
========

**Warning: this repository has been reverted back to March 2015, one month before OpenALPR went commercial and the code quality began to deteriorate**

OpenALPR is an open source *Automatic License Plate Recognition* library written in C++ with bindings in C#, Java, and Python.  The library analyzes images and identifies license plates.  The output is the text representation of any license plate characters found in the image.

User Guide
-----------


OpenALPR includes a command line utility.  Simply typing "alpr [image file path]" is enough to get started recognizing license plate images.

```
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

Compiling
-----------

OpenALPR compiles and runs on Linux, Mac OSX and Windows.

OpenALPR requires the following additional libraries:

    - Tesseract OCR v3.0.3 (https://code.google.com/p/tesseract-ocr/)
    - OpenCV v2.4.8+ (http://opencv.org/)

After cloning this GitHub repository, you should download and extract Tesseract and OpenCV source code into their own directories.  Compile both libraries.

Please follow these detailed compilation guides for your respective operating system:

* [Windows] (https://github.com/openalpr/openalpr/wiki/Compilation-instructions-(Windows))
* [Ubuntu Linux] (https://github.com/openalpr/openalpr/wiki/Compilation-instructions-(Ubuntu-Linux))
* [Android] (https://github.com/sujaybhowmick/OpenAlprDroidApp)
* [iOS] (https://github.com/twelve17/openalpr-ios)

If all went well, there should be an executable named *alpr* along with *libopenalpr-static.a* and *libopenalpr.so* that can be linked into your project.


Docker
------

``` shell
docker build -t openalpr https://github.com/openalpr/openalpr.git
wget http://plates.openalpr.com/h786poj.jpg
docker run -it --rm -v $(pwd):/data:ro openalpr -c eu h786poj.jpg
```

License
-------

Affero GPLv3
http://www.gnu.org/licenses/agpl-3.0.html

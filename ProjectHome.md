Gabor Feature Extraction for Face Recognition, Face Annotation and Image Retrieval.

For technical details of the "Gabor Wavelets Transform for Face Recognition", please refer
to the following publications,

1. C. Liu and H. Wechsler: "Gabor Feature Based Classification Using the Enhanced Fisher Linear Discriminant Model for Face Recognition", IEEE Trans. Image Processing, vol. 11, no. 4, pp. 467-476, 2002.

2. Jianke Zhu, Mang I Vai and Peng Un Mak, "A New Enhanced Nearest Feature Space (ENFS)  Classifier for Gabor Wavelets Features-Based Face Recognition", ICBA 2004. Lecture Notes in Computer Science 3072, Springer. pp. 124 - 131.

Install Guide for windows  (Linux and Mac with Matlab Mex version coming soon)

A. Setup OpenCV
1. Install the OpenCV library (Download opencv from http://sourceforge.net/projects/opencvlibrary,  this release support OpenCV ver >=3.2)
2. Add <OpenCV install dir>\lib into MSVC library search path, and <OpenCV install dir>\cxcore\include,  <OpenCV install dir>\cv\include, <OpenCV install dir>\otherlib\highgui into MSVC include search path,  add <OpenCV install dir>\bin into the system path of windows.
B. Open the prject file of MSVC7.1 directly, and build the project.

C. For MSVC 6.0, create a new project
3. Setup a new empty VC++ console project
4. Add the attached gabor\_extract.cpp into the project
5. Add cv.lib cxcore.lib highgui.lib (debug version cvd.lib cxcored.lib highguid.lib) into the additional library dependency of link tab
6. Build the project.

Install Guide for Linux
Currently implementation definitely support linux platform, the compatibility of current is not tested yet.

Usage of the library
1. Generate the fft of gabor filter bank, only need build once.
> gabor\_extract b

2. Extract the feature vector
> gabor\_extract e image\_file\_name output\_file\_name
> > e.g. gabor\_extract e 1.tiff 1.data

How to load the extracted feature vector
1. C/C++

> Open the extracted data in binary, then use this function go load the data into a double array
> double**getData(FILE** fh, int &length)
2. Matlab
> Using the provided "readbin.m" to load the binary format file.
> e.g. A = readbin('1.data');

Description of the generated files in folder "gabor".
Cgabor\_a\_b.bmp/Cgabor\_a\_b.data           cos part of the scale a orientation b gabor filter normalized image and data
Sgabor\_a\_b.bmp/Sgabor\_a\_b.data           sin part of the scale a orientation b gabor filter normalized image and data
FFTgabor\_a\_b.data                        Precomputed FFT of the gabor filter bank scale a  orientation b


Known Issues
1. Batch processing
Since about 40MB filter bank will be loaded every time, which will be very time consuming and inefficient.
You'd better add the batch processing code between the LoadGaborFFT() and UnloadGaborFFT() gabor data .

Bug reports are welcome!
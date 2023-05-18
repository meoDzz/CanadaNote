# Install OpenCV for Visual studio Window Application 
## Step 1: Download and Extract openCV
```
https://opencv.org/releases/page/2/
```
## Step 2: Add lib to Visual studio
### 1. Additional include Directories
Add the include directories
> D:\opencv\opencv\build\include;
### 2. Linker -> General
Add  ** additional library directories **
> D:\opencv\opencv\build\x64\vc14\lib;%(AdditionalLibraryDirectories)
### 3. Liner -> Input
Add the name of **lib** to **Additional Dependencies**
> opencv_world420.lib;opencv_world420d.lib;%(AdditionalDependencies)

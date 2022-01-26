# MulleObjCCLionDemo

🦁 An example CLion mulle-objc project 


## 0.20

For this to work you need to repackage all the Objective-c libraries as well as mulle-sprintf of [Foundation](//github.com/MulleFoundation/Foundation) into 
**FoundationWrap**. Place the `Foundation-startup`, `mulle-atinit`, `mulle-atexit` libraries into **FoundationWrap-startup**. Combine all the remaining
C files into a **c-wrap** library.


## 0.21 (Future as of 1.2022)

Use [FoundationWrap](//github.com/MulleFoundation/FoundationWrap) to create a directory `usr` in your project with 
all the required headers and libraries.


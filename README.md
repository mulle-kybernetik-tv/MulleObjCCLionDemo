# MulleObjCCLionDemo

🦁 An example CLion mulle-objc project 


## mulle-objc version 0.20

For this to work you need to repackage all the Objective-c libraries as well as mulle-sprintf of [Foundation](//github.com/MulleFoundation/Foundation) into 
**FoundationWrap**. Place the `Foundation-startup`, `mulle-atinit`, `mulle-atexit` libraries into **FoundationWrap-startup**. Combine all the remaining
C files into a **c-wrap** library. Create a directory `usr/include` and copy all the headers recursively there. Create a directory `usr/lib` and copy the three
libraries there.


## mulle-objc version 0.21 (Future as of 1.2022) and beyond

Use [FoundationWrap](//github.com/MulleFoundation/FoundationWrap) to create a directory `usr` in your project with 
all the required headers and libraries.


# MulleObjCCLionDemo

🦁 An example CLion mulle-objc project 

## CLion Configuration Step

Use [CLion-settings](https://github.com/mulle-kybernetik-tv/CLion-settings) to setup CLion.
Or if you want to do it manually, configure your toolchain so that **mulle-clang** is the C compiler and **mulle-gdb** is the debugger.
Also [enable Objective-C support](//www.jetbrains.com/help/clion/objective-c-c-support.html) in CLion.

## Generate new CLion project

On GitHub [generate](https://github.com/mulle-kybernetik-tv/MulleObjCCLionDemo/generate) your own project with MulleObjCClionDemo as the template. Here we are using "myproject" as the new name.

In [CLion](//www.jetbrains.com/clion/) in the welcome screen choose "Get from VCS" then enter the URL of your new project:

![Welcome Screen](https://user-images.githubusercontent.com/38703833/151197505-1bae347b-773d-45b2-bcf2-747827c422b5.png)

You should now have the project local and opened in CLion.

To get things to compile you need the [Foundation](//github.com/MulleFoundation/Foundation) repackaged in a special format and placed
into a folder `usr` in your project directory.

## mulle-objc version 0.20

For this to work you need to repackage all the Objective-c libraries as well as mulle-sprintf of [Foundation](//github.com/MulleFoundation/Foundation) into 
**FoundationWrap**. Place the `Foundation-startup`, `mulle-atinit`, `mulle-atexit` libraries into **FoundationWrap-startup**. Combine all the remaining
C files into a **c-wrap** library. Create a directory `usr/include` and copy all the headers recursively there. Create a directory `usr/lib` and copy the three
libraries there.


## mulle-objc version 0.21 (Future as of 1.2022) and beyond

Use [FoundationWrap](//github.com/MulleFoundation/FoundationWrap) to create a directory `usr` in your project with 
all the required headers and libraries.

Assuming your project is called "myproject" and has been placed into `~/CLionProjects`.

```
cd /tmp
mulle-fetch https://github.com/MulleFoundation/FoundationWrap
cd FoundationWrap
mulle-sde craft
mulle-make install . ~/CLionProjects/myproject/usr
```

# MulleObjCCLionDemo

🦁 An example CLion mulle-objc project 

This example project is also useful as a template for new CLion projects. Follow these three steps to generate a new
mulle-objc project based on the "Foundation".

## 1. Generate new CLion project on GitHub

On GitHub [generate](https://github.com/mulle-kybernetik-tv/MulleObjCCLionDemo/generate) your own project with MulleObjCClionDemo as the template. Here we are using "myproject" as the new name.

In [CLion](//www.jetbrains.com/clion/) in the welcome screen choose "Get from VCS" then enter the URL of your new project:

![Welcome Screen](https://user-images.githubusercontent.com/38703833/151197505-1bae347b-773d-45b2-bcf2-747827c422b5.png)

You should now have the project local and opened in CLion. In a fresh installation you can now configure the **mulle-clang** compiler.

![configure](https://user-images.githubusercontent.com/38703833/151203695-9ead8c7b-c56c-4a6a-904d-005f81c06b8d.png)

If this doesn't show up, check "File / Settings / Build Execution Deployment / ToolChains", which is the same dialog basically.

![ToolChains](https://user-images.githubusercontent.com/38703833/151203967-9f5ce77d-4fa2-4803-9804-a4700d8a6a25.png)

## 2. Get mulle-objc Foundation libraries

To get things to compile you need the [Foundation](//github.com/MulleFoundation/Foundation) repackaged in a special format and placed
into a folder `usr` in your project directory. Check the "FoundationWrap" release page for possibly pre-packaged release archives.
Otherwise, here is how to build and repackage the Foundation:

### mulle-objc version 0.20

For this to work you need to repackage all the Objective-c libraries as well as mulle-sprintf of [Foundation](//github.com/MulleFoundation/Foundation) into 
**FoundationWrap**. Place the `Foundation-startup`, `mulle-atinit`, `mulle-atexit` libraries into **FoundationWrap-startup**. Combine all the remaining
C files into a **c-wrap** library. Create a directory `usr/include` and copy all the headers recursively there. Create a directory `usr/lib` and copy the three
libraries there.


### mulle-objc version 0.21 (Future as of 1.2022) and beyond

Use [FoundationWrap](//github.com/MulleFoundation/FoundationWrap) to create a directory `usr` in your project with 
all the required headers and libraries.

Assuming your project is called "myproject" and has been placed into `~/CLionProjects`.

```
mulle-sde install --debug --prefix ~/CLionProjects/myproject/usr https://github.com/MulleFoundation/FoundationWrap
```

## 3. Reload CMake caches 

CLion's cmake cache needs to be resetted to work with the new configuration. Chose "Tools / Cmake / Reset Cache and Reload Project"

![image](https://user-images.githubusercontent.com/38703833/151207720-ec84dc9b-4423-48f2-9aa8-e0012e53e790.png)


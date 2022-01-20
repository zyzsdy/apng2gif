# apng2gif

This project has been in disrepair for long time. Recently, 
there is need to change the number of loops in apng file. So
I used it to modify it.

Here is the original source code information:

--------------------------------
>
> This program converts APNG animations into animated GIF format.
> Wu quantizer is used for true-color files.
>
> http://apng2gif.sourceforge.net/
>
> Copyright (c) 2010-2015 Max Stepin
> maxst@users.sourceforge.net
>
> License: zlib license
>
--------------------------------

## Usage 

```
apng2gif anim.png [anim.gif] [-t tlevel] [-b bcolor] [-l loop]
```

  Options:
```
-t 128 
```
  will set the transparency threshold level as 128, so pixels 
  with alpha level less than 128 will become fully transparent.
```
-b 255 0 0 
-b "#ff0000"
```
  will set the background color as red, so partially transparent 
  pixels will be composed over red. When -b is used, -t is ignored.

  When no options are specified, default threshold is 128, 
  no background color.
```
-l 0
```
  will make the generated gif loop infinitely, replacing the number
  of loops originally set in apng file.
```
-l orig
```
  will preserve the original loop count of apng file.

## Build

All dependencies are included in the source code repository.

Use the following command to build:

```
mkdir build
cd build
cmake ../
make
make install
```

If you use CMake GUI:

Source code: Select the root directory of this repository.
Build Binaries: Use `./build`.

Then click the button Configure twice, then click the Generate button, and then you can see the project file.
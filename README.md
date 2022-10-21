# Tecniche, Algoritmi, APA: CLION TEMPLATE

## What is this
This is a *not official* CMake template, intended to quickly setup your lab projects, in the Politecnico di Torino courses for *APA* (deprecated course), *Tecniche di Programmazione*,  *Algoritmi e Strutture Dati*. <br>

It is intended to be used with CLion, but if you feel brave you can use it without a GUI.

## Setup your project
- Download this project on your machine (git clone or download zip)
- Rename the main folder as your Lab name *(e.g. L01 for lab1)*
- (optional) open it in CLion
- Create a copy of the `EZZ` directory for every exercise. Rename it as the exercise name *(e.g. E01 for ex.1)*
- Edit CMakeLists.txt:
  - `line 6`: set `LAB_NAME` variable as the lab name *(e.g. L03 for lab 3)*
  - `line 9`: add the exercise directory names *(e.g. set(DIRECTORIES E01 E02 E03))*
- Inside each exercise folder:
  - Edit CMakeLists.txt:
    - `line 4`  set `project()` as the exercise name *(e.g. E03 for exercise 3)* <br>
    - `line 8` add executable files if needed (shouldn't be necessary)
    - `line 16` add/remove file names if needed

### note about file handling 
This template tries to offer a quick solution for a very common problem: when opening a file, usually a lot of people
tries to open it using its relative path (e.g. `./file.txt`). This causes problems since the executable, when built,
usually looks for its relative path and doesn't find it, sinche the file itself doesn't get copied.

The "standard" solution is to include the full path (e.g. `C:\user\develop\file.txt`).

With this template CMake copies the files inside the build folder: this enables you to open your files using relative path.
To do so, you need to add the **relative path** (starting from the main.c location!) of the file to the exercises CMakeLists.txt.

It is *recommended* to add your files into the same folder as your main.c !


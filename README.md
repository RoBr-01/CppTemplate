
# C++ Template Project  

## General

A simple-ish C++ template project.
This is mostly intended for use with VSCode, but you can hook up your own debugging as needed.
It provides the basic CMake setup for building executables and libraries, as well as options for running tests and benchmarks.

For this purpose, googletest and google benchmark are added as submodules, however they are not required.

##  Requirements

- CMake
- Ninja
- GCC, Clang (or MSVC if you must)

## Set-up

### Clone the project

```sh
git clone --recursive https://github.com/RoBr-01/CppTemplate.git
```
Enter the folder

```sh
cd CppTemplate
```

### Choose the configuration

Use:

```sh
cmake --list-presets
``` 
To show all the available presets, the names should be self-explanatory.

### Configure

Having chosen the preset you want to configure/build, do:

```sh
cmake --preset <thepresetyouwant>
``` 

Note: CMake will use whatever compiler is default in your environment.

###  Build (Compile the Project)  

After configuring, build using the corresponding preset:  

```sh
cmake --build --preset <thepresetyouwant>
```  

The build directory is automatically generated. Your executable will be located at:

```
build/<thepresetyouwant>/Executablename
```

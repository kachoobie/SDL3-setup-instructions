# SDL3 Setup Instructions

Largely based off of tutorials by [Mike Shah](https://www.youtube.com/watch?v=kyD5H6w1x-o&list=PLvv0ScY6vfd-RZSmGbLkZvkgec6lJ0BfX&index=1&ab_channel=MikeShah). These instructions are intended for MacOS.

## Install Homebrew and Pkgconf
Execute the following command to install Brew.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Once brew is intalled, it will provide you the commands to export it to you path.

Now, use brew to install `pkgconf`.

```bash
brew install pkgconf
```

## Clone SDL3 Repository and Download CMake

Clone the SDL3 repository from Github.

```bash
git clone https://github.com/libsdl-org/SDL.git
```

Make sure [CMake](https://cmake.org/) is downloaded.

## Create SDL Makefile

In the root `SDL` directory, create a `build` folder.

```bash
mkdir build
```

Navigate to your new `build` folder and generate the makefile using CMake.

```bash
cd build && cmake ../
```

## Build SDL3 Dynamic Library

Inside your build directory should be a bunch of new stuff, including the `Makefile`. Use the Makefile to build the SDL3 dynamic library.

```bash
make -j 16
```
> [!NOTE]
> If the above command gives you trouble, try running `make` instead of `make -j 16`.

Save the paths to the build directory to the dynamic library. Enter your password when prompted.

```bash
sudo make install
```

Make sure pkg-config acknowledges the library and header file locations.

```bash
pkg-config --libs sdl3
pkg-config --cflags sdl3
```

## Run SDL3 Example

SDL3 should be ready to use. Test it out!

Compile `example.cpp` and run the executable.

```bash
clang++ main.cpp `pkg-config --libs --cflags sdl3`
./a.out
```


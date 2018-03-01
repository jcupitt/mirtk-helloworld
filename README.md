# MIRTK helloworld

This is supposed to be a tiny example showing how to build a project against
[MIRTK](https://github.com/BioMedIA/MIRTK).

`flip.cc` is copied from the MIRTK sources as an sample program that someone
might try to build. 

# Building

Append this to your `.bashrc`:

```
export MIRTK_ROOT=/home/john/mirtk
export PATH="$MIRTK_ROOT/bin:$PATH"
export LD_LIBRARY_PATH="$MIRTK_ROOT/lib:$LD_LIBRARY_PATH"
```

Install VTK 8.1. Ubuntu 17.10 bundles VTK 6, which is too old for 
current MIRTK.

```
$ cd VTK-8.1.0
$ mkdir build
$ cd build
$ cmake -D CMAKE_INSTALL_PREFIX:PATH=$MIRTK_ROOT ..
$ make -j 8 
$ make install
```

Clone MIRTK from github. It uses submodules, which you must also init.

```
$ cd MIRTK
$ cd Packages
$ git submodule update --init -- *
$ cd ..
$ cd build
$ cmake -D WITH_VTK=ON -D MODULE_Deformable=ON -D MODULE_DrawEM=ON -D MODULE_Mapping=ON -D MODULE_PointSet=ON -D MODULE_Scripting=ON -D CMAKE_INSTALL_PREFIX:PATH=$MIRTK_ROOT ..
$ make -j 8 
$ make install
```

Then try this thing:

```
$ mkdir build
$ cd build
$ cmake -D CMAKE_MODULE_PATH:PATH="$MIRTK_ROOT/share/cmake;$MIRTK_ROOT/lib/cmake/mirtk" -D CMAKE_INSTALL_PREFIX:PATH=$MIRTK_ROOT ..
$ make
$ make install
```


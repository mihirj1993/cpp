
 

 

 

 

 

([C++](Cpp.md)) [bzlib.h: No such file or directory](CppInstallErrorBzlibHnoSuchFileOrDirectory.md)
=====================================================================================================

 

[Install error](CppInstallError.md) that can occur when installing
[Boost](CppBoost.md).

 

After doing the following, the error pops up:

 

  ----------------------------------------------------------------------
  ` ./bootstrap ./bjam --build-dir=/tmp/build-boost toolset=gcc stage`
  ----------------------------------------------------------------------

 

Solution: install python-dev:

 

  --------------------------------------------------------------------------------------------------------
  ` sudo apt-get install python-dev sudo apt-get install python-bzutils sudo apt-get install libbz2-dev`
  --------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


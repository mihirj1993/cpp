
 

 

 

 

 

([C++](Cpp.md)) [std::printf](CppStdPrintf.md)
=============================================

 

[std::printf](CppStdPrintf.md) is an [STL](CppStl.md)
[function](CppFunction.md) to write formatted output to
[std::cout](CppStdCout.md).

 

[std::printf](CppStdPrintf.md) is not typesafe (see example below). For a
type-safe alternative, use [boost::format](CppFormat.md) instead.

 

 

 

 

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cstdio> #include <iostream> #include <boost/format.hpp>  int main() {   //Correct   std::printf("(x,y) = (%1+5d,%2+5d) \n",-1,2);   std::cout     << boost::format("(x,y) = (%1+5d,%2+5d) \n") % -1 % 2;    //Incorrect   std::printf("(x,y) = (%1+5d,%2+5d) \n",-1.5,2.5);   std::cout     << boost::format("(x,y) = (%1+5d,%2+5d) \n") % -1.5 % 2.5; }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ----------------------------------------------------------------------------------------------
  ` (x,y) = (   -1, +2) (x,y) = (   -1, +2) (x,y) = (   +0,-1074266112) (x,y) = ( -1.5, +2.5)`
  ----------------------------------------------------------------------------------------------

 

 

 

 

 

External links
--------------

 

-   [Cplusplus.com page about
    std::printf](http://www.cplusplus.com/reference/clibrary/cstdio/printf)

 

 

 

 

 

 


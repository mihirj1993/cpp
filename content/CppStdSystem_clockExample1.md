
 

 

 

 

 

([C++](Cpp.md)) [StdSystem\_clockExample1](CppStdSystem_clockExample1.md)
===========================================================================

 

Technical facts
---------------

 

[Operating system(s) or programming environment(s)](CppOs.md)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.md) 15.04 (vivid)

[IDE(s)](CppIde.md):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.md) 3.1.1

[Project type](CppQtProjectType.md):

-   ![console](PicConsole.png) [Console
    application](CppConsoleApplication.md)

[C++ standard](CppStandard.md):

-   ![C++98](PicCpp98.png) [C++98](Cpp98.md)

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.9.2

[Libraries](CppLibrary.md) used:

-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): ./CppStdSystem\_clockExample1/CppStdSystem\_clockExample1.pro
------------------------------------------------------------------------------------------------------

 

  ---------------------------------------------------------------
  ` include(../../ConsoleApplication.pri)  SOURCES += main.cpp`
  ---------------------------------------------------------------

 

 

 

 

 

./CppStdSystem\_clockExample1/main.cpp
--------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <chrono> #include <cmath> #include <iostream>  int main() {   const std::chrono::system_clock::time_point t = std::chrono::system_clock::now();   const std::chrono::high_resolution_clock::time_point u = std::chrono::high_resolution_clock::now();    //Burn some time   for (int i=0; i!=100000000; ++i)   {     for (int j=0; j!=10; ++j)     {       std::sqrt(static_cast<double>(i + j));     }   }    const std::chrono::system_clock::duration d = std::chrono::system_clock::now() - t;   const std::chrono::system_clock::duration e = std::chrono::high_resolution_clock::now() - u;    std::cout     << std::chrono::duration_cast<std::chrono::milliseconds>(d).count() << " milliseconds" << '\n'     << std::chrono::duration_cast<std::chrono::milliseconds>(e).count() << " milliseconds" << '\n'     << std::endl; }  /* Screen output:  7651 milliseconds 7651 milliseconds  Press <RETURN> to close this window...  */`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 



 

 

 

 

 

([C++](Cpp.md)) [BoostTriboolExample1](CppBoostTriboolExample1.md)
====================================================================

 

![Boost](PicBoost.png)

 

[boost::tribool example 1](CppBoostTriboolExample1.md) is a
[boost::tribool](CppBoostTribool.md) [example](CppExample.md).

Technical facts
---------------

 

[Application type(s)](CppApplication.md)

-   ![Desktop](PicDesktop.png) [Desktop
    application](CppDesktopApplication.md)

[Operating system(s) or programming environment(s)](CppOs.md)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.md) 15.04 (vivid)

[IDE(s)](CppIde.md):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.md) 3.1.1

[Project type](CppQtProjectType.md):

-   ![GUI](PicGui.png) [GUI application](CppGuiApplication.md)

[C++ standard](CppStandard.md):

-   ![C++11](PicCpp11.png) [C++11](Cpp11.md)

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.9.2

[Libraries](CppLibrary.md) used:

-   ![Qt](PicQt.png) [Qt](CppQt.md): version 5.4.1 (32 bit)
-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): ./CppBoostTriboolExample1/CppBoostTriboolExample1.pro
----------------------------------------------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` exists (../../ConsoleApplication.pri) {   include(../../ConsoleApplication.pri) } !exists (../../ConsoleApplication.pri) {   QT += core   QT += gui   CONFIG   += console   CONFIG   -= app_bundle   TEMPLATE = app   CONFIG(release, debug|release) {     DEFINES += NDEBUG NTRACE_BILDERBIKKEL   }    QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra -Weffc++    unix {     QMAKE_CXXFLAGS += -Werror   } }  exists(../../Libraries/Boost.pri) {   include(../../Libraries/Boost.pri) } !exists(../../Libraries/Boost.pri) {   win32 {     INCLUDEPATH += \       ../../Libraries/boost_1_54_0   } }  SOURCES += main.cpp`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppBoostTriboolExample1/main.cpp
----------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-but-set-parameter" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #include <boost/logic/tribool.hpp> #pragma GCC diagnostic pop   int main() {   const boost::logic::tribool t { true };   const boost::logic::tribool f { false };   const boost::logic::tribool i { boost::logic::indeterminate };    /* WILL FAIL   assert(t);   assert(!f);   assert(t == t);   assert(f == f);   assert(i == i);   assert(t != f);   assert(f != i);   assert(i != t);   assert(t != i);   assert(f != t);   assert(i != f);   assert(t == true);   assert(f == false);   assert(i == boost::logic::indeterminate);   assert(t != false);   assert(f != boost::logic::indeterminate);   assert(i != true);   assert(t != boost::logic::indeterminate);   assert(f != true);   assert(i != false);   assert(t == boost::logic::tribool::true_value);   assert(f == boost::logic::tribool::false_value);   assert(i == boost::logic::tribool::indeterminate_value);   */    assert(boost::logic::indeterminate(i));   if ( t) { /* OK */ } else { assert(!"Should not get here"); }   if (!t) { assert(!"Should not get here"); } else { /* OK */ }   if (!f) { /* OK */ } else { assert(!"Should not get here"); }   if ( f) { assert(!"Should not get here"); } else { /* OK */ }   if ( boost::logic::indeterminate(i)) { /* OK */ } else { assert(!"Should not get here"); }   if (!boost::logic::indeterminate(t)) { /* OK */ } else { assert(!"Should not get here"); }   if (!boost::logic::indeterminate(f)) { /* OK */ } else { assert(!"Should not get here"); } }`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


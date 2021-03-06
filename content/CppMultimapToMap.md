
 

 

 

 

 

([C++](Cpp.md)) [MultimapToMap](CppMultimapToMap.md)
======================================================

 

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

-   ![C++11](PicCpp11.png) [C++11](Cpp11.md)

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.9.2

[Libraries](CppLibrary.md) used:

-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): ./CppMultimapToMap/CppMultimapToMap.pro
--------------------------------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------
  ` TEMPLATE = app CONFIG += console CONFIG -= app_bundle CONFIG -= qt QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra -Werror SOURCES += main.cpp`
  ----------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppMultimapToMap/main.cpp
---------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <map>  template <class Key, class Value> const std::map<Key,Value> MultimapToMap(   const std::multimap<Key,Value> m) {   std::map<Key,Value> n;   const auto end = m.end();   for (auto begin = m.begin(); begin != end; )   {     assert(begin != m.end());     const auto key = (*begin).first;     assert(m.find(key) != m.end());      //Must the average be calculated?     const auto r = m.equal_range(key);     assert(r.first != m.end());      if (r.first != r.second )     {       Value sum(0.0);       int cnt = 0;       for (auto i = r.first; i!=r.second; ++i)       {         sum += (*i).second;         ++cnt;       }       const Value result( sum / static_cast<double>(cnt));       n[ key ] = result;     }     else     {       const Value result((*r.first).second);       n[ key ] = result;     }     begin = r.second;   }   return n; }  int main() {   {     const std::multimap<int,double> m ( { { 1, 1.0} } );     const std::map<int,double> n(MultimapToMap(m));     assert(n.size() == 1);   }   {     const std::multimap<int,double> m ( { { 1, 1.0}, { 1, 1.0} } );     const std::map<int,double> n(MultimapToMap(m));     const std::map<int,double> e( { { 1, 1.0 } } );     assert(n.size() == 1);     assert(n == e);   }   {     const std::multimap<int,double> m ( { { 1, 1.0}, { 1, 2.0} } );     const std::map<int,double> n(MultimapToMap(m));     const std::map<int,double> e( { { 1, 1.5 } } );     assert(n.size() == 1);     assert(n == e);   }   {     const std::multimap<int,double> m ( { {0, 0.0}, { 1, 1.0}, { 1, 1.0}, {2, 2.0} } );     const std::map<int,double> n(MultimapToMap(m));     const std::map<int,double> e( { {0, 0.0}, { 1, 1.0 }, {2, 2.0} } );     assert(n.size() == 3);     assert(n == e);   }   {     const std::multimap<int,double> m ( { {0, 0.0}, { 1, 1.0}, { 1, 2.0}, {2, 2.0} } );     const std::map<int,double> n(MultimapToMap(m));     const std::map<int,double> e( { {0, 0.0}, { 1, 1.5 }, {2, 2.0} } );     assert(n.size() == 3);     assert(n == e);   }   assert(1==2); }`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


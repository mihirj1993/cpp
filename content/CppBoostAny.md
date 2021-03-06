# ([C++](Cpp.md)) [boost::any](CppStdAny.md)

[boost::any](CppStdAny.md) is a [Boost](CppBoost.md)
[container](CppContainer.md) for type-safe storage of any [data
type](CppDataType.md).

 

 

 

 

 

Project and source code
-----------------------

 

Operating system: [Ubuntu](http://www.ubuntu.com) 10.04 LTS Lucid Lynx

[IDE](CppIde.md): [Qt Creator](CppQt.md) 2.0.0

[Project type](CppQtProjectType.md): Qt4 Console Application

[Compiler](CppCompiler.md): [G++](CppGpp.md) 4.4.1

[Libraries](CppLibrary.md) used:

-   [Boost](CppBoost.md): version 1.40
-   [STL](CppStl.md): from [GCC](CppGcc.md), shipped with [Qt
    Creator](CppQt.md) 2.0.0

 

-   [Download the Qt Creator project 'CppAny' (zip)](CppAny.zip)

 

 

 

 

 

### main.cpp

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <iostream> #include <string> #include <vector> #include <boost/any.hpp>   int main() {   std::vector<boost::any> v;   v.push_back(boost::any(123));   v.push_back(boost::any(123.456));   v.push_back(boost::any(std::string("123")));   std::random_shuffle(v.begin(),v.end());    const std::size_t sz = v.size();    for (std::size_t i = 0; i!=sz; ++i)   {     if (v[i].type() == typeid(int))     {       std::cout << "int found at index '" << i         << "': " << boost::any_cast<int>(v[i]) << '\n';     }     else if (v[i].type() == typeid(double))     {       std::cout << "double found at index '" << i         << "': " << boost::any_cast<double>(v[i]) << '\n';     }     else if (v[i].type() == typeid(std::string))     {       std::cout << "std::string found at index '" << i         << "': " << boost::any_cast<std::string>(v[i]) << '\n';     }   } }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  -------------------------------------------------------------------------------------------------------
  ` int found at index '0': 123 std::string found at index '1': 123 double found at index '2': 123.456`
  -------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


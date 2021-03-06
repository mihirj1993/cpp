
 

 

 

 

 

([C++](Cpp.md)) [std::setfill](CppSetfill.md)
===============================================

 

[std::setfill](CppSetfill.md) is an [STL](CppStl.md)
[std::iostream](CppIostream.md) manipulator to determine the
filling/padding character used by [std::setw](CppSetw.md).

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iomanip> #include <iostream>  int main() {   const int value = 123;   std::cout     << "12345678\n"     << std::setw(8) << value << '\n'     << std::setfill('x') << std::setw(8) << value << '\n'; }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  -------------------------------
  ` 12345678      123 xxxxx123`
  -------------------------------

 

 

 

 

 

External links
--------------

 

-   [Cplusplus.com page about
    std::setfill](http://www.cplusplus.com/reference/iostream/manipulators/setfill)

 

 

 

 

 

 


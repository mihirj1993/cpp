
 

 

 

 

 

([C++](Cpp.md)) [StringGridToVector](CppStringGridToVector.md)
================================================================

 

[VCL](CppVcl.md) [code snippet](CppCodeSnippets.md) to convert a
[VCL](CppVcl.md) [TStringGrid](CppTStringGrid.md) to a 2D
[std::vector](CppStdVector.md).

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <string> #include <vector> #include <boost/lexical_cast.hpp> #include <vcl.h>  //From http://www.richelbilderbeek.nl/CppStringGridToVector.htm template <class T> const std::vector<std::vector<T> > StringGridToVector(const TStringGrid * const stringGrid) {   assert(stringGrid!=0 && "StringGrid must not be NULL");   const int height = stringGrid->RowCount;   const int width  = stringGrid->ColCount;   std::vector<std::vector<T> > v(height, std::vector<T>(width));   for (int y=0; y!=height; ++y)   {     assert(y >=0);     assert(y < static_cast<int>(v.size()) );     std::vector<T>& line = v[y];     //Don't have the guts to do a line-access on a TStringGrid...      for (int x=0; x!=width; ++x)     {       assert(x >=0);       assert(x < static_cast<int>(line.size()) );       //const_cast because the VCL is not const-correct. Grumble, grumble...       const std::string s = (const_cast<TStringGrid*>(stringGrid)->Cells[x][y]).c_str();       const T t = boost::lexical_cast<T>(s);       vLine[x] = t;     }   }   return v; }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 



 

 

 

 

 

([C++](Cpp.md)) [MinElementAbove](CppMinElementAbove.md)
==========================================================

 

[MinElementAbove](CppMinElementAbove.md) is a [math](CppMath.md) [code
snippet](CppCodeSnippets.md) to get the
[std::min\_element](CppStdMin_element.md) above a certain value.

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //From http://www.richelbilderbeek.nl/CppMinElementAbove.htm double MinElementAbove(const std::vector<double>& v, const double above) {   const double max = std::numeric_limits<double>::max();   double lowest = max;   const std::vector<double>::const_iterator j = v.end();   std::vector<double>::const_iterator i = v.begin();   for ( ; i!=j; ++i)   {     if (*i > above && *i < lowest)     {       lowest = *i;     }   }   return (lowest != max ? lowest : above); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


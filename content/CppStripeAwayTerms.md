
 

 

 

 

 

([C++](Cpp.md)) [StripeAwayTerms](CppStripeAwayTerms.md)
==========================================================

 

[Math](CppMath.md) [code snippet](CppCodeSnippets.md) to stripe away
equal terms in two sets. For example: for sets n and d, where n =
{1,2,3,4} and d = {1,2,3}, [StripeAwayTerms](CppStripeAwayTerms.md)
replaces the 2 and 3 of both sets by a 1. This can be used to divide two
[factorials](CppFactorial.md).

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <vector>  //From http://www.richelbilderbeek.nl/CppStripeAwayTerms.htm void StripeAwayTerms(std::vector<int>& v_x, std::vector<int>& v_y) {   std::vector<int>::iterator x = v_x.begin();   const std::vector<int>::iterator x_end = v_x.end();   for ( ; x!=x_end; ++x)   {     if (*x == 1) continue;     std::vector<int>::iterator y = v_y.begin();     const std::vector<int>::iterator y_end = v_y.end();     for ( ; y!=y_end; ++y)     {       if (*y == 1) continue;       if (*x % *y == 0) { *x/=*y; *y=1; }       if (*y % *x == 0) { *y/=*x; *x=1; }     }   } }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


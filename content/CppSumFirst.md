# ([C++](Cpp.md)) [SumFirst](CppSumFirst.md)

[SumFirst](CppSumFirst.md) is the answer of question \#21 of [Exercise
\#9: No for-loops](CppExerciseNoForLoops.md).

You may [contact me](http://www.richelbilderbeek.nl/Contact.htm) if you have an [STL](CppStl.md)
solution...

## ![Boost](PicBoost.png) [Boost](CppBoost.md).Bind [SumFirst](CppSumFirst.md)

Thanks to 'ofwolfandman':

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <functional> #include <numeric> #include <utility> #include <vector> #include <boost/bind.hpp>  int SumFirst(const std::vector<std::pair<int,int> >& v) {   return std::accumulate(     v.begin(),     v.end(),     static_cast<int>(0),     boost::bind(       std::plus<int>(),       _1,       boost::bind<int>(&std::pair<int,int>::first, _2)       )     ); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## ![Boost](PicBoost.png) [Boost](CppBoost.md).Lambda [SumFirst](CppSumFirst.md)

Thanks to 'ofwolfandman':

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <functional> #include <numeric> #include <utility> #include <vector> #include <boost/lambda/lambda.hpp> #include <boost/lambda/bind.hpp>  int SumFirst(const std::vector<std::pair<int,int> >& v) {   return std::accumulate(     v.begin(),     v.end(),     static_cast<int>(0),     boost::lambda::_1     + boost::lambda::bind(       &std::pair<int, int>::first, boost::lambda::_2       )   ); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

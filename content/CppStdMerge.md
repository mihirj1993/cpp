
 

 

 

 

 

([C++](Cpp.md)) [std::merge](CppStdMerge.md)
===========================================

 

[std::merge](CppStdMerge.md) is an [algorithm](CppAlgorithm.md) that
merges two sorted [containers](CppContainer.md) into a third sorted
[container](CppContainer.md).

 

[std::merge](CppStdMerge.md) is [defined](CppDefinition.md) in the
[header file](CppHeaderFile.md) [algorithm.h](CppAlgorithmH.md).

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <algorithm> #include <iostream> #include <iterator> #include <vector>  int main() {   std::vector<int> v1;   v1.push_back(1);   v1.push_back(4);   v1.push_back(9);   v1.push_back(16);    std::vector<int> v2;   v2.push_back(1);   v2.push_back(1);   v2.push_back(2);   v2.push_back(3);   v2.push_back(5);   v2.push_back(8);   v2.push_back(13);    std::vector<int> v3;   //Merge v1 and v2 to v3   std::merge(     v1.begin(),v1.end(),     v2.begin(),v2.end(),     std::back_inserter(v3));   //Display v3   std::copy(     v3.begin(),v3.end(),     std::ostream_iterator<int>(std::cout,"\n")); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Screen output:

 

  ----------------------------
  ` 1 1 1 2 3 4 5 8 9 13 16`
  ----------------------------

 

 

 

 

 

External links
--------------

 

-   [SGI page about std::merge](http://www.sgi.com/tech/stl/merge.html)

 

 

 

 

 

 



 

 

 

 

 

([C++](Cpp.md)) [iterator.hpp: Invalid template argument list](CppCompileErrorIteratorHppInvalidTemplateArgumentList.md)
==========================================================================================================================

 

[Compile error](CppCompileError.md).

 

Full error message
------------------

 

  -----------------------------------------------------------------------
  ` [C++ Error] iterator.hpp(62): E2401 Invalid template argument list`
  -----------------------------------------------------------------------

 

 

 

 

 

Cause
-----

 

-   IDE: [C++ Builder](CppBuilder.md) 6.0
-   [Compiler](CppCompiler.md): Borland BCC32.EXE version 6.0.10.157
-   Boost version: 1.35.0.

 

  ---------------------------------
  ` #include <boost/foreach.hpp>`
  ---------------------------------

 

 

 

 

 

Which takes you to the following line in
'include/boost/range/iterator.hpp':

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` typedef BOOST_RANGE_DEDUCED_TYPENAME mpl::eval_if_c< is_const<C>::value, range_const_iterator< typename remove_const<C>::type >, range_mutable_iterator<C> >::type type;`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Solution
--------

 

This compiler is not supported by Boost. Change to another compiler.

 

 

 

 

 

Note
----

 

This does not work:

 

  ---------------------------------------------------------
  ` #define BOOST_MSVC 1310 #include <boost/foreach.hpp>`
  ---------------------------------------------------------

 

 

 

 

 

 


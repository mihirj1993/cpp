
 

 

 

 

 

([C++](Cpp.md)) [Unable to locate component](CppMiscErrorUnableToLocateComponent.md)
======================================================================================

 

[Misc error](CppMiscError.md).

 

 

 

 

 

Full error message
------------------

 

[View a screenshot of this error
message](CppMiscErrorUnableToLocateComponent.md).

 

A message dialog appears.

 

The title of the message dialog is:

 

  ----------------------------------------------
  ` HelloWorld.exe Unable To Locate Component`
  ----------------------------------------------

 

The text of the message dialog is:

 

  ----------------------------------------------------------------------------------------------------------------------------------------
  ` This application has failed to start because libgcc_s_dw2-1.dll was not found. Re-installing this application may fix this problem.`
  ----------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Cause
-----

 

IDE: [Qt Creator](CppQt.md) 1.2.1

[Compiler](CppCompiler.md): [G++](CppGpp.md) 4.4.1

Boost version: 1.38.0.

Platform: Windows XP, version 2002, Service Pack 3

 

After creating a [Hello World program
(console)](CppBuilderHelloWorld.md) the MS-DOS command prompt was used
to start the executable HelloWorld.exe.

 

 

 

 

 

Solution
--------

 

Download the DLL using Google. Put it in your system path (for example,
in C:\\Windows\\System32).

 

 

 

 

 

 


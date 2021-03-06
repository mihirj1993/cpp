
 

 

 

 

 

([C++](Cpp.md)) [HelloQwtQtCreatorWindows](CppHelloQwtQtCreatorWindows.md)
============================================================================

 

![Qwt](PicQwt.png)![Qt
Creator](PicQtCreator.png)![Windows](PicWindows.png)

 

[Hello Qwt using Qt Creator under
Windows](CppHelloQwtQtCreatorWindows.md) is a [Hello
Qwt](CppHelloQwt.md) program.

 

-   [Download the Qt Creator project
    'CppHelloQwtQtCreatorWindows' (zip)](CppHelloQwtQtCreatorWindows.zip)

Technical facts
---------------

 

[Application type(s)](CppApplication.md)

-   ![Desktop](PicDesktop.png) [Desktop
    application](CppDesktopApplication.md)

[Operating system(s) or programming environment(s)](CppOs.md)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.md) 15.04 (vivid)

[IDE(s)](CppIde.md):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.md) 3.1.1

[Project type](CppQtProjectType.md):

-   ![GUI](PicGui.png) [GUI application](CppGuiApplication.md)

[C++ standard](CppStandard.md):

-   ![C++98](PicCpp98.png) [C++98](Cpp98.md)

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.9.2

[Libraries](CppLibrary.md) used:

-   ![Qt](PicQt.png) [Qt](CppQt.md): version 5.4.1 (32 bit)
-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): ./CppHelloQwtQtCreatorWindows/CppHelloQwtQtCreatorWindows.pro
------------------------------------------------------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` exists (../../Libraries/ConsoleApplication.pri) {   include(../../ConsoleApplication.pri) } !exists (../../Libraries/GeneralConsole.pri) {   QT       += core gui   greaterThan(QT_MAJOR_VERSION, 4): QT += widgets   TEMPLATE = app   SOURCES += main.cpp   QMAKE_CXXFLAGS += -Wall -Wextra -Werror }   exists (../../Libraries/Qwt.pri) {   include(../../Libraries/Qwt.pri) } !exists (../../Libraries/Qwt.pri) {   INCLUDEPATH+= ../../Libraries/qwt-6.1/src   LIBS+= -L../../Libraries/qwt-6.1/lib    CONFIG(release, debug|release) {     message(Windows: Qwt: Linking to qwt)     LIBS += -lqwt   }    CONFIG(debug, debug|release) {     message(Windows: Qwt: Linking to qwtd)     LIBS += -lqwtd   } }`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppHelloQwtQtCreatorWindows/main.cpp
--------------------------------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert> #include <cmath> #include <string> #include <string> #include <sstream>  #include <QLabel> #include <QVBoxLayout> #include <QApplication>   #include "qwt_plot.h" #include "qwt_plot_curve.h" #include "qwt_text.h"  #ifdef _WIN32 #include "qwt_point_data.h" #endif  int main(int argc, char *argv[]) {   QApplication a(argc, argv);    QwtPlotCurve * const m_curve = new QwtPlotCurve("Sine");   QwtPlot * const m_plot = new QwtPlot(QwtText("CppHelloQwtQtCreatorWindows"));    m_plot->setGeometry(0,0,640,400);   m_plot->setAxisScale(QwtPlot::xBottom, 0.0,2.0 * M_PI);   m_plot->setAxisScale(QwtPlot::yLeft,-1.0,1.0);   std::vector<double> xs;   std::vector<double> ys;   for (double x = 0; x < 2.0 * M_PI; x+=(M_PI / 10.0))   {     xs.push_back(x);     ys.push_back(std::sin(x));   }   #ifdef _WIN32   QwtPointArrayData * const data = new QwtPointArrayData(&xs[0],&ys[0],xs.size());   m_curve->setData(data);   #else   m_curve->setData(&xs[0],&ys[0],xs.size());   #endif   m_curve->attach(m_plot);   m_plot->replot();   m_plot->show();    return a.exec(); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppHelloQwtQtCreatorWindows/CppHelloQwtQtCreatorWindows.sh
------------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #!/bin/bash mymake="e:/Qt/Qt5.1.0/Tools/mingw48_32/bin/mingw32-make.exe" myqmake="e:/Qt/Qt5.1.0/5.1.0/mingw48_32/bin/qmake.exe" mytarget="CppHelloQwtQtCreatorWindows" myprofile=$mytarget.pro myexe=release/$mytarget.exe   if [ -e $myqmake ] then   echo "Compiler '$myqmake' found" else   echo "Compiler '$myqmake' not found directly"   #exit fi  if [ -e $myprofile ] then   echo "Qt Creator project '$myprofile' found" else   echo "Qt Creator project '$myprofile' not found"   exit fi  echo "1/2: Creating Windows makefile" $myqmake $myprofile  if [ -e Makefile ] then   echo "Makefile created successfully" else   echo "FAIL: $myqmake $myprofile"   exit fi  if [ -e $mymake ] then   echo "Compiler '$mymake' found" else   echo "Compiler '$mymake' not found directly"   #exit fi  echo "2/2: making makefile"  $mymake  echo $myexe  if [ -e $myexe ] then   echo "SUCCESS" else   echo "FAIL" fi  #Cleaning up rm Makefile rm Makefile.* rm -r release rm -r debug`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


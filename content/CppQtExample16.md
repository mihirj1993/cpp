
 

 

 

 

 

([C++](Cpp.md)) [QtExample16](CppQtExample16.md)
==================================================

 

![Qt](PicQt.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)![Ubuntu](PicUbuntu.png)

 

This [Qt](CppQt.md) example shows how to using resources, like [this
screenshot (png)](CppQtExample16.png).

 

-   [Download the Qt Project of 'QtExample16' (zip)](CppQtExample16.zip)

 

 

 

 

 

Using resources in [Qt Creator](CppQt.md) 2.0.0
------------------------------------------------

 

Here follows a step-by-step guide to add a bitmap as a resource to a [Qt
Creator](CppQt.md) project:

 

1.  [View screenshot](CppQtExample16_1.png)
2.  In the Project Manager, right-click on the project name on on the
    'Sources' folder. Click 'Add New'
3.  [View screenshot](CppQtExample16_2.png)
4.  In the 'New File' dialog, select to create a new 'Qt Resource file'
5.  [View screenshot](CppQtExample16_3.png)
6.  In the 'New Qt Resource file -&gt; Location' dialog, give the
    resource file a name. For example, 'MyResources'
7.  [View screenshot](CppQtExample16_4.png)
8.  In the 'New Qt Resource file -&gt; Project management' dialog, click
    'Finish'
9.  [View screenshot](CppQtExample16_5.png)
10. As you can see, 'MyResources.qrc' has now been added to the
    Project Manager. Double-click on 'MyResources.qrt' and click 'Add
    -&gt; Add Prefix' (which is all there is to choose yet)
11. [View screenshot](CppQtExample16_6.png)
12. Change the prefix to a more fitting name, for example 'MyImages'.
13. [View screenshot](CppQtExample16_7.png)
14. Click 'Add -&gt; Add Files' and add an image. In this example, this
    is a file called 'BeerSmall.bmp' (a sprite from
    [BeerWanter](https://github.com/richelbilderbeek/BeerWanter))
15. [View screenshot](CppQtExample16_8.png)
16. Now, the file has been added to your resources. The image can be
    accessed with the filename ':/MyImages/BeerSmall.bmp'
17. [View screenshot](CppQtExample16_9.png)
18. Copy-paste the example code below
19. [View final screenshot](CppQtExample16.png)

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

-   ![C++11](PicCpp11.png) [C++11](Cpp11.md)

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.9.2

[Libraries](CppLibrary.md) used:

-   ![Qt](PicQt.png) [Qt](CppQt.md): version 5.4.1 (32 bit)
-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.9.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): ./CppQtExample16/CppQtExample16.pro
----------------------------------------------------------------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` exists(../../DesktopApplication.pri) {   include(../../DesktopApplication.pri) } !exists(../../DesktopApplication.pri) {   QT += core gui   greaterThan(QT_MAJOR_VERSION, 4): QT += widgets   TEMPLATE = app    CONFIG(debug, debug|release) {     message(Debug mode)   }    CONFIG(release, debug|release) {     message(Release mode)     DEFINES += NDEBUG NTRACE_BILDERBIKKEL   }    QMAKE_CXXFLAGS += -std=c++11 -Wall -Wextra    unix {     QMAKE_CXXFLAGS += -Werror   } }  exists(../../Libraries/Boost.pri) {   include(../../Libraries/Boost.pri) } !exists(../../Libraries/Boost.pri) {   win32 {     INCLUDEPATH += \       ../../../Projects/Libraries/boost_1_55_0   } }  SOURCES += main.cpp  RESOURCES += MyResources.qrc`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQtExample16/main.cpp
-------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <cassert>  #pragma GCC diagnostic push #pragma GCC diagnostic ignored "-Weffc++" #pragma GCC diagnostic ignored "-Wunused-local-typedefs" #include <boost/shared_ptr.hpp> #include <QApplication> #include <QDialog> #include <QLabel> #include <QVBoxLayout> #pragma GCC diagnostic pop  int main(int argc, char *argv[]) {   QApplication a(argc, argv);    //Load the resource in a pixmap   const QPixmap pixmap(":/MyImages/BeerSmall.bmp");   assert(!pixmap.isNull() && "Assume bitmap is found");    //Put the pixmap in a label   boost::shared_ptr<QLabel> label(new QLabel);   label->setPixmap(pixmap);    //Add label in a layout   boost::shared_ptr<QVBoxLayout> layout(new QVBoxLayout);   layout->addWidget( label.get() );    //Create and show a window   boost::shared_ptr<QDialog> dialog(new QDialog);   dialog->setLayout(layout.get());   dialog->show();    return a.exec(); }`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


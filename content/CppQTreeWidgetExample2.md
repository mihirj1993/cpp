
 

 

 

 

 

([C++](Cpp.md)) ![Qt](PicQt.png) [QTreeWidgetExample2](CppQTreeWidgetExample2.md)
===================================================================================

 

[QTreeWidgetExample2](CppQTreeWidgetExample2.md) is an example of
[QTreeWidgetExample2](CppQTreeWidgetExample2.md).

 

-   [View a screenshot of
    'CppQTreeWidgetExample2' (png)](CppQTreeWidgetExample2.png)
-   ![Qt Creator](PicQtCreator.png) [Download the Qt Creator project
    'CppQTreeWidgetExample2' (zip)](CppQTreeWidgetExample2.zip)

 

 

 

 

 

Technical facts
---------------

 

[Application type(s)](CppApplication.md)

-   ![Desktop](PicDesktop.png) [Desktop
    application](CppDesktopApplication.md)

[Operating system(s) or programming environment(s)](CppOs.md)

-   ![Lubuntu](PicLubuntu.png) [Lubuntu](CppLubuntu.md) 12.10 (quantal)

[IDE(s)](CppIde.md):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.md) 2.5.2

[Project type](CppQtProjectType.md):

-   ![GUI](PicGui.png) [GUI application](CppGuiApplication.md)

[C++ standard](CppStandard.md):

-   ![C++98](PicCpp98.png) [C++98](Cpp98.md)

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.7.2

[Libraries](CppLibrary.md) used:

-   ![Qt](PicQt.png) [Qt](CppQt.md): version 4.8.3 (32 bit)
-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.7.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): CppQTreeWidgetExample2.pro
-------------------------------------------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` QT       += core gui greaterThan(QT_MAJOR_VERSION, 4): QT += widgets TARGET = CppQTreeWidgetExample2 TEMPLATE = app SOURCES += main.cpp HEADERS  += FORMS    += `
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

main.cpp
--------

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <QApplication> #include <QTreeWidget> #include <QTreeWidgetItem>  int main(int argc, char *argv[]) {   QApplication a(argc, argv);   QTreeWidget w;    //Hide the header   w.setHeaderHidden(true);    //Add five items   for (int i=0; i!=5; ++i)   {     QTreeWidgetItem * const item = new QTreeWidgetItem;     item->setText(0,QString::number(i));     w.addTopLevelItem(item);   }    //Let the row colors alternate   w.setAlternatingRowColors(true);    //Allow items to be drag and dropped inside of the widget   w.setDragDropMode(QAbstractItemView::InternalMove);    //Let the drag and drop be animated   w.setAnimated(true);     w.show();   return a.exec(); } `
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


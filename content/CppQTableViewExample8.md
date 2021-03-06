
 

 

 

 

 

([C++](Cpp.md)) [QTableViewExample8](CppQTableViewExample8.md)
================================================================

 

![Qt](PicQt.png)![Qt
Creator](PicQtCreator.png)![Lubuntu](PicLubuntu.png)

 

[QTableView example 8: table with checkboxes and editable text using a
custom model](CppQTableViewExample8.md) is a
[QTableView](CppQTableView.md) [example](CppExample.md).

 

-   [View a screenshot of
    'QTableViewExample8' (png)](CppQTableViewExample8.png)
-   [Download the Qt Creator project
    'QTableViewExample8' (zip)](CppQTableViewExample8.zip)

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

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): ./CppQTableViewExample8/CppQTableViewExample8.pro
------------------------------------------------------------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` QT       += core gui greaterThan(QT_MAJOR_VERSION, 4): QT += widgets TEMPLATE = app QMAKE_CXXFLAGS += -std=c++11 SOURCES += \     qtdialog.cpp \     qtmain.cpp \     mymodel.cpp  HEADERS  += qtdialog.h \     mymodel.h  FORMS    += qtdialog.ui`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQTableViewExample8/mymodel.h
---------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef MYMODEL_H #define MYMODEL_H  //#include <QAbstractTableModel> #include <QStandardItemModel>  struct MyModel : public QStandardItemModel { public:   MyModel(QObject *parent = 0);   void AddRow();  private: };  #endif // MYMODEL_H`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQTableViewExample8/mymodel.cpp
-----------------------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "mymodel.h"  #include <cassert>  MyModel::MyModel(QObject *parent)   : QStandardItemModel(parent) {   setColumnCount(3);   setHeaderData(0,Qt::Horizontal,"Y");   setHeaderData(1,Qt::Horizontal,"N");   setHeaderData(2,Qt::Horizontal,"Question");   for (int i=0; i!=5; ++i) AddRow(); }  void MyModel::AddRow() {   QList<QStandardItem*> items;   //Add 'yes' checkbox   {     QStandardItem * const item = new QStandardItem;     item->setCheckable(true);     item->setEditable(false);     item->setCheckState(Qt::Unchecked);     items.push_back(item);   }   //Add 'no' checkbox   {     QStandardItem * const item = new QStandardItem;     item->setCheckable(true);     item->setEditable(false);     item->setCheckState(Qt::Unchecked);     items.push_back(item);   }   //Add 'yes' checkbox   {     QStandardItem * const item = new QStandardItem;     item->setEditable(true);     item->setText("Is this a useful question?");     items.push_back(item);   }    assert(columnCount() == items.size());   appendRow(items);   emit layoutChanged(); }`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQTableViewExample8/qtdialog.h
----------------------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef QTDIALOG_H #define QTDIALOG_H  #include <QDialog>  namespace Ui {   class QtDialog; }  struct QStandardItemModel;  class QtDialog : public QDialog {   Q_OBJECT    public:   explicit QtDialog(QWidget *parent = 0);   ~QtDialog();    private slots:   void on_button_clicked();  private:   Ui::QtDialog *ui; };  #endif // QTDIALOG_H`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQTableViewExample8/qtdialog.cpp
------------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "qtdialog.h"  #include <cassert>  #include "mymodel.h" #include "ui_qtdialog.h"  QtDialog::QtDialog(QWidget *parent) :   QDialog(parent),   ui(new Ui::QtDialog) {   ui->setupUi(this);    assert(!ui->table->model());   ui->table->setModel(new MyModel(this));   assert( ui->table->model());     ui->table->setColumnWidth(0, 24);   ui->table->setColumnWidth(1, 24);   ui->table->setColumnWidth(2,175); }  QtDialog::~QtDialog() {   delete ui; }  void QtDialog::on_button_clicked() {   dynamic_cast<MyModel*>(ui->table->model())->AddRow();   ui->table->scrollToBottom();   const int n_rows = ui->table->model()->rowCount();   ui->table->setCurrentIndex(ui->table->model()->index(n_rows-1,2)); }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

./CppQTableViewExample8/qtmain.cpp
----------------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <QApplication> #include "qtdialog.h"  int main(int argc, char *argv[]) {   QApplication a(argc, argv);   QtDialog w;   w.show();   return a.exec(); }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


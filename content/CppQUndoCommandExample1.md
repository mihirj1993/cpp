# ([C++](Cpp.md)) ![Qt](PicQt.png) [QUndoCommand example 1](CppQUndoCommandExample1.md)

[QUndoCommand example 1](CppQUndoCommandExample1.md) is a
[QUndoCommand](CppQUndoCommand.md) example.

![View a screenshot of 'CppQUndoCommandExample1' (png)](CppQUndoCommandExample1.png)/

 * [Download the Qt Creator project 'CppQUndoCommandExample1' (zip)](CppQUndoCommandExample1.zip)

## Technical facts

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

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): CppQUndoCommandExample1.pro
--------------------------------------------------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #------------------------------------------------- # # Project created by QtCreator 2013-04-21T19:59:08 # #-------------------------------------------------  QT       += core gui  greaterThan(QT_MAJOR_VERSION, 4): QT += widgets  TARGET = CppQUndoCommandExample1 TEMPLATE = app   SOURCES += main.cpp\         qtdialog.cpp \     qtbuttonincrementcommand.cpp  HEADERS  += qtdialog.h \     qtbuttonincrementcommand.h  FORMS    += qtdialog.ui`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

main.cpp
--------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <QApplication> #include "qtdialog.h"  int main(int argc, char *argv[]) {   QApplication a(argc, argv);   QtDialog w;   w.show();      return a.exec(); }`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

qtbuttonincrementcommand.h
--------------------------

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef QTBUTTONINCREMENTCOMMAND_H #define QTBUTTONINCREMENTCOMMAND_H  #include <QUndoCommand>  struct QPushButton;  struct QtButtonIncrementCommand : public QUndoCommand {   explicit QtButtonIncrementCommand(QPushButton * const button);    ///Virtual function supplied by QUndoCommand   void redo();    ///Virtual function supplied by QUndoCommand   void undo();    private:   QPushButton * const m_button;  };  #endif // QTBUTTONINCREMENTCOMMAND_H`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

qtbuttonincrementcommand.cpp
----------------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "qtbuttonincrementcommand.h"  #include <cassert> #include <QPushButton>  QtButtonIncrementCommand::QtButtonIncrementCommand(   QPushButton * const button)   : m_button(button) {   assert(m_button); }  void QtButtonIncrementCommand::redo() {   const int current_number = m_button->text().toInt();   const int new_number = current_number + 1;   m_button->setText(QString::number(new_number) ); }  void QtButtonIncrementCommand::undo() {   const int current_number = m_button->text().toInt();   const int new_number = current_number - 1;   m_button->setText(QString::number(new_number) ); }`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

qtdialog.h
----------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef QTDIALOG_H #define QTDIALOG_H  #include <QDialog>  namespace Ui {   class QtDialog; }  struct QUndoStack;  class QtDialog : public QDialog {   Q_OBJECT    public:   explicit QtDialog(QWidget *parent = 0);   ~QtDialog();      private slots:   void keyPressEvent(QKeyEvent *);   void on_button_clicked();  private:   Ui::QtDialog *ui;    QUndoStack * const m_stack; };  #endif // QTDIALOG_H`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

qtdialog.cpp
------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "qtdialog.h"  #include <QKeyEvent> #include <QUndoStack> #include "qtbuttonincrementcommand.h"  #include "ui_qtdialog.h"  QtDialog::QtDialog(QWidget *parent) :   QDialog(parent),   ui(new Ui::QtDialog),   m_stack(new QUndoStack(this)) {   ui->setupUi(this); }  QtDialog::~QtDialog() {   delete ui; }  void QtDialog::keyPressEvent(QKeyEvent * e) {   if ( (e->modifiers() & Qt::ControlModifier)     && !(e->modifiers() & Qt::ShiftModifier)     && e->key() == Qt::Key_Z)   {     m_stack->undo();   }   if ( (e->modifiers() & Qt::ControlModifier)     && (e->modifiers() & Qt::ShiftModifier)     && e->key() == Qt::Key_Z)   {     m_stack->redo();   } }  void QtDialog::on_button_clicked() {   QtButtonIncrementCommand * const cmd     = new QtButtonIncrementCommand(ui->button);    //By pushing the command, redo is called   m_stack->push(cmd); }`
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

 


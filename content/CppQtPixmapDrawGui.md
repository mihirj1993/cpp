
 

 

 

 

 

([C++](Cpp.md) [Qt Creator](CppQtCreator.md)) [How to draw on a QPixmap with using the GUI designer?](CppQtPixmapDrawGui.md)
===============================================================================================================================

 

This page describes how to draw on a QPixmap with using the GUI
designer, resulting in [this screenshot](CppQtPixmapDrawGui.png). You
can also directly [download the CppQtPixmapDrawGui source and binary
code](CppQtPixmapDrawGui.zip).

 

To create this program in [Qt Creator](CppQtCreator.md), you can follow
the steps below:

-   Step \#1: Setting up the Qt4 Gui application project
-   Step \#2: Setting up the GUI
-   Step \#3: Coding the [declarations](CppDeclaration.md) of the
    dialog
-   Step \#4: Coding the [definitions](CppDefinition.md) of the dialog
-   Step \#5: Running the program

 

 

 

 

 

Step \#1: Setting up the Qt4 Gui application project
----------------------------------------------------

 

1.  Start [Qt Creator](CppQtCreator.md).
2.  If you are not shown the welcome screen, click on 'Welcome' on the
    left
3.  If, in the welcome screen, the 'Develop' tab is not shown, click on
    'Develop' to view the [Welcome screen Develop
    tab](CppQtCreatorWelcomeDevelop_2_1_0.png)
4.  In the [Welcome screen Develop
    tab](CppQtCreatorWelcomeDevelop_2_1_0.png), click 'Create New
    Project' to go to the [New project
    dialog](CppQtCreatorNewProject_2_5_2.png)
5.  In the [New project dialog](CppQtCreatorNewProject_2_5_2.png), click
    'QT4 Gui Application' to go to the [introduction and project
    location dialog](CppQtIntroduction.png)
6.  In the [Introduction and project location
    dialog](CppQtIntroduction.png), you must specify a name and location
    to save your (project) files. For example, after 'Name'
    type 'HelloWorldGui'. Click next
7.  In the [select required modules
    dialog](CppQtCreatorSelectRequiredModules.png), all checks are
    correct (only QtCore and QtGui are checked), so click 'Next'
8.  In the [class Information dialog](CppQtClassInformation.png), change
    the 'Base class' to 'QDialog' and click 'Next'
9.  In the [project management dialog](CppQtProjectManagement.png),
    click 'Finish'

 

Now your Qt4 Gui application project is successfully set up. Your screen
might look like [this](CppQtHelloWorldWindowedGui1.png).

 

 

 

 

 

Step \#2: Setting up the GUI
----------------------------

 

1.  On the left menu bar, you can see you are now in 'Edit' mode
    (instead of 'Welcome' mode). You can see your project right of this
    menu bar. You can see a 'QtHelloWorldGui' project folder, containing
    the following files:
    1.  QtHelloWorldGui.pro
    2.  main.cpp
    3.  dialog.cpp
    4.  dialog.h
    5.  dialog.ui

    Double-click on 'dialog.ui' to be taken to the GUI designer.
2.  Your screen might then look like
    [this](CppQtHelloWorldWindowedGui2.png). I prefer to press 'Alt-0'
    to remove the Project manager sidebar and my screen looks like
    [this](CppQtHelloWorldWindowedGui3.png).
3.  From the Widget toolbox, place a PushButton (under 'Buttons') and
    Label (under 'Display Widgets') on the MainWindow.
4.  Click on the PushButton and change the Text property to 'Invert
    colors', like [this screenshot](CppQtPixmapDrawGui2.png).
5.  Click on the Label and change the Pixmap property to 'Choose file'
    and select an image like [256x256.png](256x256.png), like [this
    screenshot](CppQtPixmapDrawGui3.png).
6.  Right-click on the Dialog and select 'Layout -&gt; Lay
    out vertically'.
7.  Right-click on the Dialog and select 'Size contraints -&gt; Set
    minimum size'.

 

You have now successfully set up the GUI. Your screen might then look
like [this](CppQtPixmapDrawGui4.png).

 

 

 

 

 

Step \#3: Coding the [declarations](CppDeclaration.md) of the dialog
---------------------------------------------------------------------

 

1.  Press 'ALT-0' to view the Project Manager sidebar again. Your screen
    might then look like [this](CppQtHelloWorldWindowedGui5.png).
2.  Double-click on 'dialog.h to be taken to the source of dialog.h:
      ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      `     #ifndef DIALOG_H     #define DIALOG_H          namespace Ui {       class Dialog;     }          class Dialog : public QDialog {       Q_OBJECT     public:       Dialog(QWidget *parent = 0);       ~Dialog();          protected:       void changeEvent(QEvent *e);          private:       Ui::Dialog *ui;     };     #endif // DIALOG_H     `
      ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

3.  Change this code to the following:
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      `     #ifndef DIALOG_H     #define DIALOG_H          #include <QDialog>     #include <QPainter>     #include <QPixmap>     #include <QTimer>          namespace Ui {       class Dialog;     }          class Dialog : public QDialog {       Q_OBJECT     public:       Dialog(QWidget *parent = 0);       ~Dialog();          protected:       void changeEvent(QEvent *e);          private slots:       void OnClick();       void OnTick();          private:       Ui::Dialog *ui;       QPixmap m_pixmap;       QPainter m_painter;       int m_z;       QTimer m_timer;     };          #endif // DIALOG_H     `
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Note that if you try to execute the program, you get the following
[(link) error](CppLinkError.md):

  -----------------------------------------------------------------------------------------------------------------------------------------------------------
  ` /MyFolder/moc_mainwindow.cpp:66: undefined reference to 'Dialog::OnClick()' /MyFolder/moc_mainwindow.cpp:66: undefined reference to 'Dialog::OnTick()'`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------

 

This [(link) error](CppLinkError.md) is correct: the [member
functions](CppMemberFunction.md) Dialog::OnClick and Dialog::OnTick are
[declared](CppDeclaration.md) but not yet [defined](CppDefinition.md).

 

 

 

 

 

Step \#4: Coding the [definitions](CppDefinition.md) of the dialog
-------------------------------------------------------------------

 

1.  Press 'ALT-0' to view the Project Manager sidebar again. Your screen
    might then look like [this](CppQtHelloWorldWindowedGui6.png).
2.  Double-click on 'dialog.cpp to be taken to the source of dialog.cpp:
      ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      `     #include "dialog.h"     #include "ui_dialog.h"          Dialog::Dialog(QWidget *parent) :         QDialog(parent),         ui(new Ui::Dialog)     {       ui->setupUi(this);     }          Dialog::~Dialog()     {       delete ui;     }          void Dialog::changeEvent(QEvent *e)     {       QDialog::changeEvent(e);       switch (e->type()) {       case QEvent::LanguageChange:         ui->retranslateUi(this);         break;       default:         break;       }     }     `
      ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

3.  Change this code to the following:
      ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      `     #include <QPainter>          #include "dialog.h"     #include "ui_dialog.h"          Dialog::Dialog(QWidget *parent) :         QDialog(parent),         ui(new Ui::Dialog),         m_pixmap("256x256.png"),         m_painter(&m_pixmap),         m_z(0)     {       ui->setupUi(this);       assert(QFile::exists("256x256.png") && "Please put a file called 256x256.png in the executable its folder");       QObject::connect(ui->pushButton,SIGNAL(clicked()),this,SLOT(OnClick()));       QObject::connect(&m_timer,SIGNAL(timeout()),this,SLOT(OnTick()));       OnTick();       m_timer.start(10);     }          Dialog::~Dialog()     {       delete ui;     }          void Dialog::changeEvent(QEvent *e)     {       QDialog::changeEvent(e);       switch (e->type()) {       case QEvent::LanguageChange:         ui->retranslateUi(this);         break;       default:         break;       }     }          void Dialog::OnTick()     {       ++m_z;       for (int x = 0; x!=256; ++x)       {         for (int y = 0; y!=256; ++y)         {           m_painter.setPen(QColor((m_z+x)%256,(m_z+y)%256,(m_z+x+y)%256));           m_painter.drawPoint(x,y);         }       }       ui->label->setPixmap(m_pixmap);     }          void Dialog::OnClick()     {       m_z+=128;     }     `
      ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Step \#5: Running the program
-----------------------------

 

1.  Press CTRL-R to start the program
2.  Your screen might then look like [this](CppQtPixmapDrawGui.png)

 

 

 

 

 

 


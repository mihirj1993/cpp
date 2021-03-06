
 

 

 

 

 

([C++](Cpp.md)) [Wt example 1](CppWtExample1.md)
==================================================

 

[Wt example 1](CppWtExample1.md) is a [Wt](CppWt.md) example to code
and display a simple menu.

 

 

 

 

 

Downloads
---------

 

-   [View a screenshot of 'Wt example 1' (png)](CppWtExample1.png)
-   [Download the 'Wt example 1' source code (zip)](CppWtExample1.zip)

 

 

 

 

 

[Operating system(s) or programming environment(s)](CppOs.md)
--------------------------------------------------------------

 

-   ![Ubuntu](PicUbuntu.png) [Ubuntu](CppUbuntu.md) 10.10 (maverick)

[IDE(s)](CppIde.md):

-   ![Qt Creator](PicQtCreator.png) [Qt Creator](CppQtCreator.md) 2.0.0

[Project type](CppQtProjectType.md):

-   ![console](PicConsole.png) Console application

[Compiler(s)](CppCompiler.md):

-   [G++](CppGpp.md) 4.4.5

[Libraries](CppLibrary.md) used:

-   ![STL](PicStl.png) [STL](CppStl.md): GNU ISO C++ Library, version
    4.4.5
-   ![Wt](PicWt.png) [Wt](CppWt.md): version 3.1.2

 

 

 

 

 

[Qt project file](CppQtProjectFile.md): CppWtMenu.pro
------------------------------------------------------

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #------------------------------------------------- # # Project created by QtCreator 2010-12-14T12:41:04 # #------------------------------------------------- QT       += core QT       -= gui LIBS += -lwt -lwthttp QMAKE_CXXFLAGS += -DNDEBUG TARGET = CppWtMenu CONFIG   += console CONFIG   -= app_bundle TEMPLATE = app SOURCES += main.cpp \     menuapplication.cpp \     menuwidget.cpp HEADERS += \     menuapplication.h \     menuwidget.h`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

main.cpp
--------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //--------------------------------------------------------------------------- #include <Wt/WApplication> #include "menuapplication.h" //--------------------------------------------------------------------------- Wt::WApplication *createApplication(   const Wt::WEnvironment& env) {   return new MenuApplication(env); } //--------------------------------------------------------------------------- int main(int argc, char **argv) {   return WRun(argc, argv, &createApplication); } //--------------------------------------------------------------------------- `
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

menuapplication.cpp
-------------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include "menuapplication.h" #include "menuwidget.h" //--------------------------------------------------------------------------- MenuApplication::MenuApplication(const Wt::WEnvironment& env)   : Wt::WApplication(env),     m_menu(new MenuWidget) {   this->setTitle(__TIME__);   root()->addWidget(m_menu); } //--------------------------------------------------------------------------- `
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

menuapplication.h
-----------------

 

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef MENUAPPLICATION_H #define MENUAPPLICATION_H //--------------------------------------------------------------------------- #include <Wt/WApplication> //--------------------------------------------------------------------------- struct MenuWidget; //--------------------------------------------------------------------------- struct MenuApplication : public Wt::WApplication {   MenuApplication(const Wt::WEnvironment& env);   private:   //All pointers are managed by Wt   MenuWidget * const m_menu; }; //--------------------------------------------------------------------------- #endif // MENUAPPLICATION_H `
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

menuwidget.cpp
--------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` //--------------------------------------------------------------------------- #include <ctime> #include <string> //--------------------------------------------------------------------------- #include <Wt/WPushButton> #include <Wt/WVBoxLayout> #include "menuwidget.h" //--------------------------------------------------------------------------- MenuWidget::MenuWidget()   : m_button1(new Wt::WPushButton),     m_button2(new Wt::WPushButton),     m_button3(new Wt::WPushButton),     m_layout(new Wt::WVBoxLayout(this)) {   m_layout->setContentsMargins(0,0,0,0);   m_layout->setSpacing(0);   m_layout->addWidget(m_button1);   m_layout->addWidget(m_button2);   m_layout->addWidget(m_button3);    m_button1->setText("Button one");   m_button2->setText("Button two");   m_button3->setText("Button three");    this->resize(200,Wt::WLength::Auto);    m_button1->clicked().connect(this, &MenuWidget::onButton1Click);   m_button2->clicked().connect(this, &MenuWidget::onButton2Click);   m_button3->clicked().connect(this, &MenuWidget::onButton3Click); } //--------------------------------------------------------------------------- void MenuWidget::onButton1Click() {   m_button1->setText( GetTime() ); } //--------------------------------------------------------------------------- void MenuWidget::onButton2Click() {   m_button2->setText( GetTime() ); } //--------------------------------------------------------------------------- void MenuWidget::onButton3Click() {   m_button3->setText( GetTime() ); } //--------------------------------------------------------------------------- ///TimeToStr converts std::time_t to std::string. ///From http://www.richelbilderbeek.nl/CppTimeToStr.htm const std::string TimeToStr(const std::time_t& time) {   return std::ctime( &time); } //--------------------------------------------------------------------------- //From http://www.richelbilderbeek.nl/CppGetTime.htm std::time_t GetTimeT() {   return std::time(0); } //--------------------------------------------------------------------------- //From http://www.richelbilderbeek.nl/CppGetTime.htm const std::string GetTime() {   return TimeToStr(GetTimeT()); } //--------------------------------------------------------------------------- `
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

menuwidget.h
------------

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #ifndef MENUWIDGET_H #define MENUWIDGET_H //--------------------------------------------------------------------------- #include <Wt/WContainerWidget> //--------------------------------------------------------------------------- namespace Wt {   struct WPushButton;   struct WVBoxLayout; }; //--------------------------------------------------------------------------- struct MenuWidget : public Wt::WContainerWidget {   MenuWidget();    private:   //All pointers are managed by Wt   Wt::WPushButton * const m_button1;   Wt::WPushButton * const m_button2;   Wt::WPushButton * const m_button3;   Wt::WVBoxLayout * const m_layout;    private slots:   void onButton1Click();   void onButton2Click();   void onButton3Click(); }; //--------------------------------------------------------------------------- //From http://www.richelbilderbeek.nl/CppGetTime.htm const std::string GetTime(); //--------------------------------------------------------------------------- #endif // MENUWIDGET_H `
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Additional preparations
-----------------------

 

Added the following arguments to the [Run
Settings](CppQtCreatorRunSettings.png):

 

  --------------------------------------------------------
  ` --docroot . --http-address 0.0.0.0 --http-port 8080`
  --------------------------------------------------------

 

 

 

 

 

[Deploying the Wt application locally](CppWtDeployLocal.md)
------------------------------------------------------------

 

When running the program (from Qt Creator) you will see the following
application output, indicating that the program works fine:

 

  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` [2010-Nov-19 16:41:38.365920] 6360 - [notice] "Wt: initializing built-in httpd" [2010-Nov-19 16:41:38.366043] 6360 - [notice] "Reading Wt config file: /etc/wt/wt_config.xml (location = '/home/richel/qtsdk-2010.04/bin/Projects/Website/CppWtExample1-build-desktop/CppWtExample1')" [2010-Nov-19 16:41:38.366592] 6360 - [notice] "Started server: http://0.0.0.0:8080"`
  -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

Now, start your web browser and go to the following address:

 

  ---------------------------
  ` http://127.0.0.1:8080/`
  ---------------------------

 

You will see the 'Hello Wt' dynamic website. You just [deployed your Wt
application locally](CppWtDeployLocal.md). This is just fine for
debugging. If the application is ready to be put on the web, [deploy the
Wt application globally](CppWtDeployGlobal.md).

 

 

 

 

 

 


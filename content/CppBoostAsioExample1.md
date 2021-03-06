
 

 

 

 

 

([C++](Cpp.md)) [Asio example 1: a chat server](CppAsioExample1.md)
=====================================================================

 

This [Asio](CppBoostAsio.md) example shows how to create a chat server.

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` This example has been copied literally from  http://www.boost.org/doc/libs/1_38_0/doc/html/boost_asio/examples.html . The purpose of this example is to convert the source code to a compiling project.`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

-   [Download the Qt Project of
    'AsioExample1' (zip)](CppAsioExample1.zip)

 

Operating system:
[Ubuntu](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)

[IDE](CppIde.md): [Qt Creator](CppQt.md) 2.0.0

[Project type](CppQtProjectType.md): Qt4 Console Application

[Compiler](CppCompiler.md): [G++](CppGpp.md) 4.4.1

[Libraries](CppLibrary.md) used:

-   [Boost](CppBoost.md): version 1.40
-   [STL](CppStl.md): from [GCC](CppGcc.md), shipped with [Qt
    Creator](CppQt.md) 2.0.0
-   [Qt](CppQt.md): version 4.7.0 (32 bit)

 

 

 

 

 

[Qt project file](CppQtProjectFile.md)
---------------------------------------

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #------------------------------------------------- # # Project created by QtCreator 2010-07-21T19:37:18 # #------------------------------------------------- QT       += core QT       -= gui TARGET = CppAsioExample1 CONFIG   += console CONFIG   -= app_bundle TEMPLATE = app SOURCES += main.cpp LIBS += -L/usr/local/lib -lboost_system HEADERS += \     chat_server.h \     chat_message.h`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Source code
-----------

 

 

 

 

 

### chat\_message.h

 

  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` // // chat_message.hpp // ~~~~~~~~~~~~~~~~ // // Copyright (c) 2003-2010 Christopher M. Kohlhoff (chris at kohlhoff dot com) // // Distributed under the Boost Software License, Version 1.0. (See accompanying // file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt) //  #ifndef CHAT_MESSAGE_HPP #define CHAT_MESSAGE_HPP  #include <cstdio> #include <cstdlib> #include <cstring>  class chat_message { public:   enum { header_length = 4 };   enum { max_body_length = 512 };    chat_message()     : body_length_(0)   {   }    const char* data() const   {     return data_;   }    char* data()   {     return data_;   }    size_t length() const   {     return header_length + body_length_;   }    const char* body() const   {     return data_ + header_length;   }    char* body()   {     return data_ + header_length;   }    size_t body_length() const   {     return body_length_;   }    void body_length(size_t length)   {     body_length_ = length;     if (body_length_ > max_body_length)       body_length_ = max_body_length;   }    bool decode_header()   {     using namespace std; // For strncat and atoi.     char header[header_length + 1] = "";     strncat(header, data_, header_length);     body_length_ = atoi(header);     if (body_length_ > max_body_length)     {       body_length_ = 0;       return false;     }     return true;   }    void encode_header()   {     using namespace std; // For sprintf and memcpy.     char header[header_length + 1] = "";     sprintf(header, "%4d", body_length_);     memcpy(data_, header, header_length);   }  private:   char data_[header_length + max_body_length];   size_t body_length_; };  #endif // CHAT_MESSAGE_HPP`
  -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

### chat\_server.h

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` // // chat_server.cpp // ~~~~~~~~~~~~~~~ // // Copyright (c) 2003-2010 Christopher M. Kohlhoff (chris at kohlhoff dot com) // // Distributed under the Boost Software License, Version 1.0. (See accompanying // file LICENSE_1_0.txt or copy at http://www.boost.org/LICENSE_1_0.txt) //  #include <algorithm> #include <cstdlib> #include <deque> //#include <iostream> #include <list> #include <set> #include <boost/bind.hpp> #include <boost/shared_ptr.hpp> #include <boost/enable_shared_from_this.hpp> #include <boost/asio.hpp> #include "chat_message.h"  using boost::asio::ip::tcp;  //----------------------------------------------------------------------  typedef std::deque<chat_message> chat_message_queue;  //----------------------------------------------------------------------  class chat_participant { public:   virtual ~chat_participant() {}   virtual void deliver(const chat_message& msg) = 0; };  typedef boost::shared_ptr<chat_participant> chat_participant_ptr;  //----------------------------------------------------------------------  class chat_room { public:   void join(chat_participant_ptr participant)   {     participants_.insert(participant);     std::for_each(recent_msgs_.begin(), recent_msgs_.end(),         boost::bind(&chat_participant::deliver, participant, _1));   }    void leave(chat_participant_ptr participant)   {     participants_.erase(participant);   }    void deliver(const chat_message& msg)   {     recent_msgs_.push_back(msg);     while (recent_msgs_.size() > max_recent_msgs)       recent_msgs_.pop_front();      std::for_each(participants_.begin(), participants_.end(),         boost::bind(&chat_participant::deliver, _1, boost::ref(msg)));   }  private:   std::set<chat_participant_ptr> participants_;   enum { max_recent_msgs = 100 };   chat_message_queue recent_msgs_; };  //----------------------------------------------------------------------  class chat_session   : public chat_participant,     public boost::enable_shared_from_this<chat_session> { public:   chat_session(boost::asio::io_service& io_service, chat_room& room)     : socket_(io_service),       room_(room)   {   }    tcp::socket& socket()   {     return socket_;   }    void start()   {     room_.join(shared_from_this());     boost::asio::async_read(socket_,         boost::asio::buffer(read_msg_.data(), chat_message::header_length),         boost::bind(           &chat_session::handle_read_header, shared_from_this(),           boost::asio::placeholders::error));   }    void deliver(const chat_message& msg)   {     bool write_in_progress = !write_msgs_.empty();     write_msgs_.push_back(msg);     if (!write_in_progress)     {       boost::asio::async_write(socket_,           boost::asio::buffer(write_msgs_.front().data(),             write_msgs_.front().length()),           boost::bind(&chat_session::handle_write, shared_from_this(),             boost::asio::placeholders::error));     }   }    void handle_read_header(const boost::system::error_code& error)   {     if (!error && read_msg_.decode_header())     {       boost::asio::async_read(socket_,           boost::asio::buffer(read_msg_.body(), read_msg_.body_length()),           boost::bind(&chat_session::handle_read_body, shared_from_this(),             boost::asio::placeholders::error));     }     else     {       room_.leave(shared_from_this());     }   }    void handle_read_body(const boost::system::error_code& error)   {     if (!error)     {       room_.deliver(read_msg_);       boost::asio::async_read(socket_,           boost::asio::buffer(read_msg_.data(), chat_message::header_length),           boost::bind(&chat_session::handle_read_header, shared_from_this(),             boost::asio::placeholders::error));     }     else     {       room_.leave(shared_from_this());     }   }    void handle_write(const boost::system::error_code& error)   {     if (!error)     {       write_msgs_.pop_front();       if (!write_msgs_.empty())       {         boost::asio::async_write(socket_,             boost::asio::buffer(write_msgs_.front().data(),               write_msgs_.front().length()),             boost::bind(&chat_session::handle_write, shared_from_this(),               boost::asio::placeholders::error));       }     }     else     {       room_.leave(shared_from_this());     }   }  private:   tcp::socket socket_;   chat_room& room_;   chat_message read_msg_;   chat_message_queue write_msgs_; };  typedef boost::shared_ptr<chat_session> chat_session_ptr;  //----------------------------------------------------------------------  class chat_server { public:   chat_server(boost::asio::io_service& io_service,       const tcp::endpoint& endpoint)     : io_service_(io_service),       acceptor_(io_service, endpoint)   {     chat_session_ptr new_session(new chat_session(io_service_, room_));     acceptor_.async_accept(new_session->socket(),         boost::bind(&chat_server::handle_accept, this, new_session,           boost::asio::placeholders::error));   }    void handle_accept(chat_session_ptr session,       const boost::system::error_code& error)   {     if (!error)     {       session->start();       chat_session_ptr new_session(new chat_session(io_service_, room_));       acceptor_.async_accept(new_session->socket(),           boost::bind(&chat_server::handle_accept, this, new_session,             boost::asio::placeholders::error));     }   }  private:   boost::asio::io_service& io_service_;   tcp::acceptor acceptor_;   chat_room room_; };  typedef boost::shared_ptr<chat_server> chat_server_ptr; typedef std::list<chat_server_ptr> chat_server_list;  //----------------------------------------------------------------------`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

### main.cpp

 

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` #include <iostream> #include <boost/asio.hpp> #include <QtCore/QCoreApplication> #include "chat_message.h" #include "chat_server.h"  int main(int argc, char* argv[]) {   try   {     if (argc < 2)     {       std::cerr << "Usage: chat_server <port> [<port> ...]\n";       return 1;     }      boost::asio::io_service io_service;      chat_server_list servers;     for (int i = 1; i < argc; ++i)     {       using namespace std; // For atoi.       tcp::endpoint endpoint(tcp::v4(), atoi(argv[i]));       chat_server_ptr server(new chat_server(io_service, endpoint));       servers.push_back(server);     }      io_service.run();   }   catch (std::exception& e)   {     std::cerr << "Exception: " << e.what() << "\n";   }    return 0; }`
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

 

 

 

 

Getting the chat program to work
--------------------------------

 

For the chat program to work, you need the executables from both [Asio
example 1: a chat server](CppAsioExample1.md) and [Asio example 2: a
chat client](CppAsioExample2.md).

 

First start the server. For the chat program I decided to use port 6660
(due to [this Wikipedia
page](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)).
The server cannot be used to send messages.

 

  ---------------------------
  ` ./CppAsioExample1 6660`
  ---------------------------

 

Now we need to start two clients. The clients are used to send messages.
I used two computers from my router (LAN?) network. The computer I
started the server on had the IP adress 192.168.23.100. Start two
clients with the code below, possibly on different computers.

 

  ------------------------------------------
  ` ./CppAsioExample2 192.168.23.100 6660`
  ------------------------------------------

 

While chatting, the server must keep running.

 

 

 

 

 

 



 

 

 

 

 

([C++](Cpp.md)) [git](CppGit.md)
==================================

 

[Git](CppGit.md) is a version control system.

 

[Git](CppGit.md) is supplied with [Qt Creator](CppQtCreator.md).

 

I use [GitHub](CppGitHub.md) as an online host to my [Git](CppGit.md)
repository (see external links).

 

 

 

 

 

[Git](CppGit.md) errors (when using it under Qt Creator)
---------------------------------------------------------

 

I have not gotten git to work. After starting a project managed by git,
I got this:

 

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` Perforce: Unable to determine the repository: Unable to launch "p4": No such file or directory  13:17 Executing: git init Unable to execute 'git': No such file or directory:`
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

So, I started a terminal:

 

  ---------------------------------------------------------------------------------------------------------------------------------------------
  ` richel@richel1-desktop:~$ git The program 'git' is currently not installed.  You can install it by typing: sudo apt-get install git-core`
  ---------------------------------------------------------------------------------------------------------------------------------------------

 

Following this instructions, installed git.

 

But p4 did not work:

 

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  ` Perforce: Unable to determine the repository: Unable to launch "p4": No such file or directory  13:22 Executing: git init Initialized empty Git repository in /home/richel/qtsdk-2010.04/bin/Projects/Website/CppGitExample1/.git/  13:22 Executing: git --version  13:22 Executing: git add --intent-to-add main.cpp  13:22 Executing: git add --intent-to-add CppGitExample1.pro`
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 

p4 can be downloaded from
http://www.perforce.com/perforce/downloads/index.html but I did not
succeed in installing it: there was no installation file within the
download.

 

 

 

 

 

External links
--------------

 

-   [My GitHub
    repository](http://github.com/richelbilderbeek/ProjectRichelBilderbeek)
-   [A successful Git branching
    policy](http://nvie.com/posts/a-successful-git-branching-model):
    article that describes a policy of using Git

 

 

 

 

 

 


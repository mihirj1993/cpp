# ([C++](Cpp.md)) [EO install error: 'UINT\_MAX' was not declared in this scope](CppInstallErrorEoUint_maxWasNotDeclaredInThisScope.md)

[Install error](CppInstallError.md).

## Error description

Operating system: [Ubuntu](http://www.ubuntu.com) 10.04 LTS Lucid Lynx

Downloaded the [EO](CppEo.md) source code, version 1.0.1. Extracted the
files.

Start configure:

```
./configure
```

Screen output:

```
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking target system type... i686-pc-linux
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for ranlib... ranlib
checking for ar... /usr/bin/ar
checking for doxygen... doxygen
checking how to run the C++ preprocessor... g++ -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for uint32_t... yes
checking for size_t... yes
checking for cos in -lm... yes
checking use gnuplot for graphical display... (cached) yes
checking for gnuplot... gnuplot
configure: creating ./config.status
config.status: creating Makefile
config.status: creating app/Makefile
config.status: creating app/mastermind/Makefile
config.status: creating app/gprop/Makefile
config.status: creating app/gpsymreg/Makefile
config.status: creating contrib/Makefile
config.status: creating doc/Makefile
config.status: creating src/Makefile
config.status: creating src/do/Makefile
config.status: creating src/es/Makefile
config.status: creating src/gp/Makefile
config.status: creating src/ga/Makefile
config.status: creating src/other/Makefile
config.status: creating src/utils/Makefile
config.status: creating test/Makefile
config.status: creating tutorial/Makefile
config.status: creating tutorial/html/Makefile
config.status: creating tutorial/Lesson1/Makefile
config.status: creating tutorial/Lesson2/Makefile
config.status: creating tutorial/Lesson3/Makefile
config.status: creating tutorial/Lesson4/Makefile
config.status: creating tutorial/Lesson5/Makefile
config.status: creating tutorial/Templates/Makefile
config.status: creating tutorial/pdf/Makefile
config.status: creating win/Makefile
config.status: creating config.h
config.status: executing depfiles commands
```

Start make:

```
make
```

Screen output:

```
make all-recursive
make[1]: Entering directory '/home/richel/Downloads/eo-1.0.1'
Making all in src
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
Making all in es
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/es'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_algo_scalar_es.o -MD -MP -MF ".deps/make_algo_scalar_es.Tpo" -c -o make_algo_scalar_es.o make_algo_scalar_es.cpp; \
then mv -f ".deps/make_algo_scalar_es.Tpo" ".deps/make_algo_scalar_es.Po"; else rm -f ".deps/make_algo_scalar_es.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_algo_scalar_real.o -MD -MP -MF ".deps/make_algo_scalar_real.Tpo" -c -o make_algo_scalar_real.o make_algo_scalar_real.cpp; \
then mv -f ".deps/make_algo_scalar_real.Tpo" ".deps/make_algo_scalar_real.Po"; else rm -f ".deps/make_algo_scalar_real.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_checkpoint_es.o -MD -MP -MF ".deps/make_checkpoint_es.Tpo" -c -o make_checkpoint_es.o make_checkpoint_es.cpp; \
then mv -f ".deps/make_checkpoint_es.Tpo" ".deps/make_checkpoint_es.Po"; else rm -f ".deps/make_checkpoint_es.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:34,
from make_checkpoint_es.cpp:44:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
In file included from make_checkpoint_es.cpp:44:
../../src/do/make_checkpoint.h: In function 'eoCheckPoint<EOTgt;& do_make_checkpoint(eoParser&, eoState&, eoEvalFuncCounter<EOT>&, eoContinue<EOT>&)’:
../../src/do/make_checkpoint.h:259: error: 'UINT_MAX’ was not declared in this scope
make[3]: *** [make_checkpoint_es.o] Error 1
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/es'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/richel/Downloads/eo-1.0.1'
make: *** [all] Error 2
richel@richel1-desktop:~/Downloads/eo-1.0.1$ make check
Making check in src
make[1]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
Making check in es
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/es'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_checkpoint_es.o -MD -MP -MF ".deps/make_checkpoint_es.Tpo" -c -o make_checkpoint_es.o make_checkpoint_es.cpp; \
then mv -f ".deps/make_checkpoint_es.Tpo" ".deps/make_checkpoint_es.Po"; else rm -f ".deps/make_checkpoint_es.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:34,
from make_checkpoint_es.cpp:44:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
In file included from make_checkpoint_es.cpp:44:
../../src/do/make_checkpoint.h: In function 'eoCheckPoint<EOTgt;& do_make_checkpoint(eoParser&, eoState&, eoEvalFuncCounter<EOT>&, eoContinue<EOT>&)’:
../../src/do/make_checkpoint.h:259: error: 'UINT_MAX’ was not declared in this scope
make[2]: *** [make_checkpoint_es.o] Error 1
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/es'
make[1]: *** [check-recursive] Error 1
make[1]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
make: *** [check-recursive] Error 1
```

I zoomed in on the following error:

```
../../src/do/make_checkpoint.h:259: error: 'UINT_MAX’ was not declared in this scope
```

I edited the file checkpoint.h by adding one line, shown below:

```
#ifndef _make_checkpoint_h
#define _make_checkpoint_h

#include <climits> //Added by RJCB
#include <eoScalarFitness.h>
#include <utils/selectors.h> // for minimizing_fitness()
```

Try make again:


```
make
```

Screen output:

```
make all-recursive
make[1]: Entering directory '/home/richel/Downloads/eo-1.0.1'
Making all in src
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
Making all in es
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/es'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_checkpoint_es.o -MD -MP -MF ".deps/make_checkpoint_es.Tpo" -c -o make_checkpoint_es.o make_checkpoint_es.cpp; \
then mv -f ".deps/make_checkpoint_es.Tpo" ".deps/make_checkpoint_es.Po"; else rm -f ".deps/make_checkpoint_es.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:35,
from make_checkpoint_es.cpp:44:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_checkpoint_real.o -MD -MP -MF ".deps/make_checkpoint_real.Tpo" -c -o make_checkpoint_real.o make_checkpoint_real.cpp; \
then mv -f ".deps/make_checkpoint_real.Tpo" ".deps/make_checkpoint_real.Po"; else rm -f ".deps/make_checkpoint_real.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:35,
from make_checkpoint_real.cpp:44:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_continue_es.o -MD -MP -MF ".deps/make_continue_es.Tpo" -c -o make_continue_es.o make_continue_es.cpp; \
then mv -f ".deps/make_continue_es.Tpo" ".deps/make_continue_es.Po"; else rm -f ".deps/make_continue_es.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_continue_real.o -MD -MP -MF ".deps/make_continue_real.Tpo" -c -o make_continue_real.o make_continue_real.cpp; \
then mv -f ".deps/make_continue_real.Tpo" ".deps/make_continue_real.Po"; else rm -f ".deps/make_continue_real.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_genotype_es.o -MD -MP -MF ".deps/make_genotype_es.Tpo" -c -o make_genotype_es.o make_genotype_es.cpp; \
then mv -f ".deps/make_genotype_es.Tpo" ".deps/make_genotype_es.Po"; else rm -f ".deps/make_genotype_es.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_genotype_real.o -MD -MP -MF ".deps/make_genotype_real.Tpo" -c -o make_genotype_real.o make_genotype_real.cpp; \
then mv -f ".deps/make_genotype_real.Tpo" ".deps/make_genotype_real.Po"; else rm -f ".deps/make_genotype_real.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_op_es.o -MD -MP -MF ".deps/make_op_es.Tpo" -c -o make_op_es.o make_op_es.cpp; \
then mv -f ".deps/make_op_es.Tpo" ".deps/make_op_es.Po"; else rm -f ".deps/make_op_es.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_op_real.o -MD -MP -MF ".deps/make_op_real.Tpo" -c -o make_op_real.o make_op_real.cpp; \
then mv -f ".deps/make_op_real.Tpo" ".deps/make_op_real.Po"; else rm -f ".deps/make_op_real.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_pop_es.o -MD -MP -MF ".deps/make_pop_es.Tpo" -c -o make_pop_es.o make_pop_es.cpp; \
then mv -f ".deps/make_pop_es.Tpo" ".deps/make_pop_es.Po"; else rm -f ".deps/make_pop_es.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_pop_real.o -MD -MP -MF ".deps/make_pop_real.Tpo" -c -o make_pop_real.o make_pop_real.cpp; \
then mv -f ".deps/make_pop_real.Tpo" ".deps/make_pop_real.Po"; else rm -f ".deps/make_pop_real.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_run_es.o -MD -MP -MF ".deps/make_run_es.Tpo" -c -o make_run_es.o make_run_es.cpp; \
then mv -f ".deps/make_run_es.Tpo" ".deps/make_run_es.Po"; else rm -f ".deps/make_run_es.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_run_real.o -MD -MP -MF ".deps/make_run_real.Tpo" -c -o make_run_real.o make_run_real.cpp; \
then mv -f ".deps/make_run_real.Tpo" ".deps/make_run_real.Po"; else rm -f ".deps/make_run_real.Tpo"; exit 1; fi
rm -f libes.a
/usr/bin/ar cru libes.a make_algo_scalar_es.o make_algo_scalar_real.o make_checkpoint_es.o make_checkpoint_real.o make_continue_es.o make_continue_real.o make_genotype_es.o make_genotype_real.o make_op_es.o make_op_real.o make_pop_es.o make_pop_real.o make_run_es.o make_run_real.o
ranlib libes.a
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT eig.o -MD -MP -MF ".deps/eig.Tpo" -c -o eig.o eig.cpp; \
then mv -f ".deps/eig.Tpo" ".deps/eig.Po"; else rm -f ".deps/eig.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT CMAState.o -MD -MP -MF ".deps/CMAState.Tpo" -c -o CMAState.o CMAState.cpp; \
then mv -f ".deps/CMAState.Tpo" ".deps/CMAState.Po"; else rm -f ".deps/CMAState.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT CMAParams.o -MD -MP -MF ".deps/CMAParams.Tpo" -c -o CMAParams.o CMAParams.cpp; \
then mv -f ".deps/CMAParams.Tpo" ".deps/CMAParams.Po"; else rm -f ".deps/CMAParams.Tpo"; exit 1; fi
rm -f libcma.a
/usr/bin/ar cru libcma.a eig.o CMAState.o CMAParams.o
ranlib libcma.a
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/es'
Making all in ga
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/ga'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_algo_scalar_ga.o -MD -MP -MF ".deps/make_algo_scalar_ga.Tpo" -c -o make_algo_scalar_ga.o make_algo_scalar_ga.cpp; \
then mv -f ".deps/make_algo_scalar_ga.Tpo" ".deps/make_algo_scalar_ga.Po"; else rm -f ".deps/make_algo_scalar_ga.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_checkpoint_ga.o -MD -MP -MF ".deps/make_checkpoint_ga.Tpo" -c -o make_checkpoint_ga.o make_checkpoint_ga.cpp; \
then mv -f ".deps/make_checkpoint_ga.Tpo" ".deps/make_checkpoint_ga.Po"; else rm -f ".deps/make_checkpoint_ga.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:35,
from make_checkpoint_ga.cpp:47:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_continue_ga.o -MD -MP -MF ".deps/make_continue_ga.Tpo" -c -o make_continue_ga.o make_continue_ga.cpp; \
then mv -f ".deps/make_continue_ga.Tpo" ".deps/make_continue_ga.Po"; else rm -f ".deps/make_continue_ga.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_genotype_ga.o -MD -MP -MF ".deps/make_genotype_ga.Tpo" -c -o make_genotype_ga.o make_genotype_ga.cpp; \
then mv -f ".deps/make_genotype_ga.Tpo" ".deps/make_genotype_ga.Po"; else rm -f ".deps/make_genotype_ga.Tpo"; exit 1; fi
In file included from ../../src/ga/make_genotype_ga.h:30,
from make_genotype_ga.cpp:44:
../../src/ga/eoBit.h: In member function 'virtual void eoBit<FitT>::readFrom(std::istream&)’:
../../src/ga/eoBit.h:104: error: 'transform’ is not a member of 'std’
make[3]: *** [make_genotype_ga.o] Error 1
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/ga'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/richel/Downloads/eo-1.0.1'
make: *** [all] Error 2
```

I zoomed in on the following error:

```
../../src/ga/eoBit.h:104: error: 'transform’ is not a member of 'std’
```

I edited the file eoBit.h by adding one line, shown below:

```
#ifndef eoBit_h
#define eoBit_h

//-----------------------------------------------------------------------------
#include <iostream>    // std::ostream, std::istream
#include <functional>  // bind2nd
#include <string>      // std::string
#include <algorithm>   // Added by RJCB
```

Try make again:

```
make
```

Screen output:

```
make all-recursive
make[1]: Entering directory '/home/richel/Downloads/eo-1.0.1'
Making all in src
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
Making all in es
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/es'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/es'
Making all in ga
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/ga'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_algo_scalar_ga.o -MD -MP -MF ".deps/make_algo_scalar_ga.Tpo" -c -o make_algo_scalar_ga.o make_algo_scalar_ga.cpp; \
then mv -f ".deps/make_algo_scalar_ga.Tpo" ".deps/make_algo_scalar_ga.Po"; else rm -f ".deps/make_algo_scalar_ga.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_checkpoint_ga.o -MD -MP -MF ".deps/make_checkpoint_ga.Tpo" -c -o make_checkpoint_ga.o make_checkpoint_ga.cpp; \
then mv -f ".deps/make_checkpoint_ga.Tpo" ".deps/make_checkpoint_ga.Po"; else rm -f ".deps/make_checkpoint_ga.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:35,
from make_checkpoint_ga.cpp:47:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:82: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_continue_ga.o -MD -MP -MF ".deps/make_continue_ga.Tpo" -c -o make_continue_ga.o make_continue_ga.cpp; \
then mv -f ".deps/make_continue_ga.Tpo" ".deps/make_continue_ga.Po"; else rm -f ".deps/make_continue_ga.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_genotype_ga.o -MD -MP -MF ".deps/make_genotype_ga.Tpo" -c -o make_genotype_ga.o make_genotype_ga.cpp; \
then mv -f ".deps/make_genotype_ga.Tpo" ".deps/make_genotype_ga.Po"; else rm -f ".deps/make_genotype_ga.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_op_ga.o -MD -MP -MF ".deps/make_op_ga.Tpo" -c -o make_op_ga.o make_op_ga.cpp; \
then mv -f ".deps/make_op_ga.Tpo" ".deps/make_op_ga.Po"; else rm -f ".deps/make_op_ga.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_pop_ga.o -MD -MP -MF ".deps/make_pop_ga.Tpo" -c -o make_pop_ga.o make_pop_ga.cpp; \
then mv -f ".deps/make_pop_ga.Tpo" ".deps/make_pop_ga.Po"; else rm -f ".deps/make_pop_ga.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_run_ga.o -MD -MP -MF ".deps/make_run_ga.Tpo" -c -o make_run_ga.o make_run_ga.cpp; \
then mv -f ".deps/make_run_ga.Tpo" ".deps/make_run_ga.Po"; else rm -f ".deps/make_run_ga.Tpo"; exit 1; fi
rm -f libga.a
/usr/bin/ar cru libga.a make_algo_scalar_ga.o make_checkpoint_ga.o make_continue_ga.o make_genotype_ga.o make_op_ga.o make_pop_ga.o make_run_ga.o
ranlib libga.a
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/ga'
Making all in gp
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/gp'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/gp'
Making all in do
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/do'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/do'
Making all in utils
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/utils'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoData.o -MD -MP -MF ".deps/eoData.Tpo" -c -o eoData.o eoData.cpp; \
then mv -f ".deps/eoData.Tpo" ".deps/eoData.Po"; else rm -f ".deps/eoData.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoFileMonitor.o -MD -MP -MF ".deps/eoFileMonitor.Tpo" -c -o eoFileMonitor.o eoFileMonitor.cpp; \
then mv -f ".deps/eoFileMonitor.Tpo" ".deps/eoFileMonitor.Po"; else rm -f ".deps/eoFileMonitor.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoGnuplot.o -MD -MP -MF ".deps/eoGnuplot.Tpo" -c -o eoGnuplot.o eoGnuplot.cpp; \
then mv -f ".deps/eoGnuplot.Tpo" ".deps/eoGnuplot.Po"; else rm -f ".deps/eoGnuplot.Tpo"; exit 1; fi
eoGnuplot.cpp: In member function 'void eoGnuplot::initGnuPlot(std::string, std::string)’:
eoGnuplot.cpp:76: error: 'strdup’ was not declared in this scope
eoGnuplot.cpp:82: warning: deprecated conversion from string constant to 'char*’
make[3]: *** [eoGnuplot.o] Error 1
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/richel/Downloads/eo-1.0.1'
make: *** [all] Error 2
```

I zoomed in on the following error:

```
eoGnuplot.cpp:76: error: 'strdup’ was not declared in this scope
```

I edited the file scr/utils/eognuplot.cpp by adding one line, shown
below:

```
#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <cstring> //Added by RJCB
#include <sstream>
#include <stdexcept>

#include "eoGnuplot.h"
```

Try make again:

```
make
```

Screen output:

```
make all-recursive
make[1]: Entering directory '/home/richel/Downloads/eo-1.0.1'
Making all in src
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
Making all in es
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/es'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/es'
Making all in ga
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/ga'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/ga'
Making all in gp
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/gp'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/gp'
Making all in do
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/do'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/do'
Making all in utils
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/utils'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoGnuplot.o -MD -MP -MF ".deps/eoGnuplot.Tpo" -c -o eoGnuplot.o eoGnuplot.cpp; \
then mv -f ".deps/eoGnuplot.Tpo" ".deps/eoGnuplot.Po"; else rm -f ".deps/eoGnuplot.Tpo"; exit 1; fi
eoGnuplot.cpp: In member function 'void eoGnuplot::initGnuPlot(std::string, std::string)’:
eoGnuplot.cpp:83: warning: deprecated conversion from string constant to 'char*’
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoGnuplot1DMonitor.o -MD -MP -MF ".deps/eoGnuplot1DMonitor.Tpo" -c -o eoGnuplot1DMonitor.o eoGnuplot1DMonitor.cpp; \
then mv -f ".deps/eoGnuplot1DMonitor.Tpo" ".deps/eoGnuplot1DMonitor.Po"; else rm -f ".deps/eoGnuplot1DMonitor.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoGnuplot1DSnapshot.o -MD -MP -MF ".deps/eoGnuplot1DSnapshot.Tpo" -c -o eoGnuplot1DSnapshot.o eoGnuplot1DSnapshot.cpp; \
then mv -f ".deps/eoGnuplot1DSnapshot.Tpo" ".deps/eoGnuplot1DSnapshot.Po"; else rm -f ".deps/eoGnuplot1DSnapshot.Tpo"; exit 1; fi
In file included from eoGnuplot1DSnapshot.h:38,
from eoGnuplot1DSnapshot.cpp:5:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:66: error: 'system’ was not declared in this scope
make[3]: *** [eoGnuplot1DSnapshot.o] Error 1
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/richel/Downloads/eo-1.0.1'
make: *** [all] Error 2
```

I zoomed in on the following error:

```
../../src/utils/eoFileSnapshot.h:66: error: 'system’ was not declared in this scope
```

I edited the file scr/utils/eoFileSnapshot.h by adding one line, shown
below:

```
#ifndef _eoFileSnapshot_h
#define _eoFileSnapshot_h

#include <cstdlib> //Added by RJCB
#include <string>
#include <fstream>
#include <utils/eoParam.h>
#include <utils/eoMonitor.h>
#include <eoObject.h>
```

Try make again:

```
make
```

Screen output:

```
make all-recursive
make[1]: Entering directory '/home/richel/Downloads/eo-1.0.1'
Making all in src
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
Making all in es
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/es'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_checkpoint_es.o -MD -MP -MF ".deps/make_checkpoint_es.Tpo" -c -o make_checkpoint_es.o make_checkpoint_es.cpp; \
then mv -f ".deps/make_checkpoint_es.Tpo" ".deps/make_checkpoint_es.Po"; else rm -f ".deps/make_checkpoint_es.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:35,
from make_checkpoint_es.cpp:44:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT make_checkpoint_real.o -MD -MP -MF ".deps/make_checkpoint_real.Tpo" -c -o make_checkpoint_real.o make_checkpoint_real.cpp; \
then mv -f ".deps/make_checkpoint_real.Tpo" ".deps/make_checkpoint_real.Po"; else rm -f ".deps/make_checkpoint_real.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:35,
from make_checkpoint_real.cpp:44:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
rm -f libes.a
/usr/bin/ar cru libes.a make_algo_scalar_es.o make_algo_scalar_real.o make_checkpoint_es.o make_checkpoint_real.o make_continue_es.o make_continue_real.o make_genotype_es.o make_genotype_real.o make_op_es.o make_op_real.o make_pop_es.o make_pop_real.o make_run_es.o make_run_real.o
ranlib libes.a
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/es'
Making all in ga
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/ga'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -I../../src -g -O2 -MT make_checkpoint_ga.o -MD -MP -MF ".deps/make_checkpoint_ga.Tpo" -c -o make_checkpoint_ga.o make_checkpoint_ga.cpp; \
then mv -f ".deps/make_checkpoint_ga.Tpo" ".deps/make_checkpoint_ga.Po"; else rm -f ".deps/make_checkpoint_ga.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/do/make_checkpoint.h:35,
from make_checkpoint_ga.cpp:47:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
rm -f libga.a
/usr/bin/ar cru libga.a make_algo_scalar_ga.o make_checkpoint_ga.o make_continue_ga.o make_genotype_ga.o make_op_ga.o make_pop_ga.o make_run_ga.o
ranlib libga.a
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/ga'
Making all in gp
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/gp'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/gp'
Making all in do
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/do'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/do'
Making all in utils
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/utils'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoGnuplot.o -MD -MP -MF ".deps/eoGnuplot.Tpo" -c -o eoGnuplot.o eoGnuplot.cpp; \
then mv -f ".deps/eoGnuplot.Tpo" ".deps/eoGnuplot.Po"; else rm -f ".deps/eoGnuplot.Tpo"; exit 1; fi
eoGnuplot.cpp: In member function 'void eoGnuplot::initGnuPlot(std::string, std::string)’:
eoGnuplot.cpp:83: warning: deprecated conversion from string constant to 'char*’
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoGnuplot1DSnapshot.o -MD -MP -MF ".deps/eoGnuplot1DSnapshot.Tpo" -c -o eoGnuplot1DSnapshot.o eoGnuplot1DSnapshot.cpp; \
then mv -f ".deps/eoGnuplot1DSnapshot.Tpo" ".deps/eoGnuplot1DSnapshot.Po"; else rm -f ".deps/eoGnuplot1DSnapshot.Tpo"; exit 1; fi
In file included from eoGnuplot1DSnapshot.h:38,
from eoGnuplot1DSnapshot.cpp:5:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoIntBounds.o -MD -MP -MF ".deps/eoIntBounds.Tpo" -c -o eoIntBounds.o eoIntBounds.cpp; \
then mv -f ".deps/eoIntBounds.Tpo" ".deps/eoIntBounds.Po"; else rm -f ".deps/eoIntBounds.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoParser.o -MD -MP -MF ".deps/eoParser.Tpo" -c -o eoParser.o eoParser.cpp; \
then mv -f ".deps/eoParser.Tpo" ".deps/eoParser.Po"; else rm -f ".deps/eoParser.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoRealBounds.o -MD -MP -MF ".deps/eoRealBounds.Tpo" -c -o eoRealBounds.o eoRealBounds.cpp; \
then mv -f ".deps/eoRealBounds.Tpo" ".deps/eoRealBounds.Po"; else rm -f ".deps/eoRealBounds.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoRNG.o -MD -MP -MF ".deps/eoRNG.Tpo" -c -o eoRNG.o eoRNG.cpp; \
then mv -f ".deps/eoRNG.Tpo" ".deps/eoRNG.Po"; else rm -f ".deps/eoRNG.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoState.o -MD -MP -MF ".deps/eoState.Tpo" -c -o eoState.o eoState.cpp; \
then mv -f ".deps/eoState.Tpo" ".deps/eoState.Po"; else rm -f ".deps/eoState.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoStdoutMonitor.o -MD -MP -MF ".deps/eoStdoutMonitor.Tpo" -c -o eoStdoutMonitor.o eoStdoutMonitor.cpp; \
then mv -f ".deps/eoStdoutMonitor.Tpo" ".deps/eoStdoutMonitor.Po"; else rm -f ".deps/eoStdoutMonitor.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT eoUpdater.o -MD -MP -MF ".deps/eoUpdater.Tpo" -c -o eoUpdater.o eoUpdater.cpp; \
then mv -f ".deps/eoUpdater.Tpo" ".deps/eoUpdater.Po"; else rm -f ".deps/eoUpdater.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -DGNUPLOT_PROGRAM=\"gnuplot\" -g -O2 -MT make_help.o -MD -MP -MF ".deps/make_help.Tpo" -c -o make_help.o make_help.cpp; \
then mv -f ".deps/make_help.Tpo" ".deps/make_help.Po"; else rm -f ".deps/make_help.Tpo"; exit 1; fi
make_help.cpp: In function 'void make_help(eoParser&)’:
make_help.cpp:68: error: 'exit’ was not declared in this scope
make_help.cpp: In function 'bool testDirRes(std::string, bool)’:
make_help.cpp:82: error: 'system’ was not declared in this scope
make[3]: *** [make_help.o] Error 1
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/richel/Downloads/eo-1.0.1'
make: *** [all] Error 2
```

I zoomed in on the following error:

```
make_help.cpp:82: error: 'system’ was not declared in this scope
```

I edited the file scr/utils/make\_help.cpp by adding one line, shown
below:

```
 
#ifdef _MSC_VER
// to avoid long name warnings
#pragma warning(disable:4786)
#endif

#include <cstdlib> //Added by RJCB
#include <utils/eoParser.h>
#include <fstream>
#include <stdexcept>

using namespace std;
```

Try make again:

```
make
```

Screen output:

```
make all-recursive
make[1]: Entering directory '/home/richel/Downloads/eo-1.0.1'
Making all in src
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
Making all in es
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/es'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/es'
Making all in ga
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/ga'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/ga'
Making all in gp
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/gp'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/gp'
Making all in do
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/do'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/do'
Making all in utils
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/utils'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/utils'
Making all in other
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src/other'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src/other'
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/src'
make[3]: Nothing to be done for 'all-am'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/src'
Making all in doc
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/doc'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/doc'
Making all in contrib
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/contrib'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/contrib'
Making all in win
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/win'
make[2]: Nothing to be done for 'all'.
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/win'
Making all in app
make[2]: Entering directory '/home/richel/Downloads/eo-1.0.1/app'
Making all in mastermind
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/app/mastermind'
make[3]: Nothing to be done for 'all'.
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/app/mastermind'
Making all in gprop
make[3]: Entering directory '/home/richel/Downloads/eo-1.0.1/app/gprop'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src -g -O2 -MT gprop.o -MD -MP -MF ".deps/gprop.Tpo" -c -o gprop.o gprop.cpp; \
then mv -f ".deps/gprop.Tpo" ".deps/gprop.Po"; else rm -f ".deps/gprop.Tpo"; exit 1; fi
In file included from ../../src/utils/eoGnuplot1DSnapshot.h:38,
from ../../src/utils/checkpointing:9,
from ../../src/eo:135,
from gprop.cpp:11:
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
../../src/utils/eoFileSnapshot.h: In constructor 'eoFileSnapshot::eoFileSnapshot(std::string, unsigned int, std::string, std::string, unsigned int, bool)’:
../../src/utils/eoFileSnapshot.h:83: warning: ignoring return value of 'int system(const char*)’, declared with attribute warn_unused_result
gprop.cpp: At global scope:
gprop.cpp:37: error: conflicting declaration 'const std::string& s’
gprop.cpp:37: error: 's’ has a previous declaration as 'mlp::set& s’
gprop.cpp: In function 'void arg(int, char**)’:
gprop.cpp:37: error: too many arguments to function 'void load_file(mlp::set&)’
gprop.cpp:81: error: at this point in file
gprop.cpp:37: error: too many arguments to function 'void load_file(mlp::set&)’
gprop.cpp:82: error: at this point in file
gprop.cpp:37: error: too many arguments to function 'void load_file(mlp::set&)’
gprop.cpp:83: error: at this point in file
make[3]: *** [gprop.o] Error 1
make[3]: Leaving directory '/home/richel/Downloads/eo-1.0.1/app/gprop'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory '/home/richel/Downloads/eo-1.0.1/app'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/home/richel/Downloads/eo-1.0.1'
make: *** [all] Error 2
```

Then, I quit trying.

You can download all modified EO files (up until the point I got)
[here](CppEo.zip).

# Getting Started {#index}
An overview of ROSE, how to download and use, basic templates and examples, and more.

## Table of contents

* [Global Table of Contents](#what_is_rose)
  * [Getting Started](#what_is_rose)
  * [Tutorials](#what_is_rose)
* [What is ROSE](#what_is_rose)
* [Download](#download)
  * [Official release](#official_release)
  * [What's included](#whats_included)
* [Prerequisites](#prerequisites)
  * [Supported platforms](#supported_platforms)
  * [Dependencies](#dependencies)
    * [GCC](#dependencies__gcc)
    * [Boost](#dependencies__boost)
    * [Autotools](#dependencies__autotools)
    * [JDK](#dependencies__jdk)
* [Installation](#installation)
  * [Setup](#installation__setup)
  * [Configure](#installation__configure)
  * [Compile](#installation__compile)
  * [Install](#installation__install)
* [Examples](#examples)
* [Documentation](#documentation)
* [Getting Help](#help)
* [Frequently Asked Questions (FAQs)](#faq)

## What is ROSE? <a name="what_is_rose"></a>
Developed at Lawrence Livermore National Laboratory (LLNL), ROSE is an open source compiler infrastructure to build source-to-source program transformation and analysis tools for large-scale C(C89 and C98), C++(C++98 and C++11), UPC, Fortran (77/95/2003), OpenMP, Java, Python and PHP applications.

Visit our website for more information: http://rosecompiler.org/.

## Download <a name="download"></a>
We currently distribute ROSE through a SCM repository hosted in Github. Tarball and binary releases are currently unavailable.

### Official release <a name="official_release"></a>
You can clone our officially released source code from our [github repository](https://github.com/rose-compiler/rose.git) using this command:

~~~{.bash}
$ git clone https://github.com/rose-compiler/rose.git
~~~

This will create a directory called `rose`. We’ll assume that the full path to this directory is in the `ROSE_ROOT` environment variable set using this command:

~~~{.bash}
$ export ROSE_ROOT="/path/to/rose"
~~~

### What's included <a name="whats_included"></a>
Once downloaded, go into the `ROSE_ROOT` directory. You'll see something like this:

~~~{.bash}
rose/
|-- docs/
|-- src/
|   |-- frontend/
|   |-- midend/
|   |-- backend/
|   |-- ROSETTA/
|-- tests/
|-- tutorials/
`-- exampleTranslators/
~~~

## Prerequisites <a name="prerequisites"></a>

### Supported platforms <a name="supported_platforms"></a>
ROSE uses continuous integration and has been officially tested on the following platforms:

 Operating System        |   Tested Versions |
-------------------------|--------------------
 Redhat Enterprise Linux | `5.11`  `6.7` `7.1`

### Dependencies <a name="dependencies"></a>
Currently, ROSE requires the following software:
* [GNU Compiler Collection](https://gcc.gnu.org/)
* [Boost C++ libraries](http://www.boost.org/)
* GNU Autotools: [Autoconf](http://www.gnu.org/software/autoconf/autoconf.html), [Automake](http://www.gnu.org/software/automake/automake.html), [Libtool](http://www.gnu.org/software/libtool/libtool.html), [Make](https://www.gnu.org/software/make/)
* [Oracle Java Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

#### GNU Compiler Collection <a name="dependencies__gcc"></a>

 Tested GCC Versions     | Tested Boost Versions    |
:-----------------------:|:-------------------------:
 `4.2.4`                 | `1.45.0` `1.47.0`        |
 `4.4.7`                 | `1.47.0`                 |
 `4.8.1`                 | `1.50.0`                 |

#### Boost C++ Libraries <a name="dependencies__boost"></a>

 Tested Boost Versions   | Tested GCC Versions      |
:-----------------------:|:-------------------------:
 `1.45.0`                | `4.2.4`
 `1.47.0`                | `4.2.4` `4.4.7`
 `1.50.0`                | `4.8.1`

#### GNU Autotools <a name="dependencies__autotools"></a>

 GNU Autotool   | Tested Versions   |
----------------|--------------------
 [Autoconf](http://www.gnu.org/software/autoconf/autoconf.html)   | `2.69`
 [Automake](http://www.gnu.org/software/automake/automake.html)   | `1.14`
 [Libtool](http://www.gnu.org/software/libtool/libtool.html)    | `2.4`
 [Make](https://www.gnu.org/software/make/)       | `3.82`

#### Java Development Kit <a name="dependencies__jdk"></a>

 Java Development Kit (JDK) |   Tested Versions |
----------------------------|--------------------
 [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/index.html)                     | `1.7.0_51`

## Installation <a name="installation"></a>

## Setup <a name="installation__setup"></a>
ROSE currently uses the GNU Autotools as the official build system to configure, compile, and install ROSE.

But before any of these steps can happen, you will need to execute the Autotools bootstrapping script in `ROSE_ROOT`:

~~~{.bash}
$ cd $ROSE_ROOT

$ ./build
~~~

This script generates the Autoconf `${ROSE_ROOT}/configure` script, which we will use next to configure ROSE for compilation.

### Configure <a name="installation__configure"></a>
ROSE must be configured in a separate directory, which we will refer to as `$ROSE_BUILD`, which must be outside of `$ROSE_ROOT`:

~~~{.bash}
$ cd /path/to/rose/workspace

$ mkdir build
$ cd build/

$ export ROSE_BUILD="/path/to/rose/workspace/build"
~~~

Currently, the minimal configuration line for ROSE is the following:

~~~{.bash}
ROSE_BUILD $ "${ROSE_ROOT}/configure" --with-boost="${BOOST_HOME}"
~~~

### Compile <a name="installation__compile"></a>

~~~{.bash}
ROSE_BUILD $ make
~~~

### Install <a name="installation__install"></a>

~~~{.bash}
ROSE_BUILD $ make install
~~~

## Basic ROSE Makefile template <a name="basic_template"></a>
In order to compile your own ROSE tool, please reference this example Makefile template for the correct commandlines required to link your source code with ROSE:

~~~{.bash}
# Sample makefile for programs that use the ROSE library.
#
# ROSE has a number of configuration details that must be present when
# compiling and linking a user program with ROSE, and some of these
# details are difficult to get right.  The most foolproof way to get
# these details into your own makefile is to use the "rose-config"
# tool.
#
#
# This makefile assumes:
#   1. The ROSE library has been properly installed (refer to the
#      documentation for configuring, building, and installing ROSE).
#
#   2. The top of the installation directory is $(ROSE_INSTALL). This
#      is the same directory you specified for the "--prefix" argument
#      of the "configure" script, or the "CMAKE_INSTALL_PREFIX" if using
#      cmake. E.g., "/usr/local".
#
# The "rose-config" tool currently only works for ROSE configured with
# GNU auto tools (e.g., you ran "configure" when you built and
# installed ROSE). The "cmake" configuration is not currently
# supported by "rose-config" [September 2015].
##############################################################################

# Standard C++ compiler stuff.
CPPFLAGS = $(shell $(ROSE_INSTALL)/bin/rose-config cppflags)
CFLAGS   = $(shell $(ROSE_INSTALL)/bin/rose-config cflags)
LDFLAGS  = $(shell $(ROSE_INSTALL)/bin/rose-config ldflags)

MOSTLYCLEANFILES =

##############################################################################
# Assuming your source code is "demo.C" to build an executable named "demo".

all: demo

demo.o: demo.C
  $(CXX) $(CPPFLAGS) $(CFLAGS) -o $@ -c $^

demo: demo.o
  $(CXX) $(CFLAGS) $(LDFLAGS) -o $@ $^
  @echo "Remember to set:"
  @echo "  LD_LIBRARY_PATH=$$LD_LIBRARY_PATH:$(shell $(ROSE_INSTALL)/bin/rose-config libdirs)"

MOSTLYCLEANFILES += demo demo.o

##############################################################################
# Standard boilerplate

.PHONY: clean
clean:
  rm -f $(MOSTLYCLEANFILES)
~~~

## Examples <a name="examples"></a>

TODO: Link to ROSE Tutorials.

## Documentation <a name="documentation"></a>

## Getting Help <a name="help"></a>

## Frequently Asked Questions (FAQs) <a name="faq"></a>

### How can I configure ROSE to use a different backend compiler?

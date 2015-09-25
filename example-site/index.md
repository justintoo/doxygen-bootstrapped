# Getting Started {#index}
An overview of ROSE, how to download and use, basic templates and examples, and more.

## Table of contents

* [What is ROSE](#what_is_rose)
* [Download](#download)
  * [Official release](#official_release)
  * [What's included](#whats_included)
* [Prerequisites](#prerequisites)
  * [Supported platforms](#supported_platforms)
  * [Dependencies](#dependencies)
    * [Boost C++ Libraries (Boost)](#dependencies__boost)
    * [GNU Compiler Collection (GCC)](#dependencies__gcc)
    * [Java Development Kit (JDK)](#dependencies__jdk)
* [Installation](#installation)
  * [Supported platforms](#supported_platforms)
  * [Prerequisites](#prerequisites)

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

ROSE is known to work on the following platforms, although they are not officially supported yet:

* CentOS >= 5.5
* Ubuntu 12.04, 14.10

### Dependencies <a name="dependencies"></a>
Currently, ROSE requires the following software:
* [GNU Compiler Collection](https://gcc.gnu.org/)
* [Boost C++ libraries](http://www.boost.org/)
* GNU Autotools: [Autoconf](http://www.gnu.org/software/autoconf/autoconf.html), [Automake](http://www.gnu.org/software/automake/automake.html), [Libtool](http://www.gnu.org/software/libtool/libtool.html), [Make](https://www.gnu.org/software/make/)
* [Oracle Java Development Kit (JDK)](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

#### GNU Compiler Collection (GCC) <a name="dependencies__gcc"></a>

 Tested GCC Versions     | Tested Boost Versions    |
:-----------------------:|:-------------------------:
 `4.2.4`                 | `1.45.0` `1.47.0`        |
 `4.4.7`                 | `1.47.0`                 |
 `4.8.1`                 | `1.50.0`                 |

#### Boost C++ Libraries (Boost) <a name="dependencies__boost"></a>

 Tested Boost Versions   | Tested GCC Versions      |
:-----------------------:|:-------------------------:
 `1.45.0`                | `4.2.4`
 `1.47.0`                | `4.2.4` `4.4.7`
 `1.50.0`                | `4.8.1`

#### GNU Autotools (Autoconf, Automake, Libtool, Make) <a name="dependencies__autotools"></a>

 GNU Autotool   | Tested Versions   |
----------------|--------------------
 [Autoconf]()   | `1.7.0_51`
 [Automake]()   | `1.7.0_51`
 [Libtool]()    | `1.7.0_51`
 [Make]()       | `1.7.0_51`

#### Java Development Kit (JDK) <a name="dependencies__jdk"></a>

 Java Development Kit (JDK) |   Tested Versions |
----------------------------|--------------------
 [Oracle](http://www.oracle.com/technetwork/java/javase/downloads/index.html)                     | `1.7.0_51`

## Setup <a name="setup"></a>

## Compile <a name="compile"></a>

## Install <a name="install"></a>

## Basic template <a name="basic_template"></a>

## Examples <a name="examples"></a>

## Documentation <a name="documentation"></a>

## Development Build <a name="development_build"></a>

## FAQ <a name="faq"></a>

### How can I configure ROSE to use a different backend compiler?

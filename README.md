# BLOGCOIN

| **General** | **Master build status** | **Development build status** |
|-------------|-------------------------|------------------------------|
| ![GitHub repo size](https://img.shields.io/github/repo-size/blognetwork/blogcoin.svg?label=Repository%20size%3A&style=popout-square) | [![Travis master branch](https://img.shields.io/travis/blognetwork/blogcoin/master.svg?label=TravisCI&style=popout-square)](https://travis-ci.org/blognetwork/blogcoin) | [![Travis development branch](https://img.shields.io/travis/blognetwork/blogcoin/development.svg?label=TravisCI&style=popout-square)](https://travis-ci.org/blognetwork/blogcoin) |
| [![GitHub issues](https://img.shields.io/github/issues-raw/blognetwork/blogcoin.svg?label=Issues%20that%20need%20help%3A&style=popout-square)](https://github.com/blognetwork/blogcoin/issues) | [![AppVeyor master branch](https://img.shields.io/appveyor/ci/TheDevMinerTV/blogcoin/master.svg?label=AppVeyor&style=popout-square)](https://ci.appveyor.com/project/TheDevMinerTV/blogcoin) | [![AppVeyor development branch](https://img.shields.io/appveyor/ci/TheDevMinerTV/blogcoin/development.svg?label=AppVeyor&style=popout-square)](https://ci.appveyor.com/project/TheDevMinerTV/blogcoin) |
| [![GitHub Releases](https://img.shields.io/github/downloads/blognetwork/blogcoin/total.svg?style=flat-square)](https://github.com/blognetwork/blogcoin/releases) | | |
| [![Discord](https://img.shields.io/discord/586214949747949588.svg?label=Discord&style=popout-square)](https://discord.gg/4huZQF9) | | |

### Installing

We offer binary images of the latest releases here: https://github.com/blognetwork/blogcoin/releases

If you would like to compile yourself, read on.

### How To Compile

#### Build Optimization

The CMake build system will, by default, create optimized *native* builds for your particular system type when you build the software. Using this method, the binaries created provide a better experience and all together faster performance.

However, if you wish to create *portable* binaries that can be shared between systems, specify `-DARCH=default` in your CMake arguments during the build process. Note that *portable* binaries will have a noticable difference in performance than *native* binaries. For this reason, it is always best to build for your particular system if possible.

#### Linux

##### Prerequisites

You will need the following packages: [Boost](https://www.boost.org/), [OpenSSL](https://www.openssl.org/), cmake (3.8 or higher), make, and git.

You will also need either GCC/G++, or Clang.

If you are using GCC, you will need GCC-7.0 or higher.

If you are using Clang, you will need Clang 6.0 or higher. You will also need libstdc++\-6.0 or higher.

##### Ubuntu, using GCC

```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y
sudo apt-get update
sudo apt-get install aptitude -y
sudo aptitude install -y build-essential g++-8 gcc-8 git libboost-all-dev python-pip libssl-dev
sudo pip install cmake
export CC=gcc-8
export CXX=g++-8
git clone -b master --single-branch https://github.com/blognetwork/blogcoin
cd blogcoin
mkdir build
cd build
cmake ..
make
```

The binaries will be in the `src` folder when you are complete.

```bash
cd src
./BlogCoinDaemon --version
```

##### Ubuntu, using Clang

```bash
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y
wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key | sudo apt-key add -
```

You need to modify the below command for your version of ubuntu - see https://apt.llvm.org/

* Ubuntu 14.04 (Trusty)
- `sudo add-apt-repository "deb https://apt.llvm.org/trusty/ llvm-toolchain-trusty 6.0 main"`

* Ubuntu 16.04 (Xenial)
- `sudo add-apt-repository "deb https://apt.llvm.org/xenial/ llvm-toolchain-xenial 6.0 main"`

* Ubuntu 18.04 (Bionic)
- `sudo add-apt-repository "deb https://apt.llvm.org/bionic/ llvm-toolchain-bionic 6.0 main"`

```bash
sudo apt-get update
sudo apt-get install aptitude -y
sudo aptitude install -y -o Aptitude::ProblemResolver::SolutionCost='100*canceled-actions,200*removals' build-essential clang-6.0 libstdc++-7-dev git libboost-all-dev python-pip libssl-dev
sudo pip install cmake
export CC=clang-6.0
export CXX=clang++-6.0
git clone -b master --single-branch https://github.com/blognetwork/blogcoin
cd v
mkdir build
cd build
cmake ..
make
```

The binaries will be in the `src` folder when you are complete.

```bash
cd src
./BlogCoinDaemon --version
```

##### Generic Linux

Ensure you have the dependencies listed above.

If you want to use clang, ensure you set the environment variables `CC` and `CXX`.
See the ubuntu instructions for an example.

```bash
git clone -b master --single-branch https://github.com/blognetwork/blogcoin
cd blogcoin
mkdir build
cd build
cmake ..
make
```

The binaries will be in the `src` folder when you are complete.

```bash
cd src
./BlogCoinDaemon --version
```

#### OSX/Apple, using Clang

##### Prerequisites

- Install XCode and Developer Tools.

##### Building

```bash
which brew || /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install --force cmake boost llvm openssl
export CC=/usr/local/opt/llvm/bin/clang
export CXX=/usr/local/opt/llvm/bin/clang++
git clone -b master --single-branch https://github.com/blognetwork/blogcoin
cd blogcoin
mkdir build
cd build
cmake ..
make
```

The binaries will be in the `src` folder when you are complete.

```bash
cd src
./BlogCoinDaemon --version
```

#### Windows

##### Prerequisites

You can build for 32-bit or 64-bit Windows. **If you're not sure, pick 64-bit.**

- Install [Visual Studio 2017 Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&page=inlineinstall)
- When installing Visual Studio, it is **required** that you install **Desktop development with C++**
- Install the latest version of Boost (currently Boost 1.68). Select the appropriate version for your system:
  - [Boost 64-bit](https://bintray.com/boostorg/release/download_file?file_path=1.68.0%2Fbinaries%2Fboost_1_68_0-msvc-14.1-64.exe)
  - [Boost 32-bit](https://bintray.com/boostorg/release/download_file?file_path=1.68.0%2Fbinaries%2Fboost_1_68_0-msvc-14.1-32.exe)
- Install the latest full version of OpenSSL (currently OpenSSL 1.1.1b). Select the appropriate version for your system:
  - [OpenSSL 64-bit](https://slproweb.com/download/Win64OpenSSL-1_1_1c.exe)
  - [OpenSSL 32-bit](https://slproweb.com/download/Win32OpenSSL-1_1_1c.exe)

##### Building

For 64-bit:
- From the start menu, open 'x64 Native Tools Command Prompt for vs2017'.

```cmd
cd <your_turtlecoin_directory>
mkdir build
cd build
set PATH="C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin";%PATH%
cmake -G "Visual Studio 15 2017 Win64" .. -DBOOST_ROOT=C:/local/boost_1_68_0
MSBuild TurtleCoin.sln /p:Configuration=Release /m
```

For 32-bit:
- From the start menu, open 'x86 Native Tools Command Prompt for vs2017'.

```cmd
cd <your_blogcoin_directory>
mkdir build
cd build
set PATH="C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin";%PATH%
cmake -G "Visual Studio 15 2017" .. -DBOOST_ROOT=C:/local/boost_1_68_0
MSBuild TurtleCoin.sln /p:Configuration=Release /p:Platform=Win32 /m
```

The binaries will be in the `src/Release` folder when you are complete.

```cmd
cd src\Release
BlogCoinDaemon.exe --version
```


#### Thanks
Cryptonote Developers, Bytecoin Developers, Monero Developers, Forknote Project, TurtleCoin Devs & Community, BlogCoin Community

### Copypasta for license when editing files

Hello BlogCoin contributor, thanks for forking and sending back Pull Requests. Extensive docs about contributing are in the works or elsewhere. For now this is the bit we need to get into all the files we touch. Please add it to the top of the files, see [src/CryptoNoteConfig.h](https://github.com/turtlecoin/turtlecoin/commit/28cfef2575f2d767f6e512f2a4017adbf44e610e) for an example.

```c
// Copyright (c) 2012-2017, The CryptoNote developers, The Bytecoin developers
// Copyright (c) 2014-2018, The Monero Project
// Copyright (c) 2018-2019, The TurtleCoin Developers
// Copyright (c) 2019, The BlogCoin Developers
//
// Please see the included LICENSE file for more information.
```

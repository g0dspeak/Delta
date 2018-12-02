### How To Compile
#### Linux

##### Prerequisites

- You will need the following packages: boost (1.55 or higher), cmake (3.8 or higher), git, gcc/g++ (7.0 or higher) or Clang (6.0 or higher), make, and python. Most of these should already be installed on your system.
- For Ubuntu: `sudo apt-get install -y build-essential python-dev gcc g++ git cmake libboost-all-dev`
- For CentOS 7 (x64): `yum install git-svn make cmake gcc gcc-c++ libstdc++-static -y`
  - Note for CentOS 7: to install later version of boost devel:
  - `wget https://phoenixnap.dl.sourceforge.net/project/boost/boost/1.58.0/boost_1_58_0.tar.gz`
  - `tar -xzf boost_1_58_0.tar.gz`
  - `./bootstrap.sh --prefix=/opt/boost`
  - `./b2 install --prefix=/opt/boost --with=all`

##### Building

- `git clone https://github.com/wrkzdev/wrkzcoin`
- `cd wrkzcoin`
- `chmod +x ./external/rocksdb/build_tools/build_detect_platform`
- `chmod +x ./external/rocksdb/build_tools/version.sh`
- `mkdir build && cd $_`
- `cmake ..`
- Or `cmake -DBOOST_ROOT=/opt/boost ..` for CentOS 7
- `make`

#### Apple

##### Prerequisites

- Install Homebrew https://brew.sh/ (if you don't have it)
- Install [cmake](https://cmake.org/). See [here](https://stackoverflow.com/questions/23849962/cmake-installer-for-mac-fails-to-create-usr-bin-symlinks) if you are unable call `cmake` from the terminal after installing.
- Install the [boost](http://www.boost.org/) libraries. Either compile boost manually or run `brew install boost`.
- Install XCode and Developer Tools.

##### Building using Clang

- `which brew || /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
- `brew install --force cmake boost llvm`
- `export CC=/usr/local/opt/llvm/bin/clang`
- `export CXX=/usr/local/opt/llvm/bin/clang++`
- `git clone https://github.com/wrkzdev/wrkzcoin`
- `cd wrkzcoin`
- `chmod +x ./external/rocksdb/build_tools/build_detect_platform`
- `chmod +x ./external/rocksdb/build_tools/version.sh`
- `mkdir build && cd $_`
- `cmake ..` or `cmake -DBOOST_ROOT=<path_to_boost_install> ..` when building
  from a specific boost install. If you used brew to install boost, your path is most likely `/usr/local/include/boost.`
- `make`

##### Building using GCC

- `which brew || /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
- `brew install --force cmake boost llvm gcc@8`
- `export CC=gcc-8`
- `export CXX=g++-8`
- `git clone https://github.com/wrkzdev/wrkzcoin`
- `cd wrkzcoin`
- `chmod +x ./external/rocksdb/build_tools/build_detect_platform`
- `chmod +x ./external/rocksdb/build_tools/version.sh`
- `mkdir build && cd $_`
- `cmake ..` or `cmake -DBOOST_ROOT=<path_to_boost_install> ..` when building
  from a specific boost install. If you used brew to install boost, your path is most likely `/usr/local/include/boost.`
- `make`

The binaries will be in `./src` after compilation is complete.

Run `./src/Wrkzd` to connect to the network and let it sync (it may take a while).

#### Windows 10

##### Prerequisites
- Install [Visual Studio 2017 Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15&page=inlineinstall)
- When installing Visual Studio, it is **required** that you install **Desktop development with C++** and the **VC++ v140 toolchain** when selecting features. The option to install the v140 toolchain can be found by expanding the "Desktop development with C++" node on the right. You will need this for the project to build correctly.
- Install [Boost 1.59.0](https://sourceforge.net/projects/boost/files/boost-binaries/1.59.0/), ensuring you download the installer for MSVC 14.

##### Building

- From the start menu, open 'x64 Native Tools Command Prompt for vs2017'.
- `cd <your_wrkzcoin_directory>`
- `mkdir build`
- `cd build`
- Set the PATH variable for cmake: ie. `set PATH="C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin";%PATH%`
- `cmake -G "Visual Studio 14 Win64" .. -DBOOST_ROOT=C:/local/boost_1_59_0` (Or your boost installed dir.)
- `MSBuild WrkzCoin.sln /p:Configuration=Release /m`
- If all went well, it will complete successfully, and you will find all your binaries in the '..\build\src\Release' directory.
- Additionally, a `.sln` file will have been created in the `build` directory. If you wish to open the project in Visual Studio with this, you can.

#### Sync
For faster sync, please use checkpoints: https://github.com/wrkzdev/wrkzcoin-checkpoints

#### Thanks
Cryptonote Developers, Bytecoin Developers, Monero Developers, Forknote Project, TurtleCoin Project

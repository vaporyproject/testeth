# testeth - Ethereum consensus test generator.

This repository contains testeth, an Ethereum consensus test generator.

## Contact

[![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg)](https://gitter.im/testeth/Lobby)
[![GitHub Issues](https://img.shields.io/github/issues-raw/badges/shields.svg)](https://github.com/ethereum/testeth/issues)

## Difference from cpp-ethereum

Currently the repository is almost identical to cpp-ethereum
* testeth will drop MacOS and Windows supports
* testeth will drop commands except `eth` and `testeth`
* testeth will drop supports for key management
* testeth will drop key management features except needed for generating tests

## Building from source

### Get the source code

Git and GitHub is used to maintain the source code. Clone the repository by:

```shell
git clone --recursive https://github.com/ethereum/testeth.git
cd testeth
```

The `--recursive` option is important. It orders git to clone additional 
submodules which are required to build the project.
If you missed it you can correct your mistake with command 
`git submodule update --init`.

### Install CMake

CMake is used to control the build configuration of the project. Quite recent 
version of CMake is required 
(at the time of writing [3.4.3 is the minimum](CMakeLists.txt#L25)).
We recommend installing CMake by downloading and unpacking the binary 
distribution  of the latest version available on the 
[**CMake download page**](https://cmake.org/download/).

The CMake package available in your operating system can also be installed
and used if it meets the minimum version requirement.

> **Alternative method**
>
> The repository contains the
[scripts/install_cmake.sh](scripts/install_cmake.sh) script that downloads 
> a fixed version of CMake and unpacks it to the given directory prefix. 
> Example usage: `scripts/install_cmake.sh --prefix /usr/local`.

### Install dependencies (Linux, macOS)

The following *libraries* are required to be installed in the system in their
development variant:

- leveldb

They usually can be installed using system-specific package manager.
Examples for some systems:

Operating system | Installation command
---------------- | --------------------
Debian-based     | `sudo apt-get install libleveldb-dev`
RedHat-based     | `dnf install leveldb-devel`
macOS            | `brew install leveldb`


We also support a "one-button" shell script 
[scripts/install_deps.sh](scripts/install_deps.sh)
which attempts to aggregate dependencies installation instructions for Unix-like
operating systems. It identifies your distro and installs the external packages.
Supporting the script is non-trivial task so please [inform us](#contact)
if it does not work for your use-case.

### Install dependencies (Windows)

We provide prebuilt dependencies required to build the project. Download them
with the [scripts/install_deps.bat](scripts/install_deps.bat) script.

```shell
scripts/install_deps.bat
```

### Build

Configure the project build with the following command. It will create the 
`build` directory with the configuration.

```shell
mkdir build; cd build  # Create a build directory.
cmake ..               # Configure the project.
cmake --build .        # Build all default targets.
```

On **Windows** Visual Studio 2015 is required. You should generate Visual Studio 
solution file (.sln) for 64-bit architecture by adding 
`-G "Visual Studio 14 2015 Win64"` argument to the CMake configure command.
After configuration is completed the `cpp-ethereum.sln` can be found in the
`build` directory.

```shell
cmake .. -G "Visual Studio 14 2015 Win64"
```

## Testing

To run the tests, make sure you clone https://github.com/ethereum/tests and point the environment variable
`ETHEREUM_TEST_PATH` to that path.

## Documentation

- [Internal documentation for developers](doc/index.rst).

## License

[![License](https://img.shields.io/github/license/ethereum/testeth.svg)](LICENSE)

All contributions are made under the [GNU General Public License v3](https://www.gnu.org/licenses/gpl-3.0.en.html). See [LICENSE](LICENSE).

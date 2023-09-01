# Electrum-FEC - Lightweight Ferrite client

> Ferrite lightweight wallet based on Electrum-LTC and Electrum codebase.<br>

### <a href="https://github.com/koh-gt/electrum-fec/releases/tag/v1.0.0" target="_blank"><img width=512 src="https://github.com/koh-gt/ferrite-core/assets/101822992/e0a14905-5779-437b-b936-30fa7361342c" /></a>

## Community group links
| [![telegram-logo](https://raw.githubusercontent.com/gauravghongde/social-icons/9d939e1c5b7ea4a24ac39c3e4631970c0aa1b920/SVG/Color/Telegram.svg)](https://t.me/ferrite_core) [Ferrite Core ](https://t.me/ferrite_core) | [![reddit-logo](https://raw.githubusercontent.com/gauravghongde/social-icons/9d939e1c5b7ea4a24ac39c3e4631970c0aa1b920/SVG/Color/Reddit.svg)](https://www.reddit.com/r/Ferritecoin) [r/Ferritecoin](https://www.reddit.com/r/Ferritecoin) | [![discord-logo](https://raw.githubusercontent.com/gauravghongde/social-icons/9d939e1c5b7ea4a24ac39c3e4631970c0aa1b920/SVG/Color/Discord.svg)](https://discord.gg/qKgF5xhS5p) [Discord](https://discord.gg/qKgF5xhS5p) | [![twitter-logo](https://raw.githubusercontent.com/gauravghongde/social-icons/9d939e1c5b7ea4a24ac39c3e4631970c0aa1b920/SVG/Color/Twitter.svg)](https://twitter.com/ferritecoin) [Twitter](https://twitter.com/ferritecoin) |
|--|--|--|--|

## Build guide
``` bash
# You will need Docker -
sudo snap install docker

git clone https://github.com/koh-gt/electrum-fec
sudo chmod +x -R electrum-fec

# Linux
cd electrum-fec/contrib/build-linux/appimage
./build.sh

# Windows
sudo apt-get install -y upx
cd electrum-fec/contrib/build-wine
./build.sh

# Android (Incomplete)
cd electrum-fec/contrib/android
## ARM 64-bit
./build.sh qml arm64-v8a release-unsigned
## x86 Android
./build.sh qml x86 release-unsigned
## Legacy Android
./build.sh qml arm64-v8a release-unsigned

```

Common distutils error - Python  
`sudo apt install python3-distutils-extra`

```
Licence: MIT Licence
Author: Thomas Voegtlin
Port Maintainer: Pooler
Language: Python (>= 3.8)
```

![electrumb_370](https://github.com/koh-gt/electrum-fec/assets/101822992/9b595953-41ce-46ae-b763-7e98f5c8c846)


## Getting started

_(If you've come here looking to simply run Electrum-FEC,
[you may download it here](https://electrum-fec.org/#download).)_

Electrum-FEC itself is pure Python, and so are most of the required dependencies,
but not everything. The following sections describe how to run from source, but here
is a TL;DR:

```
$ sudo apt install python3-pip
$ sudo apt-get install libsecp256k1-0
$ python3 -m pip install --user ".[gui,crypto]"
$ sudo apt-get install python3-pyqt5  # Not pure python - If you want to use the Qt interface, install the Qt dependencies
```

For elliptic curve operations,
[libsecp256k1](https://github.com/bitcoin-core/secp256k1)
is a required dependency:
```
$ sudo apt-get install libsecp256k1-0
```

Alternatively, when running from a cloned repository, a script is provided to build
libsecp256k1 yourself:
```
$ sudo apt-get install automake libtool
$ ./contrib/make_libsecp256k1.sh
```

Due to the need for fast symmetric ciphers,
[cryptography](https://github.com/pyca/cryptography) is required.
Install from your package manager (or from pip):
```
$ sudo apt-get install python3-cryptography
```

For fast blockchain verification,
[scrypt](https://github.com/holgern/py-scrypt) is required.
Install from your package manager (or from pip):
```
$ sudo apt-get install python3-scrypt
```

If you would like hardware wallet support,
[see this](https://github.com/spesmilo/electrum-docs/blob/master/hardware-linux.rst).


### Running from tar.gz

If you downloaded the official package (tar.gz), you can run
Electrum-FEC from its root directory without installing it on your
system; all the pure python dependencies are included in the 'packages'
directory. To run Electrum-FEC from its root directory, just do:
```
$ ./run_electrum
```

You can also install Electrum-FEC on your system, by running this command:
```
$ sudo apt-get install python3-setuptools python3-pip
$ python3 -m pip install --user .
```

This will download and install the Python dependencies used by
Electrum-FEC instead of using the 'packages' directory.
It will also place an executable named `electrum-fec` in `~/.local/bin`,
so make sure that is on your `PATH` variable.


### Development version (git clone)

_(For OS-specific instructions, see [here for Windows](contrib/build-wine/README_windows.md),
and [for macOS](contrib/osx/README_macos.md))_

Check out the code from GitHub:
```
$ git clone https://github.com/pooler/electrum-fec.git
$ cd electrum-fec
$ git submodule update --init
```

Run install (this should install dependencies):
```
$ python3 -m pip install --user -e .
```

Create translations (optional):
```
$ sudo apt-get install python-requests gettext
$ ./contrib/pull_locale
```

Finally, to start Electrum-FEC:
```
$ ./run_electrum
```

### Run tests

Run unit tests with `pytest`:
```
$ pytest electrum_fec/tests -v
```

To run a single file, specify it directly like this:
```
$ pytest electrum_fec/tests/test_bitcoin.py -v
```

## Creating Binaries

- [Linux (tarball)](contrib/build-linux/sdist/README.md)
- [Linux (AppImage)](contrib/build-linux/appimage/README.md)
- [macOS](contrib/osx/README.md)
- [Windows](contrib/build-wine/README.md)
- [Android](contrib/android/Readme.md)


## Contributing

Any help testing the software, reporting or fixing bugs, reviewing pull requests
and recent changes, writing tests, or helping with outstanding issues is very welcome.
Implementing new features, or improving/refactoring the codebase, is of course
also welcome, but to avoid wasted effort, especially for larger changes,
we encourage discussing these on the issue tracker first.

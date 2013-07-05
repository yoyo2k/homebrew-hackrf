# HackRF OSX Install

This will walk you through getting HackRF to work on OSX. It is really just an adaptation of the awesome collection of [Homebrew](https://github.com/mxcl/homebrew) recipes from [Titanous](https://github.com/titanous/homebrew-gnuradio) for getting GNU Radio running on OSX.

## Installation

These steps have been tested on Mountain Lion 10.8.4 with Xcode 4.6.3.

- Install [Homebrew](http://brew.sh/) if you haven't already

  ```sh
  ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
  ```
- After that is done run the following to make sure you have no issues with your setup, cleanup anything it catches

  ```sh
  brew doctor
  ```

- Add this line to your profile (ie `~/.profile` or `~/.bash_profile` or `~/.zshenv`) and reload
  your profile (`source ~/.profile` or `exec $SHELL`)

  ```sh
  export PATH=/usr/local/sbin:/usr/local/bin:$PATH
  ```

- Install the python package prerequisites

  ```sh
  brew install python gfortran swig
  ```

- Install the prerequisite python packages

  ```sh
  pip install numpy Cheetah lxml
  pip install https://github.com/scipy/scipy/archive/v0.12.0.tar.gz
  export PKG_CONFIG_PATH="/usr/x11/lib/pkgconfig" 
  pip install https://downloads.sourceforge.net/project/matplotlib/matplotlib/matplotlib-1.2.1/matplotlib-1.2.1.tar.gz
  ```

- Install `wxmac` 2.9 with python bindings

  ```sh
  brew install wxmac --python
  ```
- Install GCC 4.2

  ```sh
  brew update
  brew tap homebrew/dupes
  brew install apple-gcc42
  ```

- Install gnuradio 

  ```sh
  brew tap robotastic/homebrew-hackrf
  brew install gnuradio --with-qt
  ```

- Create the `~/.gnuradio/config.conf` config file for custom block support and add this into it

  ```ini
  [grc]
  local_blocks_path=/usr/local/share/gnuradio/grc/blocks
  ```

- Install HackRF & RTL-SDR related blocks

  ```sh
  brew install rtlsdr gr-osmosdr gr-baz --HEAD
  ```

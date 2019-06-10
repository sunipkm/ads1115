# ADS1115 Driver for Linux

I2C Interface driver for [Texas Instruments ADS1115 ADC](http://www.ti.com/lit/ds/symlink/ads1113.pdf).

## How to get:

On command line, execute `git clone https://github.com/sunipkmukherjee/ads1115_linux`

## How to build:

After cloning the repository, `cd` into the directory and execute `make`.
This will build the shared library `libads1115.so` that you can link with other executables in the `build` directory, along with a test
program.
The shared library can be installed (default location `/usr/local`) by executing `make install` with required permissions.
The example program can be executed by running `sudo make test`.

You can execute `make clean` to delete the objects, and `make spotless` to restore the directory to original state.
You can execute `make uninstall` with appropriate permissions to delete the installed library from default location.

By default, the library is built to access I2C bus using `/dev/i2c-1` which is the default I2C bus address on
a Raspberry Pi. However, this address can be changed in the `I2C_FILE` variable in `include/libads1115.h` or passed along at compile time.

Note: Since the variable is passed to the preprocessor through make, it should be in the following format:
```
make CXXFLAGS="-DI2C_FILE=\\\"/path/to/i2c\\\""
```
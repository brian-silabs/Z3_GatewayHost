# Z3 GatewayHost

This repository holds documentation and implementation on how to create a Linux based Zigbee 3.0 Gateway 

In order to proceed, you will need to download EmberZNet SDK through Simplicity Studio
The SDK's access can only be requested using the serial number coming from this development kit :
[SLWSTK6000B](https://www.silabs.com/development-tools/wireless/zigbee/efr32mg-zigbee-thread-starter-kit)

At the time of writing, this is done using Simplicity Studio v4 and GSDK 2.7.8

{% include list.liquid all=true %}

## Description ##
Zigbee 3.0 Gateway Host implementation. Connects to an EZSP NCP target
This project implements most of HA profiles a Gateway must on Endpoint 1
It also acts as a Green Power Combo, hence can handle Green Power Devices on its network

It has to be used with [that NCP implementation](https://github.com/brian-silabs/ncp-uart-no-fc-115200)


## Build Instructions 
You will need to add 2 files to Silicon Labs' SDK to build the project
The 2 rijndael*.c files are open source files to be downloaded (those are not Silabs copyright, hence not included in SDK purposefully) and copied to the folder developer/sdks/gecko_sdk_suite/vX.X/platform/base/hal/micro/generic/aes.

You can find these files [here](https://github.com/gagern/gnulib/tree/master/lib)

Also, 2 Libraries are necessary :
* libncurses
* libreadline

#### On Windows 
Simplest way is by using Cygwin
WSL can be used too if you find the dependencies packages and have a working tty to COM link

Fix an issue in the SDK that causes:  

```console
FATAL: Could not set pipe reader to non-blocking (22): Invalid argument
Z3_GatewayHost: ../../../../../SiliconLabs/SimplicityStudio/v4/developer/sdks/gecko_sdk_suite/v2.7/protocol/zigbee/app/util/serial/linux-serial.c:406: setNonBlockingFD: Assertion `false' failed.
Aborted (core dumped)
```

Edit gecko_sdk_suite/v2.7/protocol/zigbee/app/util/serial/linux-serial.c:406 to:  

```c
int status = fcntl(fd, F_SETFL, flags | O_NONBLOCK);
```

#### On Other platforms (Linux & Darwin) 
Simply run *make -j4 all*

## Run Instructions
Run using *./Z3_GatewayHost -n 0 -p COM14*

## Documentation ##

Official documentation can be found at our [Developer Documentation](https://docs.silabs.com/zigbee/latest/) page.

## Disclaimer ##
Unless otherwise specified in the specific directory, all examples are considered to be EXPERIMENTAL QUALITY which implies that the code provided in the repos has not been formally tested and is provided as-is.  It is not suitable for production environments.  In addition, this code will not be maintained and there may be no bug maintenance planned for these resources.

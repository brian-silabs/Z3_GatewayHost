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
The 2 rijndael*.c files are open source files to be downloaded (those are not Silabs copyright, hence not included in SDK purposefully) and copied to the respective folder …./ developer/sdks/gecko_sdk_suite/v2.6/platform/base/hal/micro/generic/aes.

Also, 2 Libraries are necessary :
* libncurses
* libreadline

# On Windows 
Simplest way is by using Cygwin
WSL can be used too if you find the dependencies packages and have a working tty to COM link

# On Other platforms (Linux & Darwin) 
Simply run *make -j4 all*

## Run Instructions
Run using *./Z3_GatewayHost -n 0 -p COM14*

## Documentation ##

Official documentation can be found at our [Developer Documentation](https://docs.silabs.com/zigbee/latest/) page.

## Disclaimer ##

The Gecko SDK suite supports development with Silicon Labs IoT SoC and module devices. Unless otherwise specified in the specific directory, all examples are considered to be EXPERIMENTAL QUALITY which implies that the code provided in the repos has not been formally tested and is provided as-is.  It is not suitable for production environments.  In addition, this code will not be maintained and there may be no bug maintenance planned for these resources. Silicon Labs may update projects from time to time.
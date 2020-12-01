---
sort: 3
---

# Running the example

-   Build and flash an NCP device with its firmware and bootloader
* [NCP for Thunderboard Sense 2](https://github.com/brian-silabs/ncp-uart-no-fc-115200/releases)
* [NCP Bootloader for Thunderboard Sense 2](https://github.com/brian-silabs/bootloader-uart-xmodem-nofc-1115200/releases)

-   Plug the Thunderboard Sense 2 to your computer
-   And simply run the built binary :  

```console
./build/exe/Z3_GatewayHost -n 0 -p ttyACM0
```

-   Use the Z3_GatewayHost sample application

* Create a Network
* Open the network
* Start the find and Bind target procedure  

To do so in the Gateway's CLI:
```console
plugin network-creator start 1
plugin network-creator-security open-net
plugin find-and-bind target 1
```

* Get your network information for debugging purposes
```console
info
keys print
```

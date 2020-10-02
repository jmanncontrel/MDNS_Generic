## MDNS_Generic

[![arduino-library-badge](https://www.ardu-badge.com/badge/MDNS_Generic.svg?)](https://www.ardu-badge.com/MDNS_Generic)
[![GitHub release](https://img.shields.io/github/release/khoih-prog/MDNS_Generic.svg)](https://github.com/khoih-prog/MDNS_Generic/releases)
[![GitHub](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/khoih-prog/MDNS_Generic/blob/master/LICENSE)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](#Contributing)
[![GitHub issues](https://img.shields.io/github/issues/khoih-prog/MDNS_Generic.svg)](http://github.com/khoih-prog/MDNS_Generic/issues)
[![star this repo](https://githubbadges.com/star.svg?user=khoih-prog&repo=MDNS_Generic)](https://github.com/khoih-prog/MDNS_Generic)

---

### Why do we need this [MDNS_Generic library](https://github.com/khoih-prog/MDNS_Generic)

MDNS ([**Multicast DNS**](https://en.wikipedia.org/wiki/Multicast_DNS)) is a protocol to resolve **hostnames to IP addresses** within small networks that do not include a local name server. It is a zero-configuration service, using essentially the same programming interfaces, packet formats and operating semantics as the unicast Domain Name System (DNS).

The mDNS protocol, published as [RFC 6762](https://tools.ietf.org/html/rfc6762), uses IP multicast User Datagram Protocol (UDP) packets, and is implemented by the [Apple Bonjour](https://en.wikipedia.org/wiki/Bonjour_(software)) and open source [Avahi software packages](https://en.wikipedia.org/wiki/Avahi_(software)).

mDNS can work in conjunction with DNS Service Discovery (DNS-SD), a companion zero-configuration networking technique specified separately in [RFC 6763](https://tools.ietf.org/html/rfc6763).


This [MDNS_Generic library](https://github.com/khoih-prog/MDNS_Generic) is based on and modified from [Dario Pennisi's ArduinoMDNS Library](https://github.com/arduino-libraries/ArduinoMDNS) to provide support to many more boards, such as **Arduino SAMD21, Adafruit SAMD21/SAMD51, Seeeduino SAMD21/SAMD51, nRF52, STM32F/L/H/G/WB/MP1, Teensy, SAM DUE, AVR Mega, etc.** and enable those boards to use MDNS services. The currently supported modules/shield is **W5x00 using Ethernet, EthernetLarge, Ethernet2 or Ethernet3 library**. 

- **Ethernet2 Library is also supported after applying the fix to add Multicast feature**. See [Libraries' Patches](https://github.com/khoih-prog/EthernetWebServer#libraries-patches)
  - ENC28J60 using EthernetENC or UIPEthernet library is not supported as UDP Multicast is not available by design.
  - LAN8742A using STM32Ethernet / STM32 LwIP libraries is not supported as UDP Multicast is not enabled by design, unless you modify the code to add support.

The **WiFiNINA modules/shields are not yet supported** as library modifications are needed.

---

### New in v1.0.1

1. Add support to **W5x00 using Ethernet2 or Ethernet3 library**
2. Update Platform.ini to support PlatformIO 5.x owner-based dependency declaration.
3. Update Packages' Patches.
4. Update Libraries' Patches for Ethernet2 library to add Multicast feature necessary for this [MDNS_Generic library](https://github.com/khoih-prog/MDNS_Generic)
5. Enhance examples.


#### New in v1.0.0

1. Add support to **nRF52** boards, such as **AdaFruit Feather nRF52832, nRF52840 Express, BlueFruit Sense, Itsy-Bitsy nRF52840 Express, Metro nRF52840 Express, NINA_B302_ublox, NINA_B112_ublox, etc.**.
2. Add support to **SAMD51 (Itsy-Bitsy M4, Metro M4, Grand Central M4, Feather M4 Express, etc.)**.
3. Add support to **SAMD21 (ZERO, MKR, NANO_33_IOT, M0, M0 Pro, AdaFruit CIRCUITPLAYGROUND_EXPRESS, etc.)**.
4. Add support to **Seeeduino SAMD21/SAMD51 boards (SEEED_WIO_TERMINAL, SEEED_FEMTO_M0, SEEED_XIAO_M0, Wio_Lite_MG126, WIO_GPS_BOARD, SEEEDUINO_ZERO, SEEEDUINO_LORAWAN, SEEED_GROVE_UI_WIRELESS, etc.)**
5. Add support to all **STM32F/L/H/G/WB/MP1 (Nucleo-144 NUCLEO_F767ZI, Nucleo-64 NUCLEO_L053R8, etc.)**
6. Add support to **Teensy (4.1, 4.0, 3.x, Teensy++ 2.0, Teensy 2.0, etc.)**
7. Add sample Packages Patches for **STM32F/L/H/G/WB/MP1**
8. Add Library Patches for Ethernet.
9. Add Packages' Patches for Arduino SAMD21 to fix compiler error issue when using **STL** for Nano-33-IoT, ZERO, MKR, etc.

---
---
 
## Prerequisite

 1. [`Arduino IDE v1.8.13+`](https://www.arduino.cc/en/Main/Software)
 2. [`Arduino AVR core 1.8.3+`](https://github.com/arduino/ArduinoCore-avr) for Arduino AVR boards. Use Arduino Board Manager to install.
 3. [`Teensy core v1.53+`](https://www.pjrc.com/teensy/td_download.html) for Teensy (4.1, 4.0, 3.6, 3.5, 3,2, 3.1, 3.0) boards.
 6. [`Arduino SAM DUE core v1.6.12+`](https://www.arduino.cc/en/Guide/ArduinoDue) for SAM DUE ARM Cortex-M3 boards.
 7. [`Arduino SAMD core v1.8.8+`](https://www.arduino.cc/en/Guide/ArduinoM0) for SAMD ARM Cortex-M0+ boards.
 8. [`Adafruit SAMD core v1.6.3+`](https://www.adafruit.com/) for SAMD ARM Cortex-M0+ and M4 boards (Nano 33 IoT, etc.).
 9. [`Seeeduino SAMD core 1.7.9+`](https://www.seeedstudio.com/) for SAMD21/SAMD51 boards (XIAO M0, Wio Terminal, etc.).
10. [`Adafruit nRF52 v0.21.0+`](https://www.adafruit.com/) for nRF52 boards such as AdaFruit Feather nRF52840 Express, NINA_B302_ublox, NINA_B112_ublox, etc.
11. [`Arduino Core for STM32 v1.9.0+`](https://github.com/khoih-prog/Arduino_Core_STM32) for STM32 boards. To install go to Arduino IDE, select Boards Manager, search for **`STM32`**.
13. Depending on which Ethernet module/shield you're using :
   - [`Ethernet library v2.0.0+`](https://www.arduino.cc/en/Reference/Ethernet) for W5100, W5200 and W5500. **Ready** from v1.0.0.
   - [`EthernetLarge library v2.0.0+`](https://github.com/OPEnSLab-OSU/EthernetLarge) for W5100, W5200 and W5500. **Ready** from v1.0.0.
   - [`Ethernet2 library v1.0.4+`](https://github.com/khoih-prog/Ethernet2) for W5500 (Deprecated, use Arduino Ethernet library). **Ready** from v1.0.1.
   - [`Ethernet3 library v1.5.3+`](https://github.com/sstaub/Ethernet3) for W5500/WIZ550io/WIZ850io/USR-ES1 with Wiznet W5500 chip. **Ready** from v1.0.1.
   - [`STM32Ethernet library v1.2.0+`](https://github.com/stm32duino/STM32Ethernet) for built-in Ethernet LAN8742A on (Nucleo-144, Discovery). To be used with [`STM32duino_LwIP library v2.1.2+`](https://github.com/stm32duino/LwIP). **Not yet ready** in v1.0.1.
14. [`WiFiNINA_Generic library v1.7.1+`](https://github.com/khoih-prog/WiFiNINA_Generic). To install. check [![arduino-library-badge](https://www.ardu-badge.com/badge/WiFiNINA_Generic.svg?)](https://www.ardu-badge.com/WiFiNINA_Generic) if using WiFiNINA for boards such as Nano 33 IoT, nRF52, Teensy, etc. **Not yet ready** in v1.0.1.
15. [`ESP_AT_Lib library v1.0.0+`](https://github.com/khoih-prog/ESP_AT_Lib) if necessary to use ESP8288/ESP32-AT shields. To install, check [![arduino-library-badge](https://www.ardu-badge.com/badge/ESP_AT_Lib.svg?)](https://www.ardu-badge.com/ESP_AT_Lib). **Not yet ready** in v1.0.1.

---

## Installation

### Use Arduino Library Manager
The best and easiest way is to use `Arduino Library Manager`. Search for `MDNS_Generic`, then select / install the latest version.
You can also use this link [![arduino-library-badge](https://www.ardu-badge.com/badge/MDNS_Generic.svg?)](https://www.ardu-badge.com/MDNS_Generic) for more detailed instructions.

### Manual Install

Another way to install is to:

1. Navigate to [MDNS_Generic](https://github.com/khoih-prog/MDNS_Generic) page.
2. Download the latest release `MDNS_Generic-master.zip`.
3. Extract the zip file to `MDNS_Generic-master` directory 
4. Copy whole `MDNS_Generic-master` folder to Arduino libraries' directory such as `~/Arduino/libraries/`.

### VS Code & PlatformIO:

1. Install [VS Code](https://code.visualstudio.com/)
2. Install [PlatformIO](https://platformio.org/platformio-ide)
3. Install **MDNS_Generic** library by using [Library Manager](https://docs.platformio.org/en/latest/librarymanager/). Search for MDNS_Generic in [Platform.io Author's Libraries](https://platformio.org/lib/search?query=author:%22Khoi%20Hoang%22)
4. Use included [platformio.ini](platformio/platformio.ini) file from examples to ensure that all dependent libraries will installed automatically. Please visit documentation for the other options and examples at [Project Configuration File](https://docs.platformio.org/page/projectconf.html)

---
---

### Packages' Patches

 1. **To be able to compile, run and automatically detect and display BOARD_NAME on nRF52840/nRF52832 boards**, you have to copy the whole [nRF52 0.21.0](Packages_Patches/adafruit/hardware/nrf52/0.21.0) directory into Adafruit nRF52 directory (~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0). 

Supposing the Adafruit nRF52 version is 0.21.0. These files must be copied into the directory:
- `~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0/platform.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0/boards.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0/variants/NINA_B302_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0/variants/NINA_B302_ublox/variant.cpp`
- `~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0/variants/NINA_B112_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0/variants/NINA_B112_ublox/variant.cpp`
- **`~/.arduino15/packages/adafruit/hardware/nrf52/0.21.0/cores/nRF5/Udp.h`**

Whenever a new version is installed, remember to copy these files into the new version directory. For example, new version is x.yy.z
These files must be copied into the directory:

- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/platform.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/boards.txt`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B302_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B302_ublox/variant.cpp`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B112_ublox/variant.h`
- `~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/variants/NINA_B112_ublox/variant.cpp`
- **`~/.arduino15/packages/adafruit/hardware/nrf52/x.yy.z/cores/nRF5/Udp.h`**

 2. **To be able to compile and run on Teensy boards**, you have to copy the file [Teensy boards.txt](Packages_Patches/hardware/teensy/avr/boards.txt) into Teensy hardware directory (./arduino-1.8.12/hardware/teensy/avr/boards.txt). 

Supposing the Arduino version is 1.8.12. This file must be copied into the directory:

- `./arduino-1.8.12/hardware/teensy/avr/boards.txt`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `./arduino-x.yy.zz/hardware/teensy/avr/boards.txt`

 3. **To be able to compile and run on SAM DUE boards**, you have to copy the whole [SAM DUE](Packages_Patches/arduino/hardware/sam/1.6.12) directory into Arduino sam directory (~/.arduino15/packages/arduino/hardware/sam/1.6.12). 

Supposing the Arduino SAM core version is 1.6.12. This file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/sam/1.6.12/platform.txt`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/sam/x.yy.zz/platform.txt`

 4. **To be able to compile without error and automatically detect and display BOARD_NAME on Arduino SAMD (Nano-33-IoT, etc) boards**, you have to copy the whole [Arduino SAMD cores 1.8.8](Packages_Patches/arduino/hardware/samd/1.8.8) directory into Arduino SAMD directory (~/.arduino15/packages/arduino/hardware/samd/1.8.8).
 
Supposing the Arduino SAMD version is 1.8.8. These files must be copied into the directory:
- `~/.arduino15/packages/arduino/hardware/samd/1.8.8/platform.txt`
- **`~/.arduino15/packages/arduino/hardware/samd/1.8.8/cores/arduino/Arduino.h`**

Whenever a new version is installed, remember to copy these files into the new version directory. For example, new version is x.yy.z

These files must be copied into the directory:

- `~/.arduino15/packages/arduino/hardware/samd/x.yy.z/platform.txt`
- **`~/.arduino15/packages/arduino/hardware/samd/x.yy.z/cores/arduino/Arduino.h`**
 
 This is mandatory to fix the **notorious Arduino SAMD compiler error**. See [Improve Arduino compatibility with the STL (min and max macro)](https://github.com/arduino/ArduinoCore-samd/pull/399)
 
```
 ...\arm-none-eabi\include\c++\7.2.1\bits\stl_algobase.h:243:56: error: macro "min" passed 3 arguments, but takes just 2
     min(const _Tp& __a, const _Tp& __b, _Compare __comp)
```

Whenever the above-mentioned compiler error issue is fixed with the new Arduino SAMD release, you don't need to copy the `Arduino.h` file anymore.

 5. **To be able to automatically detect and display BOARD_NAME on Adafruit SAMD (Itsy-Bitsy M4, etc) boards**, you have to copy the file [Adafruit SAMD platform.txt](Packages_Patches/adafruit/hardware/samd/1.6.3) into Adafruit samd directory (~/.arduino15/packages/adafruit/hardware/samd/1.6.3). 

Supposing the Adafruit SAMD core version is 1.6.3. This file must be copied into the directory:

- `~/.arduino15/packages/adafruit/hardware/samd/1.6.3/platform.txt`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `~/.arduino15/packages/adafruit/hardware/samd/x.yy.zz/platform.txt`

 6. **To be able to automatically detect and display BOARD_NAME on Seeeduino SAMD (XIAO M0, Wio Terminal, etc) boards**, you have to copy the file [Seeeduino SAMD platform.txt](Packages_Patches/Seeeduino/hardware/samd/1.7.9) into Adafruit samd directory (~/.arduino15/packages/Seeeduino/hardware/samd/1.7.9). 

Supposing the Seeeduino SAMD core version is 1.7.9. This file must be copied into the directory:

- `~/.arduino15/packages/Seeeduino/hardware/samd/1.7.9/platform.txt`

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz
This file must be copied into the directory:

- `~/.arduino15/packages/Seeeduino/hardware/samd/x.yy.zz/platform.txt`

7. **To use Serial1 on some STM32 boards without Serial1 definition (Nucleo-144 NUCLEO_F767ZI, Nucleo-64 NUCLEO_L053R8, etc.) boards**, you have to copy the files [STM32 variant.h](Packages_Patches/STM32/hardware/stm32/1.9.0) into STM32 stm32 directory (~/.arduino15/packages/STM32/hardware/stm32/1.9.0). You have to modify the files corresponding to your boards, this is just an illustration how to do.

Supposing the STM32 stm32 core version is 1.9.0. These files must be copied into the directory:

- `~/.arduino15/packages/STM32/hardware/stm32/1.9.0/variants/NUCLEO_F767ZI/variant.h` for Nucleo-144 NUCLEO_F767ZI.
- `~/.arduino15/packages/STM32/hardware/stm32/1.9.0/variants/NUCLEO_L053R8/variant.h` for Nucleo-64 NUCLEO_L053R8.

Whenever a new version is installed, remember to copy this file into the new version directory. For example, new version is x.yy.zz,
theses files must be copied into the corresponding directory:

- `~/.arduino15/packages/STM32/hardware/stm32/x.yy.zz/variants/NUCLEO_F767ZI/variant.h`
- `~/.arduino15/packages/STM32/hardware/stm32/x.yy.zz/variants/NUCLEO_L053R8/variant.h`

---

### Libraries' Patches

1. If your application requires 2K+ HTML page, the current [`Ethernet library`](https://www.arduino.cc/en/Reference/Ethernet) must be modified if you are using W5200/W5500 Ethernet shields. W5100 is not supported for 2K+ buffer. If you use boards requiring different CS/SS pin for W5x00 Ethernet shield, for example ESP32, ESP8266, nRF52, etc., you also have to modify the following libraries to be able to specify the CS/SS pin correctly.

2. To fix [`Ethernet library`](https://www.arduino.cc/en/Reference/Ethernet), just copy these following files into the [`Ethernet library`](https://www.arduino.cc/en/Reference/Ethernet) directory to overwrite the old files:
- [Ethernet.h](LibraryPatches/Ethernet/src/Ethernet.h)
- [Ethernet.cpp](LibraryPatches/Ethernet/src/Ethernet.cpp)
- [EthernetServer.cpp](LibraryPatches/Ethernet/src/EthernetServer.cpp)
- [w5100.h](LibraryPatches/Ethernet/src/utility/w5100.h)
- [w5100.cpp](LibraryPatches/Ethernet/src/utility/w5100.cpp)

3. To fix [`EthernetLarge library`](https://github.com/OPEnSLab-OSU/EthernetLarge), just copy these following files into the [`EthernetLarge library`](https://github.com/OPEnSLab-OSU/EthernetLarge) directory to overwrite the old files:
- [EthernetLarge.h](LibraryPatches/EthernetLarge/src/EthernetLarge.h)
- [EthernetLarge.cpp](LibraryPatches/EthernetLarge/src/EthernetLarge.cpp)
- [EthernetServer.cpp](LibraryPatches/EthernetLarge/src/EthernetServer.cpp)
- [w5100.h](LibraryPatches/EthernetLarge/src/utility/w5100.h)
- [w5100.cpp](LibraryPatches/EthernetLarge/src/utility/w5100.cpp)

4. To fix [`Ethernet2 library`](https://github.com/khoih-prog/Ethernet2), just copy these following files into the [`Ethernet2 library`](https://github.com/khoih-prog/Ethernet2) directory to overwrite the old files:

- [Ethernet2.h](LibraryPatches/Ethernet2/src/Ethernet2.h)
- [Ethernet2.cpp](LibraryPatches/Ethernet2/src/Ethernet2.cpp)

To add UDP Multicast support, necessary for this [**UPnP_Generic library**](https://github.com/khoih-prog/UPnP_Generic):

- [EthernetUdp2.h](LibraryPatches/Ethernet2/src/EthernetUdp2.h)
- [EthernetUdp2.cpp](LibraryPatches/Ethernet2/src/EthernetUdp2.cpp)

5. To fix [`Ethernet3 library`](https://github.com/sstaub/Ethernet3), just copy these following files into the [`Ethernet3 library`](https://github.com/sstaub/Ethernet3) directory to overwrite the old files:
- [Ethernet3.h](LibraryPatches/Ethernet3/src/Ethernet3.h)
- [Ethernet3.cpp](LibraryPatches/Ethernet3/src/Ethernet3.cpp)

6. ***To be able to compile and run on nRF52 boards with ENC28J60 using UIPEthernet library***, you have to copy these following files into the UIPEthernet `utility` directory to overwrite the old files:

- [UIPEthernet.h](LibraryPatches/UIPEthernet/UIPEthernet.h)
- [UIPEthernet.cpp](LibraryPatches/UIPEthernet/UIPEthernet.cpp)
- [Enc28J60Network.h](LibraryPatches/UIPEthernet/utility/Enc28J60Network.h)
- [Enc28J60Network.cpp](LibraryPatches/UIPEthernet/utility/Enc28J60Network.cpp)

7. To fix [`ESP32 compile error`](https://github.com/espressif/arduino-esp32), just copy the following file into the [`ESP32`](https://github.com/espressif/arduino-esp32) cores/esp32 directory (e.g. ./arduino-1.8.12/hardware/espressif/cores/esp32) to overwrite the old file:
- [Server.h](LibraryPatches/esp32/cores/esp32/Server.h)

---

### Important Notes

1. For **Adafruit nRF52**, use the SPI's  pin as follows:

  - SS/CS     = 10
  - SPI_MOSI  = MO(SI)
  - SPI_MISO  = MI(SO)
  - SPI_SCK   = SCK

2. For **Adafruit SAMD21/SAMD51**, use the SPI's CS/SS pin as follows:

  - Itsy-Bitsy M0/M4, Feather M0 (Express), Hallowing M0 Express, Zero, Metro M0 => use CS = 16 = pin A2
  - Feather M4 (SAMD51)   => use SS/CS = 9
  - Grand Central M4      => use SS/CS = 53
  - Hallowing M4          => use SS/CS = 10
  - Metro M4 AirLift      => use SS/CS = 36

To know the default CS/SS pins of not listed boards, check the related `variant.h` files in 

`~/.arduino15/packages/adafruit/hardware/samd/x.y.zz/variants/board_name/variant.h`

3. For **Arduino SAM DUE**, use the SPI's  pin as follows:

  - SS/CS     = 10
  - SPI_MOSI  = 75 ( pin 4 @ [ICSP connector](pics/ICSP_connector.jpg) )
  - SPI_MISO  = 74 ( pin 1 @ [ICSP connector](pics/ICSP_connector.jpg) )
  - SPI_SCK   = 76 ( pin 3 @ [ICSP connector](pics/ICSP_connector.jpg) )
  
<p align="center">
    <img src="https://github.com/khoih-prog/MDNS_Generic/blob/master/pics/ICSP_connector.jpg">
</p>
  
---

## Basic Usage

### Using the mDNS services:

```c++
EthernetUDP udp;
MDNS mdns(udp);

mdns.begin(Ethernet.localIP(), hostname.c_str() /*"arduino"*/);

void loop()
{
  mdns.run();
}
```

### Specify callback function when resolving host name:

```c++
mdns.setNameResolvedCallback(nameFound);

void nameFound(const char* name, IPAddress ip)
{
  // To process the MDNS resolved name and IP from hostname
}
```

### Specify callback function when discovering offered services:

```c++
mdns.setServiceFoundCallback(serviceFound);

void serviceFound(const char* type, MDNSServiceProtocol /*proto*/, const char* name, IPAddress ip,
                  unsigned short port, const char* txtContent)
{
  // To process the MDNS resolved name, IP, port and txtContent (if available) 
}
```

### To resolve a host name:

```c++
mdns.resolveName(hostName, 5000);
```

### To register a service via mDNS:

```c++
mdns.addServiceRecord("You_Service._http", 80, MDNSServiceTCP);
```


### To discover services

```c++
mdns.startDiscoveringService(serviceName, MDNSServiceTCP, 5000);
```

---

### Examples

1. [DiscoveringServices](examples/Ethernet/DiscoveringServices)
2. [RegisteringServices](examples/Ethernet/RegisteringServices)
3. [RegisteringServicesWithTxtRecord](examples/Ethernet/RegisteringServicesWithTxtRecord)
4. [ResolvingHostNames](examples/Ethernet/ResolvingHostNames)

---

### Example [ResolvingHostNames](examples/Ethernet/ResolvingHostNames)

Please take a look at other examples, as well.

#### 1. File [ResolvingHostNames.ino](examples/Ethernet/ResolvingHostNames/ResolvingHostNames.ino)

```cpp
//  Illustrates how to resolve host names via MDNS (Multicast DNS)

#include "defines.h"

#include <MDNS_Generic.h>

EthernetUDP udp;
MDNS mdns(udp);

void nameFound(const char* name, IPAddress ip);

void setup()
{
  Serial.begin(115200);
  while (!Serial);

  Serial.print("\nStarting ResolvingHostNames on " + String(BOARD_NAME));

#if USE_ETHERNET
  Serial.println(" using W5x00/Ethernet Library");
#elif USE_ETHERNET_LARGE
  Serial.println(" using W5x00/EthernetLarge Library");
#endif

  Serial.println(("========================="));
  Serial.println(("Default SPI pinout:"));
  Serial.print("MOSI:");
  Serial.println(MOSI);
  Serial.print("MISO:");
  Serial.println(MISO);
  Serial.print("SCK:");
  Serial.println(SCK);
  Serial.print("SS:");
  Serial.println(SS);
  Serial.println(("========================="));

  // unknown board, do nothing, use default SS = 10
#ifndef USE_THIS_SS_PIN
  #define USE_THIS_SS_PIN   10    // For other boards
#endif

  Serial.print(("Unknown board setCsPin:"));
  Serial.println(USE_THIS_SS_PIN);

  Ethernet.init (USE_THIS_SS_PIN);

  // start the ethernet connection and the server:
  // Use Static IP
  //Ethernet.begin(mac, ip);
  // Use DHCP dynamic IP and random mac
  uint16_t index = millis() % NUMBER_OF_MAC;

  Ethernet.begin(mac[index]);

  // Just info to know how to connect correctly
  Serial.println("=========================");
  Serial.println("Currently Used SPI pinout:");
  Serial.print("MOSI:");
  Serial.println(MOSI);
  Serial.print("MISO:");
  Serial.println(MISO);
  Serial.print("SCK:");
  Serial.println(SCK);
  Serial.print("SS:");
  Serial.println(SS);
  Serial.println("=========================");

  Serial.print("Using mac index = ");
  Serial.println(index);

  Serial.print("Connected! IP address: ");
  Serial.println(Ethernet.localIP());

  // Initialize the mDNS library. You can now reach or ping this
  // Arduino via the host name "arduino.local", provided that your operating
  // system is mDNS/Bonjour-enabled (such as MacOS X).
  // Always call this before any other method!
  String hostname = String(BOARD_NAME) + "_" + String(index);
  hostname.toLowerCase();
  hostname.replace(" ", "_");
  
  Serial.println("Register host name: " + hostname + ".local");

  mdns.begin(Ethernet.localIP(), hostname.c_str() /*"arduino"*/);

  // We specify the function that the mDNS library will call when it
  // resolves a host name. In this case, we will call the function named
  // "nameFound".
  mdns.setNameResolvedCallback(nameFound);

  Serial.println("Enter a mDNS host name via the Arduino Serial Monitor to have it resolved.");
  Serial.println("Do not postfix the name with \".local\"");
}

void loop()
{
  static char hostName[256];
  //char hostName[512];

  uint8_t length = 0;

  // read in a host name from the Arduino IDE's serial monitor.
  while (Serial.available())
  {
    hostName[length] = Serial.read();
    length = (length + 1) % 256;
    delay(5);
  }

  // Terminal adds "\r\n", need to remove
  if (length > 1)
    length = (length - 2) % 256;

  hostName[length] = '\0';

  // You can use the "isResolvingName()" function to find out whether the
  // mDNS library is currently resolving a host name.
  // If so, we skip this input, since we want our previous request to continue.
  if (!mdns.isResolvingName())
  {
    if (length > 0)
    {
      MDNS_LOGDEBUG3("Receiving len = ", length, ", hostname", hostName);

      Serial.print("Resolving '");
      Serial.print(hostName);
      Serial.println("' via Multicast DNS (Bonjour)...");

      // Now we tell the mDNS library to resolve the host name. We give it a
      // timeout of 5 seconds (e.g. 5000 milliseconds) to find an answer. The
      // library will automatically resend the query every second until it
      // either receives an answer or your timeout is reached - In either case,
      // the callback function you specified in setup() will be called.

      mdns.resolveName(hostName, 5000);
    }
  }

  // This actually runs the mDNS module. YOU HAVE TO CALL THIS PERIODICALLY,
  // OR NOTHING WILL WORK! Preferably, call it once per loop().
  mdns.run();

  //delay(1000);
}

// This function is called when a name is resolved via mDNS/Bonjour. We set
// this up in the setup() function above. The name you give to this callback
// function does not matter at all, but it must take exactly these arguments
// (a const char*, which is the hostName you wanted resolved, and a const
// byte[4], which contains the IP address of the host on success, or NULL if
// the name resolution timed out).
void nameFound(const char* name, IPAddress ip)
{
  if ( (ip[0] != 0) && (ip[1] != 0) && (ip[2] != 0) && (ip[3] != 0) )
  {
    Serial.print("The IP address for '");
    Serial.print(name);
    Serial.print("' is ");
    Serial.println(ip);

    for (int i = 0; i < 4; i++)
    {
      MDNS_LOGDEBUG3("IP[", i, "]=", ip[i]);
    }
  }
  else if (ip[0] == 0)
  {
    Serial.print("Resolving '");
    Serial.print(name);
    Serial.println("' error.");
  }
  else
  {
    Serial.print("Resolving '");
    Serial.print(name);
    Serial.println("' timed out.");
  }
}
```

#### 2. File [defines.h](examples/Ethernet/ResolvingHostNames/defines.h)

```cpp
#ifndef defines_h
#define defines_h

#define MDNS_DEBUG_PORT       Serial

// Debug Level from 0 to 4
#define _MDNS_LOGLEVEL_       1

#if    ( defined(ARDUINO_SAMD_ZERO) || defined(ARDUINO_SAMD_MKR1000) || defined(ARDUINO_SAMD_MKRWIFI1010) \
      || defined(ARDUINO_SAMD_NANO_33_IOT) || defined(ARDUINO_SAMD_MKRFox1200) || defined(ARDUINO_SAMD_MKRWAN1300) || defined(ARDUINO_SAMD_MKRWAN1310) \
      || defined(ARDUINO_SAMD_MKRGSM1400) || defined(ARDUINO_SAMD_MKRNB1500) || defined(ARDUINO_SAMD_MKRVIDOR4000) || defined(__SAMD21G18A__) \
      || defined(ARDUINO_SAMD_CIRCUITPLAYGROUND_EXPRESS) || defined(__SAMD21E18A__) || defined(__SAMD51__) || defined(__SAMD51J20A__) || defined(__SAMD51J19A__) \
      || defined(__SAMD51G19A__) || defined(__SAMD51P19A__) || defined(__SAMD21G18A__) )
  #if defined(ETHERNET_USE_SAMD)
    #undef ETHERNET_USE_SAMD
  #endif
  #define ETHERNET_USE_SAMD      true
  #endif

#if ( defined(NRF52840_FEATHER) || defined(NRF52832_FEATHER) || defined(NRF52_SERIES) || defined(ARDUINO_NRF52_ADAFRUIT) || \
        defined(NRF52840_FEATHER_SENSE) || defined(NRF52840_ITSYBITSY) || defined(NRF52840_CIRCUITPLAY) || defined(NRF52840_CLUE) || \
        defined(NRF52840_METRO) || defined(NRF52840_PCA10056) || defined(PARTICLE_XENON) || defined(NINA_B302_ublox) || defined(NINA_B112_ublox) )
  #if defined(ETHERNET_USE_NRF528XX)
    #undef ETHERNET_USE_NRF528XX
  #endif
  #define ETHERNET_USE_NRF528XX      true
#endif

#if ( defined(ARDUINO_SAM_DUE) || defined(__SAM3X8E__) )
  #if defined(ETHERNET_USE_SAM_DUE)
    #undef ETHERNET_USE_SAM_DUE
  #endif
  #define ETHERNET_USE_SAM_DUE      true
#endif

#if ( defined(STM32F0) || defined(STM32F1) || defined(STM32F2) || defined(STM32F3)  ||defined(STM32F4) || defined(STM32F7) || \
       defined(STM32L0) || defined(STM32L1) || defined(STM32L4) || defined(STM32H7)  ||defined(STM32G0) || defined(STM32G4) || \
       defined(STM32WB) || defined(STM32MP1) )
  #if defined(ETHERNET_USE_STM32)
    #undef ETHERNET_USE_STM32
  #endif
  #define ETHERNET_USE_STM32        true
#endif

#if defined(ETHERNET_USE_SAMD)
  // For SAMD
  
  #if ( defined(ARDUINO_SAMD_ZERO) && !defined(SEEED_XIAO_M0) )
    #define BOARD_TYPE      "SAMD Zero"
  #elif defined(ARDUINO_SAMD_MKR1000)
    #define BOARD_TYPE      "SAMD MKR1000"
  #elif defined(ARDUINO_SAMD_MKRWIFI1010)
    #define BOARD_TYPE      "SAMD MKRWIFI1010"
  #elif defined(ARDUINO_SAMD_NANO_33_IOT)
    #define BOARD_TYPE      "SAMD NANO_33_IOT"
  #elif defined(ARDUINO_SAMD_MKRFox1200)
    #define BOARD_TYPE      "SAMD MKRFox1200"
  #elif ( defined(ARDUINO_SAMD_MKRWAN1300) || defined(ARDUINO_SAMD_MKRWAN1310) )
    #define BOARD_TYPE      "SAMD MKRWAN13X0"
  #elif defined(ARDUINO_SAMD_MKRGSM1400)
    #define BOARD_TYPE      "SAMD MKRGSM1400"
  #elif defined(ARDUINO_SAMD_MKRNB1500)
    #define BOARD_TYPE      "SAMD MKRNB1500"
  #elif defined(ARDUINO_SAMD_MKRVIDOR4000)
    #define BOARD_TYPE      "SAMD MKRVIDOR4000"
  #elif defined(ARDUINO_SAMD_CIRCUITPLAYGROUND_EXPRESS)
    #define BOARD_TYPE      "SAMD ARDUINO_SAMD_CIRCUITPLAYGROUND_EXPRESS"
  #elif defined(ADAFRUIT_FEATHER_M0_EXPRESS)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_FEATHER_M0_EXPRESS"
  #elif defined(ADAFRUIT_METRO_M0_EXPRESS)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_METRO_M0_EXPRESS"
  #elif defined(ADAFRUIT_CIRCUITPLAYGROUND_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_CIRCUITPLAYGROUND_M0"
  #elif defined(ADAFRUIT_GEMMA_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_GEMMA_M0"
  #elif defined(ADAFRUIT_TRINKET_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_TRINKET_M0"
  #elif defined(ADAFRUIT_ITSYBITSY_M0)
    #define BOARD_TYPE      "SAMD21 ADAFRUIT_ITSYBITSY_M0"
  #elif defined(ARDUINO_SAMD_HALLOWING_M0)
    #define BOARD_TYPE      "SAMD21 ARDUINO_SAMD_HALLOWING_M0"
  #elif defined(ADAFRUIT_METRO_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_METRO_M4_EXPRESS"
  #elif defined(ADAFRUIT_GRAND_CENTRAL_M4)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_GRAND_CENTRAL_M4"
  #elif defined(ADAFRUIT_FEATHER_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_FEATHER_M4_EXPRESS"
  #elif defined(ADAFRUIT_ITSYBITSY_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_ITSYBITSY_M4_EXPRESS"
  #elif defined(ADAFRUIT_TRELLIS_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_TRELLIS_M4_EXPRESS"
  #elif defined(ADAFRUIT_PYPORTAL)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYPORTAL"
  #elif defined(ADAFRUIT_PYPORTAL_M4_TITANO)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYPORTAL_M4_TITANO"
  #elif defined(ADAFRUIT_PYBADGE_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYBADGE_M4_EXPRESS"
  #elif defined(ADAFRUIT_METRO_M4_AIRLIFT_LITE)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_METRO_M4_AIRLIFT_LITE"
  #elif defined(ADAFRUIT_PYGAMER_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYGAMER_M4_EXPRESS"
  #elif defined(ADAFRUIT_PYGAMER_ADVANCE_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYGAMER_ADVANCE_M4_EXPRESS"
  #elif defined(ADAFRUIT_PYBADGE_AIRLIFT_M4)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_PYBADGE_AIRLIFT_M4"
  #elif defined(ADAFRUIT_MONSTER_M4SK_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_MONSTER_M4SK_EXPRESS"
  #elif defined(ADAFRUIT_HALLOWING_M4_EXPRESS)
    #define BOARD_TYPE      "SAMD51 ADAFRUIT_HALLOWING_M4_EXPRESS"
  #elif defined(SEEED_WIO_TERMINAL)
    #define BOARD_TYPE      "SAMD SEEED_WIO_TERMINAL"
  #elif defined(SEEED_FEMTO_M0)
    #define BOARD_TYPE      "SAMD SEEED_FEMTO_M0"
  #elif defined(SEEED_XIAO_M0)
    #define BOARD_TYPE      "SAMD SEEED_XIAO_M0"
    #define USE_THIS_SS_PIN       A1
    #warning define SEEED_XIAO_M0 USE_THIS_SS_PIN == A1
  #elif defined(Wio_Lite_MG126)
    #define BOARD_TYPE      "SAMD SEEED Wio_Lite_MG126"
  #elif defined(WIO_GPS_BOARD)
    #define BOARD_TYPE      "SAMD SEEED WIO_GPS_BOARD"
  #elif defined(SEEEDUINO_ZERO)
    #define BOARD_TYPE      "SAMD SEEEDUINO_ZERO"
  #elif defined(SEEEDUINO_LORAWAN)
    #define BOARD_TYPE      "SAMD SEEEDUINO_LORAWAN"
  #elif defined(SEEED_GROVE_UI_WIRELESS)
    #define BOARD_TYPE      "SAMD SEEED_GROVE_UI_WIRELESS"
  #elif defined(__SAMD21E18A__)
    #define BOARD_TYPE      "SAMD21E18A"
  #elif defined(__SAMD21G18A__)
    #define BOARD_TYPE      "SAMD21G18A"
  #elif defined(__SAMD51G19A__)
    #define BOARD_TYPE      "SAMD51G19A"
  #elif defined(__SAMD51J19A__)
    #define BOARD_TYPE      "SAMD51J19A"
  #elif defined(__SAMD51J20A__)
    #define BOARD_TYPE      "SAMD51J20A"
  #elif defined(__SAM3X8E__)
    #define BOARD_TYPE      "SAM3X8E"
  #elif defined(__CPU_ARC__)
    #define BOARD_TYPE      "CPU_ARC"
  #elif defined(__SAMD51__)
    #define BOARD_TYPE      "SAMD51"
  #else
    #define BOARD_TYPE      "SAMD Unknown"
  #endif

#elif (ETHERNET_USE_SAM_DUE)
  #define BOARD_TYPE      "SAM DUE"

#elif (ETHERNET_USE_NRF528XX)

  #if defined(NRF52840_FEATHER)
    #define BOARD_TYPE      "NRF52840_FEATHER"
  #elif defined(NRF52832_FEATHER)
    #define BOARD_TYPE      "NRF52832_FEATHER"
  #elif defined(NRF52840_FEATHER_SENSE)
    #define BOARD_TYPE      "NRF52840_FEATHER_SENSE"
  #elif defined(NRF52840_ITSYBITSY)
    #define BOARD_TYPE      "NRF52840_ITSYBITSY"
  #elif defined(NRF52840_CIRCUITPLAY)
    #define BOARD_TYPE      "NRF52840_CIRCUITPLAY"
  #elif defined(NRF52840_CLUE)
    #define BOARD_TYPE      "NRF52840_CLUE"
  #elif defined(NRF52840_METRO)
    #define BOARD_TYPE      "NRF52840_METRO"
  #elif defined(NRF52840_PCA10056)
    #define BOARD_TYPE      "NRF52840_PCA10056"
  #elif defined(NINA_B302_ublox)
    #define BOARD_TYPE      "NINA_B302_ublox"
  #elif defined(NINA_B112_ublox)
    #define BOARD_TYPE      "NINA_B112_ublox"
  #elif defined(PARTICLE_XENON)
    #define BOARD_TYPE      "PARTICLE_XENON"
  #elif defined(ARDUINO_NRF52_ADAFRUIT)
    #define BOARD_TYPE      "ARDUINO_NRF52_ADAFRUIT"
  #else
    #define BOARD_TYPE      "nRF52 Unknown"
  #endif

#elif ( defined(CORE_TEENSY) )
  #if defined(__IMXRT1062__)
    // For Teensy 4.1/4.0
    #define BOARD_TYPE      "TEENSY 4.1/4.0"
  #elif defined(__MK66FX1M0__)
    #define BOARD_TYPE "Teensy 3.6"
  #elif defined(__MK64FX512__)
    #define BOARD_TYPE "Teensy 3.5"
  #elif defined(__MKL26Z64__)
    #define BOARD_TYPE "Teensy LC"
  #elif defined(__MK20DX256__)
    #define BOARD_TYPE "Teensy 3.2" // and Teensy 3.1 (obsolete)
  #elif defined(__MK20DX128__)
    #define BOARD_TYPE "Teensy 3.0"
  #elif defined(__AVR_AT90USB1286__)
    #error Teensy 2.0++ not supported yet
  #elif defined(__AVR_ATmega32U4__)
    #error Teensy 2.0 not supported yet
  #else
    // For Other Boards
    #define BOARD_TYPE      "Unknown Teensy Board"
  #endif

#elif (ETHERNET_USE_STM32)
  #if defined(STM32F0)
    #define BOARD_TYPE  "STM32F0"
  #elif defined(STM32F1)
    #define BOARD_TYPE  "STM32F1"
  #elif defined(STM32F2)
    #define BOARD_TYPE  "STM32F2"
  #elif defined(STM32F3)
    #define BOARD_TYPE  "STM32F3"
  #elif defined(STM32F4)
    #define BOARD_TYPE  "STM32F4"
  #elif defined(STM32F7)
    #define BOARD_TYPE  "STM32F7"
  #elif defined(STM32L0)
    #define BOARD_TYPE  "STM32L0"
  #elif defined(STM32L1)
    #define BOARD_TYPE  "STM32L1"
  #elif defined(STM32L4)
    #define BOARD_TYPE  "STM32L4"
  #elif defined(STM32H7)
    #define BOARD_TYPE  "STM32H7"
  #elif defined(STM32G0)
    #define BOARD_TYPE  "STM32G0"
  #elif defined(STM32G4)
    #define BOARD_TYPE  "STM32G4"
  #elif defined(STM32WB)
    #define BOARD_TYPE  "STM32WB"
  #elif defined(STM32MP1)
    #define BOARD_TYPE  "STM32MP1"
  #else
    #define BOARD_TYPE  "STM32 Unknown"
  #endif

#else
  // For Mega
  #define BOARD_TYPE      "AVR Mega"
#endif

#ifndef BOARD_NAME
  #define BOARD_NAME    BOARD_TYPE
#endif

#include <SPI.h>

// UIPEthernet, Ethernet2, Ethernet3, Ethernet_Shield_W5200, EtherCard, EtherSia libraries are not supported

// To override the default CS/SS pin. Don't use unless you know exactly which pin to use
// You can define here or customize for each board at same place with BOARD_TYPE
// Check @ defined(SEEED_XIAO_M0)
//#define USE_THIS_SS_PIN   22  //21  //5 //4 //2 //15

// Only one of the following to be true.
#define USE_ETHERNET          false //true
#define USE_ETHERNET_LARGE    true
 
#if USE_ETHERNET_LARGE
  #include "EthernetLarge.h"
  #include "EthernetUdp.h"
  #warning Use EthernetLarge lib
#else
  #define USE_ETHERNET          true
  #include "Ethernet.h"
  #warning Use Ethernet lib
#endif

// Enter a MAC address and IP address for your controller below.
#define NUMBER_OF_MAC      20

byte mac[][NUMBER_OF_MAC] =
{
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x01 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x02 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x03 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x04 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x05 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x06 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x07 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x08 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x09 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x0A },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x0B },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x0C },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x0D },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x0E },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x0F },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x10 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x11 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x12 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0x13 },
  { 0xDE, 0xAD, 0xBE, 0xEF, 0xBE, 0x14 },
};

// Select the IP address according to your local network
IPAddress ip(192, 168, 2, 222);

#endif    //defines_h
```

---
---

### Debug Termimal Output Samples

1. This is terminal debug output when running [ResolvingHostNames](examples/Ethernet/ResolvingHostNames) on nRF52 **Adafruit NRF52840_FEATHER EXPRESS with W5500 Ethernet module using EthernetLarge library.**

```
Starting ResolvingHostNames on NRF52840_FEATHER with W5x00 using Ethernet2 Library
=========================
Default SPI pinout:
MOSI:11
MISO:12
SCK:13
SS:10
=========================
[MDNS] Board : NRF52840_FEATHER , setCsPin: 10
=========================
Currently Used SPI pinout:
MOSI:11
MISO:12
SCK:13
SS:10
=========================
Using mac index = 15
Connected! IP address: 192.168.2.158
Register host name: nrf52840_feather_19.local
Enter a mDNS host name via the Arduino Serial Monitor to have it resolved.
Do not postfix the name with ".local"
Resolving 'raspberrypi-02' via Multicast DNS (Bonjour)...
The IP address for 'raspberrypi-02' is 192.168.2.122
Resolving 'raspberrypi-01' via Multicast DNS (Bonjour)...
The IP address for 'raspberrypi-01' is 192.168.2.120
```

2. This is terminal debug output when running [DiscoveringServices](examples/Ethernet/DiscoveringServices) on nRF52 **Adafruit NRF52840_FEATHER EXPRESS with W5500 Ethernet module using EthernetLarge library.**

```
Starting DiscoveringServices on NRF52840_FEATHER with W5x00 using EthernetLarge Library
=========================
Default SPI pinout:
MOSI:25
MISO:24
SCK:26
SS:5
=========================
[MDNS] Board : NRF52840_FEATHER , setCsPin: 10
_pinCS = 0
W5100 init, using SS_PIN_DEFAULT = 10, new ss_pin = 10, W5100Class::ss_pin = 10
W5100::init: W5500, SSIZE =8192
=========================
Currently Used SPI pinout:
MOSI:25
MISO:24
SCK:26
SS:5
=========================
Using mac index = 16
Connected! IP address: 192.168.2.160
Register host name: nrf52840_feather_16.local
Enter a mDNS service name via Serial Monitor to discover instances on the network.
Examples are "_http", "_afpovertcp" or "_ssh" (Note the underscores).
Discovering services of type '_http' via Multi-Cast DNS (Bonjour)...
Found: 'Arduino Bonjour Webserver Example' at 192.168.2.156, port 4 (TCP)
Found: 'Arduino mDNS Webserver Example, Page 2' at 192.168.2.156, port 4 (TCP)
Found: 'Linksys07265' at 192.168.2.12, port 80 (TCP)
Finished discovering services of type _http

```

3. This is terminal debug output when running [ResolvingHostNames](examples/Ethernet/ResolvingHostNames) on SAMD21 **Seeeduino SEEED_XIAO_M0 with W5500 Ethernet module using EthernetLarge library.**

```
Starting ResolvingHostNames on SEEED_XIAO_M0 with W5x00 using EthernetLarge Library
=========================
Default SPI pinout:
MOSI:10
MISO:9
SCK:8
SS:4
=========================
[MDNS] Board : SEEED_XIAO_M0 , setCsPin: 1
_pinCS = 0
W5100 init, using SS_PIN_DEFAULT = 10, new ss_pin = 10, W5100Class::ss_pin = 1
W5100::init: W5500, SSIZE =8192
=========================
Currently Used SPI pinout:
MOSI:10
MISO:9
SCK:8
SS:4
=========================
Using mac index = 0
Connected! IP address: 192.168.2.165
Register host name: seeed_xiao_m0_0.local
Enter a mDNS host name via the Arduino Serial Monitor to have it resolved.
Do not postfix the name with ".local"
Resolving 'raspberrypi-01' via Multicast DNS (Bonjour)...
The IP address for 'raspberrypi-01' is 192.168.2.110
Resolving 'raspberrypi-02' via Multicast DNS (Bonjour)...
The IP address for 'raspberrypi-02' is 192.168.2.112
```

4. This is terminal debug output when running [DiscoveringServices](examples/Ethernet/DiscoveringServices) on STM32 **Nucleo-144 NUCLEO_F767ZI with W5x00 using Ethernet2 Library.**

```
Starting DiscoveringServices on NUCLEO_F767ZI with W5x00 using Ethernet2 Library
=========================
Default SPI pinout:
MOSI:11
MISO:12
SCK:13
SS:10
=========================
[MDNS] Board : NUCLEO_F767ZI , setCsPin: 10
=========================
Currently Used SPI pinout:
MOSI:11
MISO:12
SCK:13
SS:10
=========================
Using mac index = 15
Connected! IP address: 192.168.2.98
Register host name: nucleo_f767zi_15.local
Enter a mDNS service name via Serial Monitor to discover instances on the network.
Examples are "_http", "_afpovertcp" or "_ssh" (Note the underscores).
Discovering services of type '_http' via Multi-Cast DNS (Bonjour)...
Found: 'Arduino mDNS Webserver Example' at 192.168.2.85, port 0 (TCP)
Found: 'Linksys07265' at 192.168.2.12, port 80 (TCP)
Finished discovering services of type _http
```

5. This is terminal debug output when running [ResolvingHostNames](examples/Ethernet/ResolvingHostNames) on STM32 **Nucleo-144 NUCLEO_F767ZI with W5x00 using Ethernet2 Library.**

```
Starting ResolvingHostNames on NUCLEO_F767ZI with W5x00 using Ethernet2 Library
=========================
Default SPI pinout:
MOSI:11
MISO:12
SCK:13
SS:10
=========================
[MDNS] Board : NUCLEO_F767ZI , setCsPin: 10
=========================
Currently Used SPI pinout:
MOSI:11
MISO:12
SCK:13
SS:10
=========================
Using mac index = 15
Connected! IP address: 192.168.2.98
Register host name: nucleo_f767zi_15.local
Enter a mDNS host name via the Arduino Serial Monitor to have it resolved.
Do not postfix the name with ".local"
Resolving 'raspberrypi-02' via Multicast DNS (Bonjour)...
The IP address for 'raspberrypi-02' is 192.168.2.112
Resolving 'raspberrypi-01' via Multicast DNS (Bonjour)...
The IP address for 'raspberrypi-01' is 192.168.2.110
```

---
---

### TO DO

 1. Support more boards.
 2. Support WiFiNINA.
 3. Support ENC28J60 Ethernet.
 4. Support LAN8742A Ethernet.
 5. Support ESP8266/ESP32-AT shields.
 6. Add SSL support to SAMD and nRF52 using WiFiNINA.
 7. Support more non-compatible Ethernet Libraries such as Ethernet2, Ethernet3, Ethernet_Shield_W5200, EtherCard, EtherSia
 8. Add more examples


### DONE

 1. Add support to **Arduino SAMD21 (ZERO, MKR, NANO_33_IOT, etc.)**
 2. Add support to **Adafruit SAMD21 (Itsy-Bitsy M0, Metro M0, Feather M0 Express, etc.)**.
 3. Add support to **Adafruit SAMD51 (Itsy-Bitsy M4, Metro M4, Grand Central M4, Feather M4 Express, etc.)**.
 4. Add support to **Seeeduino SAMD21/SAMD51: LoRaWAN, Zero, Femto M0, XIAO M0, Wio GPS Board, Wio Terminal, Grove UI Wireless, etc.**
 5. Add support to **Adafruit nRF52 ( Feather nRF52832, nRF52840 Express, BlueFruit Sense, Itsy-Bitsy nRF52840 Express, Metro nRF52840 Express, NINA_B302_ublox, NINA_B112_ublox, etc.**.
 6. Add support to SAM DUE.
 7. Add support to **STM32F/L/H/G/WB/MP1.**
 8. Add support to **Ethernet W5x00**, using either [`Ethernet`](https://www.arduino.cc/en/Reference/Ethernet) or [`EthernetLarge`](https://github.com/OPEnSLab-OSU/EthernetLarge) library
 9. Add debugging feature.
10. Add support to **Ethernet W5x00**, using [`Ethernet2`](https://github.com/adafruit/Ethernet2) or [`Ethernet3`](https://github.com/sstaub/Ethernet3) library

---
---

### New in v1.0.1

1. Add support to **W5x00 using Ethernet2 or Ethernet3 library**
2. Update Platform.ini to support PlatformIO 5.x owner-based dependency declaration.
3. Update Packages' Patches.
4. Update Libraries' Patches for Ethernet2 library to add Multicast feature necessary for this [MDNS_Generic library](https://github.com/khoih-prog/MDNS_Generic)
5. Enhance examples.

#### New in v1.0.0

1. Add support to **nRF52** boards, such as **AdaFruit Feather nRF52832, nRF52840 Express, BlueFruit Sense, Itsy-Bitsy nRF52840 Express, Metro nRF52840 Express, NINA_B302_ublox, NINA_B112_ublox, etc.**.
2. Add support to **SAMD51 (Itsy-Bitsy M4, Metro M4, Grand Central M4, Feather M4 Express, etc.)**.
3. Add support to **SAMD21 (ZERO, MKR, NANO_33_IOT, M0, M0 Pro, AdaFruit CIRCUITPLAYGROUND_EXPRESS, etc.)**.
4. Add support to **Seeeduino SAMD21/SAMD51 boards (SEEED_WIO_TERMINAL, SEEED_FEMTO_M0, SEEED_XIAO_M0, Wio_Lite_MG126, WIO_GPS_BOARD, SEEEDUINO_ZERO, SEEEDUINO_LORAWAN, SEEED_GROVE_UI_WIRELESS, etc.)**
5. Add support to all **STM32F/L/H/G/WB/MP1 (Nucleo-144 NUCLEO_F767ZI, Nucleo-64 NUCLEO_L053R8, etc.)**
6. Add support to **Teensy (4.1, 4.0, 3.x, Teensy++ 2.0, Teensy 2.0, etc.)**
7. Add sample Packages Patches for **STM32F/L/H/G/WB/MP1**
8. Add Library Patches for Ethernet.
9. Add Packages' Patches for Arduino SAMD21 to fix compiler error issue when using **STL** for Nano-33-IoT, ZERO, MKR, etc.

---

### Issues

Submit issues to: [MDNS_Generic issues](https://github.com/khoih-prog/MDNS_Generic/issues)

---

### Contributions and thanks

1. Based on and modified from [TrippyLighting's EthernetBonjour](https://github.com/TrippyLighting/EthernetBonjour) and [Dario Pennisi's ArduinoMDNS](https://github.com/arduino-libraries/ArduinoMDNS)

<table>
  <tr>
    <td align="center"><a href="https://github.com/TrippyLighting"><img src="https://github.com/TrippyLighting.png" width="100px;" alt="TrippyLighting"/><br /><sub><b>⭐️ TrippyLighting</b></sub></a><br /></td>
    <td align="center"><a href="https://github.com/pnndra"><img src="https://github.com/pnndra.png" width="100px;" alt="pnndra"/><br /><sub><b>⭐️ Dario Pennisi</b></sub></a><br /></td>
  </tr> 
</table>

---

### Contributing

If you want to contribute to this project:

- Report bugs and errors
- Ask for enhancements
- Create issues and pull requests
- Tell other people about this library

---

### License and credits ###

- Most of the credits go to original authors **Georg Kaindl**, [TrippyLighting](https://github.com/TrippyLighting) and [Dario Pennisi](https://github.com/pnndra).

- The library is licensed under [GPLv3.0](http://www.gnu.org/licenses) and [MIT](https://github.com/khoih-prog/MDNS_Generic/blob/master/LICENSE)

---

## Copyright

1. Copyright (C) 2010 Georg Kaindl
2. Copyright (c) 2017 Arduino LLC.  All right reserved.
3. Copyright (c) 2020- Khoi Hoang




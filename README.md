
# ESP32 + KSZ8863RLL Development Board — Wi-Fi and Dual Ethernet in One!

The ESP32-KSZ8863RLL Development Board is an integrated IoT development platform that combines Wi-Fi wireless networking with a wired dual-port Ethernet switch. Based on the powerful dual-core ESP32 MCU and the KSZ8863RLL 2-port switch chip, it is ideal for developing gateways, bridges, smart factories, and robot network equipment. also it makes your custom ethernet daisy-chain networking.


## Screenshots

![App Screenshot_1](https://github.com/user-attachments/assets/cae1f7ba-1907-478e-80b3-5450ef7b9853)

![App Screenshot_2](https://github.com/user-attachments/assets/24f86a0e-1915-4caa-bf30-c487a905d60e)

![App Screenshot_4](https://github.com/user-attachments/assets/8ab7c5d7-32cd-48b2-910b-a4821d4c754a)


## Features


### Key Features

* ESP32 Dual-Core MCU – Integrated Wi-Fi / BLE Support!

* KSZ8863RLL 2-Port Ethernet Switch – Stable Wired Network Configuration

* Ethernet Daisy-Chain Configuration

* I2C / RMII Interface Integration – Fast Communication and Data Processing

* Wi-Fi ↔ Ethernet Bridge Implementation

* Maximized Convenience in Firmware Development – ​​ESP-IDF

* 5 ~ 12V Power Input

### Applications

* IoT Gateway / Sensor Hub

* Industrial Ethernet Bridge

* Smart Home and Smart Factory Network Equipment

* Robot Communication Module / Control Board

* Security and Monitoring Systems

### Development Environment

* Fully Compatible with ESP-IDF (Official SDK)

* FreeRTOS-Based Multitasking Support

* Network Debugging with Wireshark + Serial Debug


## Optimizations

* Modified it more compact size, 70 x 100 mm (see the above scrrenshots)

* Adopted the USB to serial chipset to CH343G, up to 6Mbps

* Modified the USB connector to B type for commercial or industrial purpose

* Modified the external power input connector to 2p XH power connector for commercial or industrial purpose

* reverse porality protection & over current protection in USB power

* reverse porality protection & over current protection in external power

## Buy

For an inquiry, email me jnlee4838@gmail.com

### Korea

* Smartstore: https://smartstore.naver.com/radiosystek

* Coupang: https://shop.coupang.com/radiosystek

### International

* Aliexpress: Not yet

* Amazon: Not yet

## Preparation

We are going to use ESP-IDF version 5.4.2 only in this project, you should install and set up your own IDE, toolchain, etc. and the demo environment is Windows 11 & VS Code.

* Prepare the esp32 ksz8863rll dual ethernet ev kit, 1 usb B to usb A cable, 2 utp cables, one router, one PC

* Set the strap pins config as follows;

![I2C Strap Pin Config](https://github.com/user-attachments/assets/b89a59e5-01f1-4294-bdac-bb289d5b3ce3)

* install VS CODE

* Setup ESP-IDF

* go to https://github.com/espressif/vscode-esp-idf-extension?tab=readme-ov-file#how-to-use and try to follow "Hello world" project first.

* everything is done !!!

## Set-up Flow

### MANUAL WAY

* visit [**here**](https://components.espressif.com/components/espressif/ksz8863/versions/0.2.10/readme) and download the archive. and make it unzip //should be the latest one !!!

* create a folder, "dual_ethernet".

* go back to the downloaded folder, speciallay "examples > simple_switch".

* copy "simple_switch" and paste it to "dual_ethernet > simple_switch".

* execute VS Code.

* goto "File" > "Open folder..." and select the above "dual_ethernet > simple_switch".

* make sure everything is ok

### ESP-IDF

* create a folder, "dual_ethernet".

* execute VS Code goto "File" > "Open folder..." and select the above "dual_ethernet.

* press "F1" and select ">ESP-IDF: Open ESP-IDF Terminal".

* goto ESP-IDF Terminal prompt and type.


```esp-idf
idf.py create-project-from-example "espressif/ksz8863=0.2.10:simple_switch"
```

* close project and exit.

* execute VS Code goto "File" > "Open folder..." and select the above "dual_ethernet > simple_switch".

* make sure everything is ok.


### Next Steps
    
* press left bottom icons step by step.

* Set your project path properly.

* Set your ESP-IDF path properly.

* Set the FW upload interface UART.

* Set the FW upload port COMx depending on your pc.

* Set the target device "esp32" and "ESP32 chip (via ESP Prog)".

* click "SDK Configuration Editor (menuconfig)" and then it takes time and you can see new folders "build" and "managed_compoennts" in the "EXPLORER" window at left side. and also please check the "OUTPUT" window in bottom side of your VS Code that will tell whether your config is correct or not. hopefully no problems at all!

* you could see "SDK Configutation editor" window in your VS Code.

* we will check four parameters only.

    * --> Type "cpu" in the top search box" and find "CPU Frequency" to "240MHz".

    * --> Type "flash" and find "Flash size" to "4M".

    * --> Click "Example Configuration" and find "Enable external RMII clock oscillator" unselect. //it doesn't affect on project conf. but btw we are not using external osciallator.

    * --> Type "eth" and find "Ethernet" and make sure "Support ESP32 internal EMAC controller" is checked and "RMII clock mode: Input RMII clockfrom external"`.

* Done !!! Click "Save".

* Click "build" and try to enjoy a cup of coffee. it takes time depending on your computer performance. anyway, you'd better take a break.

* congrats if you can see a "Memory Type Usage Summary" in "TERMINAL" window. otherwise, you should fix the errors and misconfig...

* click "Flash Device" icon.

* neally done !

* click "Monitor Device" and see what is going on in that "Terminal".


**or please check the video for config and build HERE**

## Console output

the console should be the followings if you have the following connection diagram

* a router <--> port #1 of esp32 ksz8863rll ev kit
              port #2 <--> your PC
* the router should have DHCP server on.

```ESP-IDF MONITOR TERMINAL

ets Jul 29 2019 12:21:46

rst:0x1 (POWERON_RESET),boot:0x12 (SPI_FAST_FLASH_BOOT)
configsip: 0, �ets Jul 29 2019 12:21:46

rst:0x1 (POWERON_RESET),boot:0x12 (SPI_FAST_FLASH_BOOT)
configsip: 0, SPIWP:0xee
clk_drv:0x00,q_drv:0x00,d_drv:0x00,cs0_drv:0x00,hd_drv:0x00,wp_drv:0x00
mode:DIO, clock div:2
load:0x3fff0030,len:6276
load:0x40078000,len:15736
load:0x40080400,len:4
--- 0x40080400: _init at ??:?
load:0x40080404,len:3860
entry 0x4008063c
I (29) boot: ESP-IDF v5.4.2 2nd stage bootloader
I (29) boot: compile time Oct 22 2025 17:19:20
I (29) boot: Multicore bootloader
I (31) boot: chip revision: v3.1
I (34) boot.esp32: SPI Speed      : 40MHz
I (37) boot.esp32: SPI Mode       : DIO
I (41) boot.esp32: SPI Flash Size : 4MB
I (44) boot: Enabling RNG early entropy source...
I (49) boot: Partition Table:
I (51) boot: ## Label            Usage          Type ST Offset   Length
I (58) boot:  0 nvs              WiFi data        01 02 00009000 00006000
I (64) boot:  1 phy_init         RF data          01 01 0000f000 00001000
I (71) boot:  2 factory          factory app      00 00 00010000 00100000
I (77) boot: End of partition table
I (81) esp_image: segment 0: paddr=00010020 vaddr=3f400020 size=158c8h ( 88264) map
I (118) esp_image: segment 1: paddr=000258f0 vaddr=3ff80000 size=0001ch (    28) load
I (119) esp_image: segment 2: paddr=00025914 vaddr=3ffb0000 size=02648h (  9800) load
I (126) esp_image: segment 3: paddr=00027f64 vaddr=40080000 size=080b4h ( 32948) load
I (143) esp_image: segment 4: paddr=00030020 vaddr=400d0020 size=372b4h (225972) map
I (220) esp_image: segment 5: paddr=000672dc vaddr=400880b4 size=0799ch ( 31132) load
I (240) boot: Loaded app from partition at offset 0x10000
I (240) boot: Disabling RNG early entropy source...
I (250) cpu_start: Multicore app
I (259) cpu_start: Pro cpu start user code
I (259) cpu_start: cpu freq: 240000000 Hz
I (259) app_init: Application information:
I (259) app_init: Project name:     ksz8863_simple_switch
I (264) app_init: App version:      1
I (267) app_init: Compile time:     Oct 22 2025 17:18:48
I (272) app_init: ELF file SHA256:  95acbd72a...
I (277) app_init: ESP-IDF:          v5.4.2
I (281) efuse_init: Min chip rev:     v0.0
I (284) efuse_init: Max chip rev:     v3.99
I (288) efuse_init: Chip rev:         v3.1
I (293) heap_init: Initializing. RAM available for dynamic allocation:
I (299) heap_init: At 3FFAE6E0 len 00001920 (6 KiB): DRAM
I (304) heap_init: At 3FFB3A20 len 0002C5E0 (177 KiB): DRAM
I (309) heap_init: At 3FFE0440 len 00003AE0 (14 KiB): D/IRAM
I (314) heap_init: At 3FFE4350 len 0001BCB0 (111 KiB): D/IRAM
I (320) heap_init: At 4008FA50 len 000105B0 (65 KiB): IRAM
I (326) spi_flash: detected chip: generic
I (329) spi_flash: flash io: dio
I (333) main_task: Started on CPU0
I (343) main_task: Calling app_main()
W (343) simple_switch_example: Simple Switch mode Example...

W (343) i2c.master: Please check pull-up resistances whether be connected properly. Otherwise unexpected behavior would happen. For more detailed information, please read docs
W (353) ksz8863_eth: SW reset resets all Global, MAC and PHY registers!
I (363) esp_eth.netif.netif_glue: XX XX XX XX XX XX
I (363) esp_eth.netif.netif_glue: ethernet attached to netif
I (393) simple_switch_example: Ethernet Started
I (393) simple_switch_example: Ethernet Link Up
I (393) simple_switch_example: Ethernet HW Addr XX XX XX XX XX XX
I (393) simple_switch_example: Ethernet Started
I (2393) simple_switch_example: Ethernet Started
I (2393) simple_switch_example: Ethernet Link Up Port 2
I (2393) simple_switch_example: Ethernet HW Addr 00:00:00:00:00:00
I (2393) main_task: Returned from app_main()
I (2393) simple_switch_example: Ethernet Link Up Port 1
I (2393) simple_switch_example: Dynamic MAC Table content:
I (2403) simple_switch_example: Ethernet HW Addr 00:00:00:00:00:00
I (2403) simple_switch_example: valid entries 1
I (2413) simple_switch_example: port 3
I (2423) simple_switch_example: XX XX XX XX XX XX

I (4903) esp_netif_handlers: eth ip: 192.168.1.141, mask: 255.255.255.0, gw: 192.168.1.1
I (4903) simple_switch_example: Ethernet Got IP Address
I (4903) simple_switch_example: ~~~~~~~~~~~
I (4903) simple_switch_example: ETHIP:192.168.1.141
I (4913) simple_switch_example: ETHMASK:255.255.255.0
I (4913) simple_switch_example: ETHGW:192.168.1.1
I (4923) simple_switch_example: ~~~~~~~~~~~
I (7423) simple_switch_example: Dynamic MAC Table content:
I (7423) simple_switch_example: valid entries 3
I (7423) simple_switch_example: port 2
I (7423) simple_switch_example: XX XX XX XX XX XX
I (7423) simple_switch_example: port 1
I (7433) simple_switch_example: XX XX XX XX XX XX
I (7433) simple_switch_example: port 3
I (7443) simple_switch_example: XX XX XX XX XX XX

```
## Test

### Source code "simple_switch_main.c"

Line no. 321

```C
    // Sync semaphore is needed since main task local variables are used during initialization in other tasks
    init_done = xSemaphoreCreateBinary();
    assert(init_done);

    // Periodically print content of Dynamic MAC table
    xTaskCreate(print_dyn_mac, "print_dyn_mac", 4096, p1_eth_handle, 5, NULL);
    xSemaphoreTake(init_done, portMAX_DELAY);
    // Periodically transmit test message
    xTaskCreate(transmit_l2test_msg, "tx_test_msg", 4096, NULL, 4, NULL);

    vSemaphoreDelete(init_done);
```

### ESP-IDF MONITOR Terminal

* The following data should be out every five secs.
```Terminal
I (7423) simple_switch_example: Dynamic MAC Table content:
I (7423) simple_switch_example: valid entries 3
I (7423) simple_switch_example: port 2
I (7423) simple_switch_example: XX XX XX XX XX XX
I (7423) simple_switch_example: port 1
I (7433) simple_switch_example: XX XX XX XX XX XX
I (7433) simple_switch_example: port 3
I (7443) simple_switch_example: XX XX XX XX XX XX
```

### IP Assignment

* Please check wheater your pc has a proper IP from from your router in PowerShell or CMD Terminal.
    ```Terminal
    ipconfig /all
    ```
* You can check all device status from your router's networking status as well

### Wire Shark

#### check source code

Line no. 72

```C
    test_vfs_eth_tap_msg_t test_msg = {
        .header = {
            .src.addr = {0},
            .dest.addr = { 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF }, // broadcast
            .type = ntohs(eth_type_filter),
        },
        .str = "This is ESP32 L2 TAP test msg"
    };
```
it braodcasts the above ethernet frame every two seconds.

* please download "WireShark" and execute it.
* select the "ethernet" to analyze.
* type "ARP" in filter.
* you can find the "ARP" ethernet frames that they are talking each others.
* type "eth.src == xx xx xx xx xx xx" (Port #3) and find a lot of messages...esp32_ksz8863rll_ev_kit is shooting it every two secs.

## Related

Here is another project to check the Throughput of esp32_ksz8863rll_ev_kit by Iperf

[Iperf_esp32_ksz8863rll_ev_kit_README](https://github.com/jnlee4838/Iperf_esp32_ksz8863rll_ev_kit_readme)


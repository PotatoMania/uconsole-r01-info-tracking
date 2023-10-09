# uConsole R01 info tracking

Last updated: 2023-10-09

PR welcomed.

## Basic statistics

When

- Bootloader from CPi's OS image
- Using BSP kernel, tweaked
- Arch Linux userspace(rootfs)

I got:

- Startup time: about 20 seconds
    - Network Manager enabled(disable it cuts 5 seconds)
- Shutdown time: about 13 seconds
- Idle CPU load: around 30%
- Memory usage after boot: less than 70 MB
    - no extra service except Network Manager

## Linux kernel

Here tracks general features. For more detailed features, please refer [page on linux-sunxi.org](https://linux-sunxi.org/Linux_mainlining_effort#Status_Matrix)

Item | BSP(5.4) | Smaeul's fork(6.1) | Mainline(6.5)
:- | :- | :- | :-
USB | ✅ | ✅ | ✅
WiFi | ✅ | ✅ | ✅
Bluetooth | ✅ | ✅ | ✅
LCD (MIPI-DSI)  | ✅ <sup>1,2</sup> | ❌ <sup>4</sup> | ❌ <sup>4</sup>
HDMI            | ✅ <sup>3</sup> | ✅ | ❌
Audio(speaker and 3.5mm)   | ✅ | ❔ | ❔
Hardware video decoding | ⭕ | ❔ | ❔

✅: Tested and known working.  
❌: Tested and known NOT working.  
❔: Not tested and don't know whether working or not.  
⭕: Should work but with addtional program and hard to use with common userspace program.  

Notes:

1. No hardware cursor.
1. No video burst mode support.
1. Need additional program to change output.
1. Tested with CPi's driver patch, along with the timing parameters in the BSP kernel patch, but no output observed, except full screen white flash on driver reload.

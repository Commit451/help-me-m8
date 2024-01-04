# help-me-m8
Help for the Dirtywave M8 setup and troubleshooting on RG351V.

## Guide
The official guide to the Dirtywave M8 can be found here on their site:
https://dirtywave.com/pages/resources-downloads

## RG351V
The console itself can be found [here](https://www.amazon.com/dp/B09CQ1XMX7?th=1). There are other units besides the 351V that you could get, but the 351V is nice because it has two USB-C ports, allowing one to host the Teensy while the other stays open for charging.

## SD Card
The official list of recommended SD cards can be found [here](https://dirtywave.com/pages/recommended-microsd-cards) and specifically [this](https://www.amazon.com/SanDisk-Ultra-UHS-I-Memory-Adapter/dp/B00M55C0NS?th=1) is a great option for cheap.

## Teensy
The Teensy can be found [here](https://www.amazon.com/PJRC-Cortex-M7-Processor-iMXRT1062-Without/dp/B088JY7P2H) on Amazon, you do NOT need the version with pins. Follow the [official headless setup](https://github.com/DirtyWave/M8Docs/blob/main/docs/M8HeadlessSetup.md) on your computer to get the Teensy up and running with your SanDisk SD card. You can also plug your Teensy into your computer via the OTG cable and see its output via https://m8.run/. This is a great way to test things out and gives you a larger screen to work with.

## OTG Cable
A good cable option is found [here](https://www.amazon.com/gp/product/B09DG4DXQC/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&th=1) - a two pack! 1 foot is a bit long, but half a foot is just too short.

## Slot Case
The slot case design can be found [here](https://www.thingiverse.com/thing:4965543). Thanks a bunch to dschroeter for its creation. It can be quite difficult to get the Teensy in there the first time, you may be surprised at the level of force you need to apply. Ask your friend with a 3D printer to print it for you! Or get one on [Etsy](https://www.etsy.com/listing/1417826298/high-quality-teensy-41-m8-headless)

## Adhesion
You can use strips of [this adhesive](https://www.amazon.com/dp/B09FY9MCQB?ref=ppx_yo2ov_dt_b_product_details&th=1) to mount the slot case to the back of the 351V.

## OS
Currently, [ArkOS 2.0](https://github.com/christianhaitian/arkos) is used, specifically the build ArkOS_RK2023_v2.0_10162023. Later builds do have issues with the rg351_m8c specifically because that project uses subdirectories, which are not supported in later ArkOS versions. Newly shipped versions of the RG351V seem to have a different screen than some older modules, so if you are setting things up and see a white screen with a black bar on the side, you have run into [this issue](https://github.com/christianhaitian/arkos/issues/662) and will need to download [this](https://github.com/christianhaitian/arkos/issues/662#issuecomment-1510064072) .dtb file and replace the one in the root of the SD card to get things working.

## RG351 m8c
The RG351V with m8c is currently found [here](https://github.com/jasonporritt/rg351_m8c), but tweaks are needed to make things work. For example, you cannot use m8 firmware greater than 3.0.4 with that project, since it does not compile the latest version of [m8c](https://github.com/laamaa/m8c/) but rather relies on an earlier build. If you want to resolve this, you need to update the submodules via running `git submodule update --recursive` and then following the instructions for installation and setup. Keep in mind that you need to have an internet connection on the RG351 when you first run the setup scripts.

## Acknowledgements
This entire project/experience would not be possible without the great work from Dirtywave and all the help I found in the [Discord](https://discord.gg/WEavjFNYHh). Thanks to christianhaitian for the creation of ArkOS, jasonporritt for creating rg351_m8c and also laamaa for the work on m8c. We all stand on the shoulders of giants.

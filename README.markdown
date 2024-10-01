
  Apple Hardware Test (AHT)
=============================

 Description
-------------

Apple computers ship with a pre-installed suite of hardware diagnostic tools, known as Apple Hardware Test (AHT). In principle you can start them by holding the `D` key while booting. Newer models support holding `⌥+D` to load AHT over the internet. Refer to the official Apple documentation for details: Using AHT on [Intel-based Macs](https://support.apple.com/kb/ht1509), [Mountain Lion](https://support.apple.com/kb/PH11342), [Mavericks](https://support.apple.com/kb/PH14291) and [Yosemite](https://support.apple.com/kb/PH18765). Apple redesigned the AHT, now called [Apple Diagnostics](https://support.apple.com/kb/HT5781), for Macs introduced after June 2013. Consult the [reference codes](https://support.apple.com/en-us/HT203747) to interpret the results.

If however, you reinstalled an older computer from scratch, the diagnostic tools might no longer be available. Unless you have the original disks that came with your computer, there seems to be no way to restore the AHT.

It happens that Apple provides disk images with AHT for most computers, but does not make the links publicly available. Various blogs and forums, mostly [Riven by Five](https://rivenbyfive.blogspot.ch/2012/01/download-and-run-apple-hardware-test.html) and [MacForum.ro](http://arhiva.macforum.ro/comunitate/topic/1194-apple-hardware-test/) have gathered a list of download links. The rest were obtained by scraping `https://download.info.apple.com/Apple_Hardware_Test/` for all the links of the form `0(18|22)-\d{4}-A.dmg`.

Even though there's no guarantee that this list is correct or complete, some links can come in very handy to whoever is trying to debug hardware problems.

You can use the following terminal commands to determine the model and board ID of your computer:

```sh
sysctl hw.model | awk '{ print $2 }'
ioreg -l | awk -F\" '/board-id/ { print $4 }'
```

Download the AHT for your computer model and use the contents to restore the `/System/Library/CoreServices/.diagnostics` folder, then reboot while holding `D` to start the diagnostic tools. Alternatively you may try with a bootable USB stick, as described below. This is also the preferred way on OS X 10.11 or later, where the System Integrity Protection (SIP) no longer allows writing to system folders.

When trying to open an old dmg you may get the error 'legacy image should be converted'. To convert it to a newer format, open Disk Utility, in the menu _Images_ click on _Convert_ and select the dmg to convert and save it under a new name.

Note that there is no one-to-one correspondence between hardware model and AHT. For some models no hardware test could be found, while others seem to have multiple AHT. As the differences are not clear, feel free to try them out, to see which one works best for your hardware.

 Run AHT from a bootable USB stick
-----------------------------------

  * You need a bootable USB stick, for instance using Disk Utility's _Erase_ with `Format: OS X Extended` and `Scheme: GUID Partition Map`. On newer Macs you will need to do this using the command line. Make sure you replace `disk2` with the appropriate disk name. You can find out yours by running `diskutil list`.

```sh
diskutil eraseDisk JHFS+ USBstick GPT disk2
```

  * Let's assume the USB stick is mounted under `/Volumes/USBstick`.
  * Download the AHT for your computer model from the list below.
  * Mount the AHT dmg. Let's refer to the mount point as `/Volumes/AHT`.
  * Copy the AHT to the USB stick and flag it as bootable

```sh
cp -r /Volumes/AHT/System /Volumes/USBstick/
sudo bless --folder /Volumes/USBstick/ --file /Volumes/USBstick/System/Library/CoreServices/.diagnostics/diags.efi --label AHT
```

  * Insert USB stick in the computer to be tested, boot holding the option key and select the AHT.


 Download Links
----------------

### PowerMac

* [PowerMac v1.2.6, PowerMac G4](https://download.info.apple.com/Apple_Hardware_Test/693-3994-A.dmg)
* [PowerMac v2.2.5GMc2](https://download.info.apple.com/Apple_Hardware_Test/018-1594-A.dmg)
* [PowerMac v2.5GMc1](https://download.info.apple.com/Apple_Hardware_Test/018-1880-A.dmg)
* [PowerMac v2.5.2GMc1](https://download.info.apple.com/Apple_Hardware_Test/018-2216-A.dmg)

### PowerBook

* [PowerBook v1.2.3, PowerBook FireWire, PowerBook G4](https://download.info.apple.com/Apple_Hardware_Test/693-4420-A.dmg)
* [PowerBook v2.5.2GMc1](https://download.info.apple.com/Apple_Hardware_Test/018-2120-A.dmg)

### iBook

* [iBook v2.2.1GMc1](https://download.info.apple.com/Apple_Hardware_Test/018-1680-A.dmg)
* [iBook v2.5GMc1](https://download.info.apple.com/Apple_Hardware_Test/018-2056-A.dmg)

### iMac

* [iMac ............................... v2.5.1GMc1](https://download.info.apple.com/Apple_Hardware_Test/018-1879-A.dmg)
* [iMac ............................... v2.5.2GMc5](https://download.info.apple.com/Apple_Hardware_Test/018-2158-A.dmg)
* [iMac ............................... v2.5.3GMc1](https://download.info.apple.com/Apple_Hardware_Test/018-2215-A.dmg)
* [iMac 4,1 ................................ 3A103](https://download.info.apple.com/Apple_Hardware_Test/018-2392-A.dmg)
* [iMac 5,1 ......................... Mac-F4228EC8](https://download.info.apple.com/Apple_Hardware_Test/018-2534-A.dmg)
* [iMac 5,1 ......................... Mac-F42786A9](https://download.info.apple.com/Apple_Hardware_Test/018-2533-A.dmg)
* [iMac 5,2 ......................... Mac-F4218EC8](https://download.info.apple.com/Apple_Hardware_Test/018-2535-A.dmg)
* [iMac 6,1 ......................... Mac-F4218FC8](https://download.info.apple.com/Apple_Hardware_Test/018-2579-A.dmg)
* [iMac 7,1 ......................... Mac-F42386C8](https://download.info.apple.com/Apple_Hardware_Test/018-2845-A.dmg)
* [iMac 8,1 ......................... Mac-F226BEC8](https://download.info.apple.com/Apple_Hardware_Test/022-3936-A.dmg)
* [iMac 8,1 ......................... Mac-F227BEC8](https://download.info.apple.com/Apple_Hardware_Test/022-3937-A.dmg)
* [iMac 9,1 ......................... Mac-F2218EA9](https://download.info.apple.com/Apple_Hardware_Test/022-4297-A.dmg)
* [iMac 9,1 ......................... Mac-F2218EC8](https://download.info.apple.com/Apple_Hardware_Test/022-4293-A.dmg)
* [iMac 9,1 ......................... Mac-F2218FC8](https://download.info.apple.com/Apple_Hardware_Test/022-4294-A.dmg)
* [iMac 10,1 ........................ Mac-F2268CC8](https://download.info.apple.com/Apple_Hardware_Test/022-4451-A.dmg)
* [iMac 10,1 ........................ Mac-F2268CC8](https://download.info.apple.com/Apple_Hardware_Test/022-4647-A.dmg)
* [iMac 10,1 ........................ Mac-F2268DC8](https://download.info.apple.com/Apple_Hardware_Test/022-4452-A.dmg)
* [iMac 10,1 ........................ Mac-F2268DC8](https://download.info.apple.com/Apple_Hardware_Test/022-4644-A.dmg)
* [iMac 11,2 ........................ Mac-F2238AC8](https://download.info.apple.com/Apple_Hardware_Test/022-4703-A.dmg)
* [iMac 11,3 ........................ Mac-F2238BAE](https://download.info.apple.com/Apple_Hardware_Test/022-4776-A.dmg)
* [iMac 12,1 ................ Mac-942B5BF58194151B](https://download.info.apple.com/Apple_Hardware_Test/022-5090-A.dmg)
* [iMac 12,1 ................ Mac-942B5BF58194151B](https://download.info.apple.com/Apple_Hardware_Test/022-5344-A.dmg)
* [iMac 12,2 ................ Mac-942B59F58194171B](https://download.info.apple.com/Apple_Hardware_Test/022-5091-A.dmg)

### Mac Mini

* [Mac Mini ............................. v1.1GMc2](https://download.info.apple.com/Apple_Hardware_Test/018-2079-A.dmg)
* [Mac Mini ............................ 1,1 3A102](https://download.info.apple.com/Apple_Hardware_Test/018-2342-A.dmg)
* [Mac Mini 2,1 ..................... Mac-F4208EAA](https://download.info.apple.com/Apple_Hardware_Test/018-2886-A.dmg)
* [Mac Mini 3,1 ..................... Mac-F22C86C8](https://download.info.apple.com/Apple_Hardware_Test/022-4292-A.dmg)
* [Mac Mini 4,1 ............ Mac-F2208EC8 (Server)](https://download.info.apple.com/Apple_Hardware_Test/022-4739-A.dmg)
* [Mac Mini 4,1 ..................... Mac-F2208EC8](https://download.info.apple.com/Apple_Hardware_Test/022-4706-A.dmg)
* [Mac Mini 5,1 ............. Mac-8ED6AF5B48C039E1](https://download.info.apple.com/Apple_Hardware_Test/022-5207-A.dmg)
* [Mac Mini 5,2 ............. Mac-4BC72D62AD45599E](https://download.info.apple.com/Apple_Hardware_Test/022-5207-A.dmg)

### Mac Pro

* [Mac Pro 1,1 ...................... Mac-F4208DC8](https://download.info.apple.com/Apple_Hardware_Test/018-2769-A.dmg)
* [Mac Pro 2,1 ...................... Mac-F4208DA9](https://download.info.apple.com/Apple_Hardware_Test/018-2667-A.dmg)
* [Mac Pro 3,1 ...................... Mac-F42C88C8](https://download.info.apple.com/Apple_Hardware_Test/018-3273-A.dmg)
* [Mac Pro 3,1 ...................... Mac-F42C88C8](https://download.info.apple.com/Apple_Hardware_Test/022-3843-A.dmg)
* [Mac Pro 3,1 ...................... Mac-F42C88C8](https://download.info.apple.com/Apple_Hardware_Test/022-4020-A.dmg)
* [Mac Pro 4,1 ...................... Mac-F221BEC8](https://download.info.apple.com/Apple_Hardware_Test/022-4149-A.dmg)
* [Mac Pro 5,1 ...................... Mac-F221BEC8](https://download.info.apple.com/Apple_Hardware_Test/022-4831-A.dmg)

### MacBook

* [MacBook 2,1 ...................... Mac-F4208CA9](https://download.info.apple.com/Apple_Hardware_Test/018-2590-A.dmg)
* [MacBook 2,1 ...................... Mac-F4208CAA](https://download.info.apple.com/Apple_Hardware_Test/018-2766-A.dmg)
* [MacBook 3,1 ...................... Mac-F22788C8](https://download.info.apple.com/Apple_Hardware_Test/018-3085-A.dmg)
* [MacBook 4,1 ...................... Mac-F22788A9](https://download.info.apple.com/Apple_Hardware_Test/022-3862-A.dmg)
* [MacBook 5,1 ...................... Mac-F42D89A9](https://download.info.apple.com/Apple_Hardware_Test/022-4216-A.dmg)
* [MacBook 5,1 ...................... Mac-F42D89C8](https://download.info.apple.com/Apple_Hardware_Test/022-4037-A.dmg)
* [MacBook 5,2 ...................... Mac-F22788AA](https://download.info.apple.com/Apple_Hardware_Test/022-4299-A.dmg)
* [MacBook 6,1 ...................... Mac-F22C8AC8](https://download.info.apple.com/Apple_Hardware_Test/022-4453-A.dmg)
* [MacBook 7,1 ...................... Mac-F22C89C8](https://download.info.apple.com/Apple_Hardware_Test/022-4705-A.dmg)

### MacBook Pro

* [MacBook Pro 1,1 ......................... 3A106](https://download.info.apple.com/Apple_Hardware_Test/018-2398-A.dmg)
* [MacBook Pro 1,1 ......................... 3A107](https://download.info.apple.com/Apple_Hardware_Test/018-2405-A.dmg)
* [MacBook Pro 2,1 .................. Mac-F42189C8](https://download.info.apple.com/Apple_Hardware_Test/018-2592-A.dmg)
* [MacBook Pro 2,2 .................. Mac-F42187C8](https://download.info.apple.com/Apple_Hardware_Test/018-2591-A.dmg)
* [MacBook Pro 3,1 .................. Mac-F42388C8](https://download.info.apple.com/Apple_Hardware_Test/018-2833-A.dmg)
* [MacBook Pro 3,1 .................. Mac-F4238BC8](https://download.info.apple.com/Apple_Hardware_Test/018-2770-A.dmg)
* [MacBook Pro 4,1 .................. Mac-F42C86C8](https://download.info.apple.com/Apple_Hardware_Test/022-3832-A.dmg)
* [MacBook Pro 4,1 .................. Mac-F42C89C8](https://download.info.apple.com/Apple_Hardware_Test/022-3833-A.dmg)
* [MacBook Pro 5,1 .................. Mac-F42D86A9](https://download.info.apple.com/Apple_Hardware_Test/022-4266-A.dmg)
* [MacBook Pro 5,1 .................. Mac-F42D86C8](https://download.info.apple.com/Apple_Hardware_Test/022-4048-A.dmg)
* [MacBook Pro 5,2 .................. Mac-F2268EC8](https://download.info.apple.com/Apple_Hardware_Test/022-4217-A.dmg)
* [MacBook Pro 5,3 .................. Mac-F22587C8](https://download.info.apple.com/Apple_Hardware_Test/022-4343-A.dmg)
* [MacBook Pro 5,4 .................. Mac-F22587A1](https://download.info.apple.com/Apple_Hardware_Test/022-4344-A.dmg)
* [MacBook Pro 5,5 .................. Mac-F2268AC8](https://download.info.apple.com/Apple_Hardware_Test/022-4339-A.dmg)
* [MacBook Pro 6,1 .................. Mac-F22589C8](https://download.info.apple.com/Apple_Hardware_Test/022-4596-A.dmg)
* [MacBook Pro 6,2 .................. Mac-F22586C8](https://download.info.apple.com/Apple_Hardware_Test/022-4597-A.dmg)
* [MacBook Pro 7,1 .................. Mac-F222BEC8](https://download.info.apple.com/Apple_Hardware_Test/022-4653-A.dmg)
* [MacBook Pro 8,1 .......... Mac-94245B3640C91C81](https://download.info.apple.com/Apple_Hardware_Test/022-5052-A.dmg)
* [MacBook Pro 8,2 .......... Mac-94245A3940C91C80](https://download.info.apple.com/Apple_Hardware_Test/022-5053-A.dmg)
* [MacBook Pro 8,3 .......... Mac-942459F5819B171B](https://download.info.apple.com/Apple_Hardware_Test/022-5054-A.dmg)
* [MacBook Pro 9,1 .......... Mac-4B7AC7E43945597E](https://download.info.apple.com/Apple_Hardware_Test/022-5879-A.dmg)
* [MacBook Pro 9,2 .......... Mac-6F01561E16C75D06](https://download.info.apple.com/Apple_Hardware_Test/022-5879-A.dmg)
* [MacBook Pro 10,1 ......... Mac-C3EC7CD22292981F](https://download.info.apple.com/Apple_Hardware_Test/022-5882-A.dmg)

### MacBook Air

* [MacBook Air 1,1 .................. Mac-F42C8CC8](https://download.info.apple.com/Apple_Hardware_Test/018-3259-A.dmg)
* [MacBook Air 2,1 .................. Mac-F42D88C8](https://download.info.apple.com/Apple_Hardware_Test/022-4114-A.dmg)
* [MacBook Air 3,1 .......... Mac-942452F5819B1C1B](https://download.info.apple.com/Apple_Hardware_Test/022-4704-A.dmg)
* [MacBook Air 3,2 .......... Mac-942C5DF58193131B](https://download.info.apple.com/Apple_Hardware_Test/022-4267-A.dmg)
* [MacBook Air 4,1 .......... Mac-C08A6BB70A942AC2](https://download.info.apple.com/Apple_Hardware_Test/022-5205-A.dmg)
* [MacBook Air 4,2 .......... Mac-742912EFDBEE19B3](https://download.info.apple.com/Apple_Hardware_Test/022-5205-A.dmg)
* [MacBook Air 5,1 .......... Mac-66F35F19FE2A0D05](https://download.info.apple.com/Apple_Hardware_Test/022-5745-A.dmg)
* [MacBook Air 5,2 .......... Mac-2E6FAB96566FE58C](https://download.info.apple.com/Apple_Hardware_Test/022-5745-A.dmg)

### Xserve

* [Xserve 1,1 ....................... Mac-F4208AC8](https://download.info.apple.com/Apple_Hardware_Test/018-3282-A.dmg)
* [Xserve 2,1 ....................... Mac-F42289C8](https://download.info.apple.com/Apple_Hardware_Test/018-3282-A.dmg)

### Misc

* [unidentified](https://download.info.apple.com/Apple_Hardware_Test/018-2393-A.dmg), possibly [MacBook 1,1 ..... Mac-F4208CC8](https://github.com/upekkha/AppleHardwareTest/issues/31)
* [unidentified](https://download.info.apple.com/Apple_Hardware_Test/018-2418-A.dmg)
* [Bundle](https://download.info.apple.com/Apple_Hardware_Test/018-3169-A.dmg)
  - MacBook 3,1 ..................... Mac-F22788C8
  - MacBook Pro 3,1 ................. Mac-F42388C8
  - MacBook Pro 3,1 ................. Mac-F4238BC8
  - Mac Mini 2,1 .................... Mac-F4208EAA
  - Mac Pro 1,1 ..................... Mac-F4208DC8
  - Mac Pro 2,1 ..................... Mac-F4208DA9
  - iMac 5,2 ........................ Mac-F4218EC8
  - iMac 7,1 ........................ Mac-F42386C8
  - iMac 7,1 ........................ Mac-F4238CC8
* [Bundle](https://download.info.apple.com/Apple_Hardware_Test/018-3254-A.dmg)
  - MacBook 3,1 ..................... Mac-F22788C8
  - MacBook Pro 3,1 ................. Mac-F42388C8
  - MacBook Pro 3,1 ................. Mac-F4238BC8
  - Mac Mini 2,1 .................... Mac-F4208EAA
  - Mac Pro 1,1 ..................... Mac-F4208DC8
  - Mac Pro 2,1 ..................... Mac-F4208DA9
  - iMac 5,2 ........................ Mac-F4218EC8
  - iMac 7,1 ........................ Mac-F42386C8
  - iMac 7,1 ........................ Mac-F4238CC8
* [Bundle](https://download.info.apple.com/Apple_Hardware_Test/022-5348-A.dmg)
  - MacBook 6,1 ..................... Mac-F22C8AC8
  - MacBook 7,1 ..................... Mac-F22C89C8
  - MacBook Pro 8,1 ......... Mac-94245B3640C91C81
  - MacBook Pro 8,2 ......... Mac-94245A3940C91C80
  - MacBook Pro 8,3 ......... Mac-942459F5819B171B
  - Mac Pro 4,1 ..................... Mac-F221BEC8
  - Mac Pro 5,1 ..................... Mac-F221BEC8
  - iMac 12,1 ............... Mac-942B5BF58194151B
  - iMac 12,2 ............... Mac-942B59F58194171B
* [Bundle](https://download.info.apple.com/Apple_Hardware_Test/022-6031-A.dmg)
  - MacBook Air 5,1 ......... Mac-66F35F19FE2A0D05
  - MacBook Air 5,2 ......... Mac-2E6FAB96566FE58C
  - MacBook Pro 9,1 ......... Mac-4B7AC7E43945597E
  - MacBook Pro 9,2 ......... Mac-6F01561E16C75D06
  - MacBook Pro 9,2 ......... Mac-7DF2A3B5E5D671ED
  - MacBook Pro 10,1 ........ Mac-C3EC7CD22292981F
  - MacBook Pro 10,2 ........ Mac-AFD8A9D944EA4843
  - Mac Mini 6,1 ............ Mac-031AEE4D24BFF0B1
  - Mac Mini 6,2 ............ Mac-F65AE981FFA204ED
  - iMac 12,1 ............... Mac-942B5BF58194151B
  - iMac 13,1 ............... Mac-00BE6ED71E35EB86
  - iMac 13,2 ............... Mac-FC02E91DDD3FA6A4

### Hosted on third-party servers

This contains a `.pkg` that tries to install the AHT to your system folder. Alternatively, right-click it to show the package contents and unpack the `Archive.pax.gz` file inside. The extracted `Archive/System/` folder contains the diagnostic tools and can be used to create a bootable USB stick, as with the other `.dmg` files downloaded from Apple.

* [Bundle](http://arhiva.macforum.ro/files/AHT-iMac10,1.zip)
  - MacBook 5,1 ..................... Mac-F42D89A9
  - MacBook 5,1 ..................... Mac-F42D89C8
  - MacBook 5,2 ..................... Mac-F22788AA
  - MacBook 6,1 ..................... Mac-F22C8AC8
  - MacBook Air 2,1 ................. Mac-F42D88C8
  - MacBook Pro 5,1 ................. Mac-F42D86A9
  - MacBook Pro 5,1 ................. Mac-F42D86C8
  - MacBook Pro 5,2 ................. Mac-F2268EC8
  - MacBook Pro 5,3 ................. Mac-F22587C8
  - MacBook Pro 5,4 ................. Mac-F22587A1
  - MacBook Pro 5,5 ................. Mac-F2268AC8
  - Mac Mini 3,1 .................... Mac-F22C86C8
  - iMac 9,1 ........................ Mac-F2218EC8
  - iMac 9,1 ........................ Mac-F2218FC8
  - iMac 10,1 ....................... Mac-F2268CC8
  - iMac 10,1 ....................... Mac-F2268DC8
  - iMac 11,1 ....................... Mac-F2268DAE

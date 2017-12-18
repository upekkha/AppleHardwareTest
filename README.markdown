
  Apple Hardware Test (AHT)
=============================

 Description
-------------

Apple computers ship with a pre-installed suite of hardware diagnostic tools, known as Apple Hardware Test (AHT). In principle you can start them by holding the `d` key while booting. Newer models support holding `option d` to load AHT over the internet. Refer to the official Apple documentation for details: Using AHT on [Intel-based Macs](http://support.apple.com/kb/ht1509), [Mountain Lion](http://support.apple.com/kb/PH11342), [Mavericks](http://support.apple.com/kb/PH14291) and [Yosemite](http://support.apple.com/kb/PH18765). Apple redesigned the AHT, now called [Apple Diagnostics](http://support.apple.com/kb/HT5781), for Macs introduced after June 2013. Consult the [reference codes](http://support.apple.com/en-us/HT203747) to interpret the results.

If however, you reinstalled an older computer from scratch, the diagnostic tools might no longer be available. Unless you have the original disks that came with your computer, there seems to be no way to restore the AHT.

It happens that Apple provides disk images with AHT for most computers, but does not make the links publicly available. Various blogs and forums, mostly [Riven by Five](http://rivenbyfive.blogspot.ch/2012/01/download-and-run-apple-hardware-test.html) and [MacForum.ro](http://arhiva.macforum.ro/comunitate/topic/1194-apple-hardware-test/) have gathered a list of download links. The rest were obtained by scraping `http://download.info.apple.com/Apple_Hardware_Test/` for all the links of the form `0(18|22)-\d{4}-A.dmg`.

Even though there's no guarantee that this list is correct or complete, some links can come in very handy to whoever is trying to debug hardware problems.

You can use the following terminal commands to determine the model and board ID of your computer:

```sh
sysctl hw.model | awk '{ print $2 }'
ioreg -l | awk -F\" '/board-id/ { print $4 }'
```

Download the AHT for your computer model and use the contents to restore the `/System/Library/CoreServices/.diagnostics` folder, then reboot while holding `d` to start the diagnostic tools. Alternatively you may try with a bootable USB stick, as described below. This is also the preferred way on OS X 10.11 or later, where the System Integrity Protection (SIP) no longer allows writing to system folders.

When trying to open an old dmg you may get the error 'legacy image should be converted'. To convert it to a newer format, open Disk Utility, in the menu _Images_ click on _Convert_ and select the dmg to convert and save it under a new name.

Note that there is no one-to-one correspondence between hardware model and AHT. For some models no hardware test could be found, while others seem to have multiple AHT. As the differences are not clear, feel free to try them out, to see which one works best for your hardware.

 Run AHT from bootable USB stick
---------------------------------

  * You need a bootable USB stick, for instance using Disk Utility's _Erase_ with `Format: OS X Extended` and `Scheme: GUID Partition Map`.
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

* [PowerMac v1.2.6, PowerMac G4](http://download.info.apple.com/Apple_Hardware_Test/693-3994-A.dmg)
* [PowerMac v2.2.5GMc2](http://download.info.apple.com/Apple_Hardware_Test/018-1594-A.dmg)
* [PowerMac v2.5GMc1](http://download.info.apple.com/Apple_Hardware_Test/018-1880-A.dmg)
* [PowerMac v2.5.2GMc1](http://download.info.apple.com/Apple_Hardware_Test/018-2216-A.dmg)

### PowerBook

* [PowerBook v1.2.3, PowerBook FireWire, PowerBook G4](http://download.info.apple.com/Apple_Hardware_Test/693-4420-A.dmg)
* [PowerBook v2.5.2GMc1](http://download.info.apple.com/Apple_Hardware_Test/018-2120-A.dmg)

### iBook

* [iBook v2.2.1GMc1](http://download.info.apple.com/Apple_Hardware_Test/018-1680-A.dmg)
* [iBook v2.5GMc1](http://download.info.apple.com/Apple_Hardware_Test/018-2056-A.dmg)

### iMac

* [iMac v2.5.1GMc1](http://download.info.apple.com/Apple_Hardware_Test/018-1879-A.dmg)
* [iMac v2.5.2GMc5](http://download.info.apple.com/Apple_Hardware_Test/018-2158-A.dmg)
* [iMac v2.5.3GMc1](http://download.info.apple.com/Apple_Hardware_Test/018-2215-A.dmg)
* [iMac4,1 3A103](http://download.info.apple.com/Apple_Hardware_Test/018-2392-A.dmg)
* [iMac5,1       Mac-F4228EC8](http://download.info.apple.com/Apple_Hardware_Test/018-2534-A.dmg)
* [iMac5,1       Mac-F42786A9](http://download.info.apple.com/Apple_Hardware_Test/018-2533-A.dmg)
* [iMac5,2       Mac-F4218EC8](http://download.info.apple.com/Apple_Hardware_Test/018-2535-A.dmg)
* [iMac6,1       Mac-F4218FC8](http://download.info.apple.com/Apple_Hardware_Test/018-2579-A.dmg)
* [iMac7,1       Mac-F42386C8](http://download.info.apple.com/Apple_Hardware_Test/018-2845-A.dmg)
* [iMac8,1       Mac-F226BEC8](http://download.info.apple.com/Apple_Hardware_Test/022-3936-A.dmg)
* [iMac8,1       Mac-F227BEC8](http://download.info.apple.com/Apple_Hardware_Test/022-3937-A.dmg)
* [iMac9,1       Mac-F2218EA9](http://download.info.apple.com/Apple_Hardware_Test/022-4297-A.dmg)
* [iMac9,1       Mac-F2218EC8](http://download.info.apple.com/Apple_Hardware_Test/022-4293-A.dmg)
* [iMac9,1       Mac-F2218FC8](http://download.info.apple.com/Apple_Hardware_Test/022-4294-A.dmg)
* [iMac10,1      Mac-F2268CC8](http://download.info.apple.com/Apple_Hardware_Test/022-4451-A.dmg)
* [iMac10,1      Mac-F2268CC8](http://download.info.apple.com/Apple_Hardware_Test/022-4647-A.dmg)
* [iMac10,1      Mac-F2268DC8](http://download.info.apple.com/Apple_Hardware_Test/022-4452-A.dmg)
* [iMac10,1      Mac-F2268DC8](http://download.info.apple.com/Apple_Hardware_Test/022-4644-A.dmg)
* [iMac11,2      Mac-F2238AC8](http://download.info.apple.com/Apple_Hardware_Test/022-4703-A.dmg)
* [iMac11,3      Mac-F2238BAE](http://download.info.apple.com/Apple_Hardware_Test/022-4776-A.dmg)
* [iMac12,1      Mac-942B5BF58194151B](http://download.info.apple.com/Apple_Hardware_Test/022-5090-A.dmg)
* [iMac12,1      Mac-942B5BF58194151B](http://download.info.apple.com/Apple_Hardware_Test/022-5344-A.dmg)
* [iMac12,2      Mac-942B59F58194171B](http://download.info.apple.com/Apple_Hardware_Test/022-5091-A.dmg)

### MacMini

* [MacMini v1.1GMc2](http://download.info.apple.com/Apple_Hardware_Test/018-2079-A.dmg)
* [MacMini1,1 3A102](http://download.info.apple.com/Apple_Hardware_Test/018-2342-A.dmg)
* [MacMini2,1    Mac-F4208EAA](http://download.info.apple.com/Apple_Hardware_Test/018-2886-A.dmg)
* [MacMini3,1    Mac-F22C86C8](http://download.info.apple.com/Apple_Hardware_Test/022-4292-A.dmg)
* [MacMini4,1    Mac-F2208EC8](http://download.info.apple.com/Apple_Hardware_Test/022-4739-A.dmg)
* [MacMini4,1    Mac-F2208EC8](http://download.info.apple.com/Apple_Hardware_Test/022-4706-A.dmg)
* [MacMini5,1    Mac-8ED6AF5B48C039E1](http://download.info.apple.com/Apple_Hardware_Test/022-5207-A.dmg)
* [MacMini5,2    Mac-4BC72D62AD45599E](http://download.info.apple.com/Apple_Hardware_Test/022-5207-A.dmg)

### MacPro

* [MacPro1,1     Mac-F4208DC8](http://download.info.apple.com/Apple_Hardware_Test/018-2769-A.dmg)
* [MacPro2,1     Mac-F4208DA9](http://download.info.apple.com/Apple_Hardware_Test/018-2667-A.dmg)
* [MacPro3,1     Mac-F42C88C8](http://download.info.apple.com/Apple_Hardware_Test/018-3273-A.dmg)
* [MacPro3,1     Mac-F42C88C8](http://download.info.apple.com/Apple_Hardware_Test/022-3843-A.dmg)
* [MacPro3,1     Mac-F42C88C8](http://download.info.apple.com/Apple_Hardware_Test/022-4020-A.dmg)
* [MacPro4,1     Mac-F221BEC8](http://download.info.apple.com/Apple_Hardware_Test/022-4149-A.dmg)
* [MacPro5,1     Mac-F221BEC8](http://download.info.apple.com/Apple_Hardware_Test/022-4831-A.dmg)

### MacBook

* [MacBook2,1    Mac-F4208CA9](http://download.info.apple.com/Apple_Hardware_Test/018-2590-A.dmg)
* [MacBook2,1    Mac-F4208CAA](http://download.info.apple.com/Apple_Hardware_Test/018-2766-A.dmg)
* [MacBook3,1    Mac-F22788C8](http://download.info.apple.com/Apple_Hardware_Test/018-3085-A.dmg)
* [MacBook4,1    Mac-F22788A9](http://download.info.apple.com/Apple_Hardware_Test/022-3862-A.dmg)
* [MacBook5,1    Mac-F42D89A9](http://download.info.apple.com/Apple_Hardware_Test/022-4216-A.dmg)
* [MacBook5,1    Mac-F42D89C8](http://download.info.apple.com/Apple_Hardware_Test/022-4037-A.dmg)
* [MacBook5,2    Mac-F22788AA](http://download.info.apple.com/Apple_Hardware_Test/022-4299-A.dmg)
* [MacBook6,1    Mac-F22C8AC8](http://download.info.apple.com/Apple_Hardware_Test/022-4453-A.dmg)
* [MacBook7,1    Mac-F22C89C8](http://download.info.apple.com/Apple_Hardware_Test/022-4705-A.dmg)

### MacBookPro

* [MacBookPro1,1 3A106](http://download.info.apple.com/Apple_Hardware_Test/018-2398-A.dmg)
* [MacBookPro1,1 3A107](http://download.info.apple.com/Apple_Hardware_Test/018-2405-A.dmg)
* [MacBookPro2,1 Mac-F42189C8](http://download.info.apple.com/Apple_Hardware_Test/018-2592-A.dmg)
* [MacBookPro2,2 Mac-F42187C8](http://download.info.apple.com/Apple_Hardware_Test/018-2591-A.dmg)
* [MacBookPro3,1 Mac-F42388C8](http://download.info.apple.com/Apple_Hardware_Test/018-2833-A.dmg)
* [MacBookPro3,1 Mac-F4238BC8](http://download.info.apple.com/Apple_Hardware_Test/018-2770-A.dmg)
* [MacBookPro4,1 Mac-F42C86C8](http://download.info.apple.com/Apple_Hardware_Test/022-3832-A.dmg)
* [MacBookPro4,1 Mac-F42C89C8](http://download.info.apple.com/Apple_Hardware_Test/022-3833-A.dmg)
* [MacBookPro5,1 Mac-F42D86A9](http://download.info.apple.com/Apple_Hardware_Test/022-4266-A.dmg)
* [MacBookPro5,1 Mac-F42D86C8](http://download.info.apple.com/Apple_Hardware_Test/022-4048-A.dmg)
* [MacBookPro5,2 Mac-F2268EC8](http://download.info.apple.com/Apple_Hardware_Test/022-4217-A.dmg)
* [MacBookPro5,3 Mac-F22587C8](http://download.info.apple.com/Apple_Hardware_Test/022-4343-A.dmg)
* [MacBookPro5,4 Mac-F22587A1](http://download.info.apple.com/Apple_Hardware_Test/022-4344-A.dmg)
* [MacBookPro5,5 Mac-F2268AC8](http://download.info.apple.com/Apple_Hardware_Test/022-4339-A.dmg)
* [MacBookPro6,1 Mac-F22589C8](http://download.info.apple.com/Apple_Hardware_Test/022-4596-A.dmg)
* [MacBookPro6,2 Mac-F22586C8](http://download.info.apple.com/Apple_Hardware_Test/022-4597-A.dmg)
* [MacBookPro7,1 Mac-F222BEC8](http://download.info.apple.com/Apple_Hardware_Test/022-4653-A.dmg)
* [MacBookPro8,1 Mac-94245B3640C91C81](http://download.info.apple.com/Apple_Hardware_Test/022-5052-A.dmg)
* [MacBookPro8,2 Mac-94245A3940C91C80](http://download.info.apple.com/Apple_Hardware_Test/022-5053-A.dmg)
* [MacBookPro8,3 Mac-942459F5819B171B](http://download.info.apple.com/Apple_Hardware_Test/022-5054-A.dmg)
* [MacBookPro9,1 Mac-4B7AC7E43945597E](http://download.info.apple.com/Apple_Hardware_Test/022-5879-A.dmg)
* [MacBookPro9,2 Mac-6F01561E16C75D06](http://download.info.apple.com/Apple_Hardware_Test/022-5879-A.dmg)
* [MacBookPro10,1 Mac-C3EC7CD22292981F](http://download.info.apple.com/Apple_Hardware_Test/022-5882-A.dmg)

### MacBookAir

* [MacBookAir1,1 Mac-F42C8CC8](http://download.info.apple.com/Apple_Hardware_Test/018-3259-A.dmg)
* [MacBookAir2,1 Mac-F42D88C8](http://download.info.apple.com/Apple_Hardware_Test/022-4114-A.dmg)
* [MacBookAir3,1 Mac-942452F5819B1C1B](http://download.info.apple.com/Apple_Hardware_Test/022-4704-A.dmg)
* [MacBookAir3,2 Mac-942C5DF58193131B](http://download.info.apple.com/Apple_Hardware_Test/022-4267-A.dmg)
* [MacBookAir4,1 Mac-C08A6BB70A942AC2](http://download.info.apple.com/Apple_Hardware_Test/022-5205-A.dmg)
* [MacBookAir4,2 Mac-742912EFDBEE19B3](http://download.info.apple.com/Apple_Hardware_Test/022-5205-A.dmg)
* [MacBookAir5,1 Mac-66F35F19FE2A0D05](http://download.info.apple.com/Apple_Hardware_Test/022-5745-A.dmg)
* [MacBookAir5,2 Mac-2E6FAB96566FE58C](http://download.info.apple.com/Apple_Hardware_Test/022-5745-A.dmg)

### Xserve

* [Xserve1,1     Mac-F4208AC8](http://download.info.apple.com/Apple_Hardware_Test/018-3282-A.dmg)
* [Xserve2,1     Mac-F42289C8](http://download.info.apple.com/Apple_Hardware_Test/018-3282-A.dmg)

### Misc

* [unidentified](http://download.info.apple.com/Apple_Hardware_Test/018-2393-A.dmg), possibly [MacBook1,1 Mac-F4208CC8](https://github.com/upekkha/AppleHardwareTest/issues/31)
* [unidentified](http://download.info.apple.com/Apple_Hardware_Test/018-2418-A.dmg)
* [Bundle](http://download.info.apple.com/Apple_Hardware_Test/018-3169-A.dmg)
  - MacBook3,1     Mac-F22788C8
  - MacBookPro3,1  Mac-F42388C8
  - MacBookPro3,1  Mac-F4238BC8
  - MacMini2,1     Mac-F4208EAA
  - MacPro1,1      Mac-F4208DC8
  - MacPro2,1      Mac-F4208DA9
  - iMac5,2        Mac-F4218EC8
  - iMac7,1        Mac-F42386C8
  - iMac7,1        Mac-F4238CC8
* [Bundle](http://download.info.apple.com/Apple_Hardware_Test/018-3254-A.dmg)
  - MacBook3,1     Mac-F22788C8
  - MacBookPro3,1  Mac-F42388C8
  - MacBookPro3,1  Mac-F4238BC8
  - MacMini2,1     Mac-F4208EAA
  - MacPro1,1      Mac-F4208DC8
  - MacPro2,1      Mac-F4208DA9
  - iMac5,2        Mac-F4218EC8
  - iMac7,1        Mac-F42386C8
  - iMac7,1        Mac-F4238CC8
* [Bundle](http://download.info.apple.com/Apple_Hardware_Test/022-5348-A.dmg)
  - MacBook6,1     Mac-F22C8AC8
  - MacBook7,1     Mac-F22C89C8
  - MacBookPro8,1  Mac-94245B3640C91C81
  - MacBookPro8,2  Mac-94245A3940C91C80
  - MacBookPro8,3  Mac-942459F5819B171B
  - MacPro4,1      Mac-F221BEC8
  - MacPro5,1      Mac-F221BEC8
  - iMac12,1       Mac-942B5BF58194151B
  - iMac12,2       Mac-942B59F58194171B
* [Bundle](http://download.info.apple.com/Apple_Hardware_Test/022-6031-A.dmg)
  - MacBookAir5,1  Mac-66F35F19FE2A0D05
  - MacBookAir5,2  Mac-2E6FAB96566FE58C
  - MacBookPro9,1  Mac-4B7AC7E43945597E
  - MacBookPro9,2  Mac-6F01561E16C75D06
  - MacBookPro9,2  Mac-7DF2A3B5E5D671ED
  - MacBookPro10,1 Mac-C3EC7CD22292981F
  - MacBookPro10,2 Mac-AFD8A9D944EA4843
  - MacMini6,1     Mac-031AEE4D24BFF0B1
  - MacMini6,2     Mac-F65AE981FFA204ED
  - iMac12,1       Mac-942B5BF58194151B
  - iMac13,1       Mac-00BE6ED71E35EB86
  - iMac13,2       Mac-FC02E91DDD3FA6A4

### Hosted on third-party servers

This contains a `.pkg` that tries to install the AHT to your system folder. Alternatively right-click it to show the package contents and unpack the `Archive.pax.gz` file inside. The extracted `Archive/System/` folder contains the diagnostic tools and can be used to create a bootable USB stick, as with the other `.dmg` files downloaded from Apple.

* [Bundle](http://arhiva.macforum.ro/files/AHT-iMac10,1.zip)
  - MacBook5,1     Mac-F42D89A9
  - MacBook5,1     Mac-F42D89C8
  - MacBook5,2     Mac-F22788AA
  - MacBook6,1     Mac-F22C8AC8
  - MacBookAir2,1  Mac-F42D88C8
  - MacBookPro5,1  Mac-F42D86A9
  - MacBookPro5,1  Mac-F42D86C8
  - MacBookPro5,2  Mac-F2268EC8
  - MacBookPro5,3  Mac-F22587C8
  - MacBookPro5,4  Mac-F22587A1
  - MacBookPro5,5  Mac-F2268AC8
  - MacMini3,1     Mac-F22C86C8
  - iMac9,1        Mac-F2218EC8
  - iMac9,1        Mac-F2218FC8
  - iMac10,1       Mac-F2268CC8
  - iMac10,1       Mac-F2268DC8
  - iMac11,1       Mac-F2268DAE

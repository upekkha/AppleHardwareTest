
  Apple Hardware Test (AHT)
=============================

 Description
-------------

Apple computers ship with a preinstalled suite of hardware diagnostic tools, known as Apple Hardware Test (AHT). In principle you can start them by holding the ``d`` key while booting. Newer models support holding ``option d`` to load AHT over the internet. Refer to the official Apple documentation for details: [Using AHT on Intel-based Macs](http://support.apple.com/kb/ht1509), [Using AHT on Mountain Lion](http://support.apple.com/kb/PH11342).

If however, you reinstalled an older computer from scratch, the diagnostic tools might no longer be available. Unless you have the original disks that came with your computer, there seems to be no way to restore the AHT, as the [official AHT](http://www.info.apple.com/support/aht.html) page only contains information about ancient computer models.

It happens that Apple provides disk images with AHT for most computers, but does not make the links publically available. Various blogs and forums, mostly [Riven by Five](http://rivenbyfive.blogspot.ch/2012/01/download-and-run-apple-hardware-test.html) and [MacForum.ro](http://macforum.ro/topic/1194-apple-hardware-test) have gathered a list of these download links, that can come in very handy to whoever is trying to debug hardware problems.

Download the AHT for your computer model and use the contents to restore the ``/System/Library/CoreServices/.diagnostics`` folder, then reboot while holding ``d`` to start the diagnostic tools.


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
* [iMac5,1       Mac-F42786A9](http://download.info.apple.com/Apple_Hardware_Test/018-2533-A.dmg)
* [iMac5,1       Mac-F4228EC8](http://download.info.apple.com/Apple_Hardware_Test/018-2534-A.dmg)
* [iMac5,2       Mac-F4218EC8](http://download.info.apple.com/Apple_Hardware_Test/018-2535-A.dmg)
* [iMac6,1       Mac-F4218FC8](http://download.info.apple.com/Apple_Hardware_Test/018-2579-A.dmg)
* [iMac7,1       Mac-F42386C8](http://download.info.apple.com/Apple_Hardware_Test/018-2845-A.dmg)

### MacMini

* [MacMini v1.1GMc2](http://download.info.apple.com/Apple_Hardware_Test/018-2079-A.dmg)
* [MacMini1,1 3A102](http://download.info.apple.com/Apple_Hardware_Test/018-2342-A.dmg)
* [MacMini2,1    Mac-F4208EAA](http://download.info.apple.com/Apple_Hardware_Test/018-2886-A.dmg)

### MacPro

* [MacPro2,1     Mac-F4208DA9](http://download.info.apple.com/Apple_Hardware_Test/018-2667-A.dmg)
* [MacPro1,1     Mac-F4208DC8](http://download.info.apple.com/Apple_Hardware_Test/018-2769-A.dmg)
* [MacPro3,1     Mac-F42C88C8](http://download.info.apple.com/Apple_Hardware_Test/018-3273-A.dmg)

### MacBook

* [MacBook2,1    Mac-F4208CA9](http://download.info.apple.com/Apple_Hardware_Test/018-2590-A.dmg)
* [MacBook2,1    Mac-F4208CAA](http://download.info.apple.com/Apple_Hardware_Test/018-2766-A.dmg)
* [MacBook3,1    Mac-F22788C8](http://download.info.apple.com/Apple_Hardware_Test/018-3085-A.dmg)

### MacBookPro

* [MacBookPro1,1 3A106](http://download.info.apple.com/Apple_Hardware_Test/018-2398-A.dmg)
* [MacBookPro1,1 3A107](http://download.info.apple.com/Apple_Hardware_Test/018-2405-A.dmg)
* [MacBookPro2,2 Mac-F42187C8](http://download.info.apple.com/Apple_Hardware_Test/018-2591-A.dmg)
* [MacBookPro2,1 Mac-F42189C8](http://download.info.apple.com/Apple_Hardware_Test/018-2592-A.dmg)
* [MacBookPro3,1 Mac-F4238BC8](http://download.info.apple.com/Apple_Hardware_Test/018-2770-A.dmg)
* [MacBookPro3,1 Mac-F42388C8](http://download.info.apple.com/Apple_Hardware_Test/018-2833-A.dmg)
* [MacBookPro5,1 Mac-F42D86A9](http://download.info.apple.com/Apple_Hardware_Test/022-4266-A.dmg)
* [MacBookPro6,1 Mac-F22589C8](http://download.info.apple.com/Apple_Hardware_Test/022-4596-A.dmg)
* [MacBookPro6,2 Mac-F22586C8](http://download.info.apple.com/Apple_Hardware_Test/022-4597-A.dmg)

### MacBookAir

* [MacBookAir1,1 Mac-F42C8CC8](http://download.info.apple.com/Apple_Hardware_Test/018-3259-A.dmg)
* [MacBookAir3,2 Mac-942C5DF58193131B](http://download.info.apple.com/Apple_Hardware_Test/022-4267-A.dmg)

### Xserve

* [Xserve1,1     Mac-F4208AC8](http://download.info.apple.com/Apple_Hardware_Test/018-3282-A.dmg)
* [Xserve2,1     Mac-F42289C8](http://download.info.apple.com/Apple_Hardware_Test/018-3282-A.dmg)

### Misc

* [unidentified](http://download.info.apple.com/Apple_Hardware_Test/018-2393-A.dmg)
* [unidentified](http://download.info.apple.com/Apple_Hardware_Test/018-2418-A.dmg)
* [Bundle](http://download.info.apple.com/Apple_Hardware_Test/018-3169-A.dmg)
  - iMac5,2       Mac-F4218EC8
  - iMac7,1       Mac-F4238CC8
  - iMac7,1       Mac-F42386C8
  - Macmini2,1    Mac-F4208EAA
  - MacPro1,1     Mac-F4208DC8
  - MacPro2,1     Mac-F4208DA9
  - MacBookPro3,1 Mac-F4238BC8
  - MacBookPro3,1 Mac-F42388C8
  - MacBook3,1    Mac-F22788C8
* [Bundle](http://download.info.apple.com/Apple_Hardware_Test/018-3254-A.dmg)
  - iMac5,2       Mac-F4218EC8
  - iMac7,1       Mac-F4238CC8
  - iMac7,1       Mac-F42386C8
  - Macmini2,1    Mac-F4208EAA
  - MacPro1,1     Mac-F4208DC8
  - MacPro2,1     Mac-F4208DA9
  - MacBookPro3,1 Mac-F4238BC8
  - MacBookPro3,1 Mac-F42388C8
  - MacBook3,1    Mac-F22788C8



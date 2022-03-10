# Intro-To-Android-Pen-Testing

##### first we need an Android emulator to be set up in our Linux system 
##### i'm gonna use Anbox here [You can try android studio emulator , GennyMotion too if you want]

## Anbox Setup
```bash
$ sudo apt update
$ sudo apt install snapd
$ sudo apt install android-tools-adb
```
##### now we gonna install Anbox using snap
```bash
$ sudo snap install --devmode --beta anbox
```
##### Add it to path, otherwise you get the good old “The command could not be located because ‘/snap/bin’ is not included in the PATH environment variable."
```bash
$ export PATH=$PATH:/snap/bin
```
now you can lauch Anbox with
```
$ anbox.appmgr
```
![](https://raw.githubusercontent.com/Rajchowdhury420/temp-files-for-writeup/main/anbox.png)
```
It should also register under “adb devices” and be usable with adb in general. However, in my experience, Anbox and adb can be rather finicky. Anbox must be running for it to be usable with adb. In case it does not show up, try the following troubleshooting steps: Stop Anbox, restart adb, start Anbox again, open Anbox appmanager, check for adb devices.
```
```bash
$ sudo snap stop anbox
$ adb kill-server && adb start-server
$ sudo snap start anbox
$ anbox.appmgr
```
**If you experience graphical issues, or blacked out screens you might want to try and enable software rendering.
```bash
$ sudo snap set anbox software-rendering.enable=true
```
**To install an app on Anbox you must use adb**
```bash
$ adb install example.apk
```
**and make sure to use "x86 64bit" not "ARM".
**Depending on your app, you might need to allow installation from unknown sources, under "Settings" -> "Security".

![](https://raw.githubusercontent.com/Rajchowdhury420/temp-files-for-writeup/main/settings.png)
##### In case you have trouble with app signing, or have an unsigned app, you can use [Uber APK Signer](https://github.com/patrickfav/uber-apk-signer/releases/download/v1.2.1/uber-apk-signer-1.2.1.jar)

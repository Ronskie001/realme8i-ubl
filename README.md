## THIS GUIDE IS SPECIFIC FOR REALME 8I/NARZO 50 ONLY. ADAPT IT FOR YOUR DEVICE. ##

REQUIREMENTS:
* Working platform-tools installed (adb & fastboot)
* Data backup (your device gets reset after unlock)
* Brains
* OEM unlocking enabled from developer settings
* USB debugging enabled, and device verified (adb devices) from developer settings

Steps:
1. Clone this repository. (git clone https://github.com/rk134/realme8i-ubl)
2. Go to setings > about device > status.
3. Copy your IMEI 1 & serial number.
4. Open a terminal in the cloned folder.
5. run this (keep 0x, replace H* with your serial number, and replace D with IMEI 1.):
```
perl deeptesting-junk.pl pcb 0xHHHHHHHH imei DDDDDDDDDDDDDDD cmd applyLkUnlock
```
6. After it shows `{"resultCode":0,"msg":"SUCCESS"}`, then run this command:
```
perl deeptesting-junk.pl pcb 0xHHHHHHHH imei DDDDDDDDDDDDDDD cmd checkApproveResult
```
7. After it shows {"resultCode":0,"msg":"SUCCESS","data":{"unlockCode":"0345af...lots of hexdigits"}}
   install the apk, and apply for deep test.
8. After waiting for a few minutes, go back and query application status.
9. After approval, click start deep testing IF YOU MEET PREREQUSISITES.
10. It will reboot to fastboot, ignore any errors/warnings. Then run the following command:
```
fastboot flashing unlock
```
11. It will prompt you and show a big scarwy warning of warranty. Ignore it, and select yes and press the power button.
12. You will be greeted with a boot mode screen. DO NOT PRESS ANYTHING.
13. Hold power + vol down, and you will return back to the fastboot screen.
14. Type fastboot reboot recovery.
15. You are now in recovery. Format data, and reboot to system. 
16. Setup device, and then check oem unlocking option in developer settings (should be greyed out)

As usual, me or turistu OR ANY OTHER ENTITY are not responsible for any issues/damages caused to your device.
Please do not bother us for device support, drivers issues etc.
Instead, ask for advice in your device specific telegram groups/chats.

This method is confirmed working on realme 9 (RMX3474), realme 8i (RMX3151), realme narzo 50 (RMX3286) as of 18/05/2023.

This method is not guaranteed to work all the time, and could be easily patched. Good luck!
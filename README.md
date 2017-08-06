# xposed
# APK研究
1. 列出所有设备
```code
~/Library/Android/sdk/platform-tools/adb devices
```
1. 查看log
```code
~/Library/Android/sdk/platform-tools/adb logcat
```
1. 启动apk
```code
~/Library/Android/sdk/platform-tools/adb -s emulator-5554 shell am start -n com.tencent.mobileqq/.activity.LoginActivity
```
1. 发送点击事件
```code
 ~/Library/Android/sdk/platform-tools/adb -s emulator-5554 shell getevent | grep -e "0035" -e "0036"
/dev/input/event1: 0003 0035 00005439
/dev/input/event1: 0003 0036 0000347e
~/Library/Android/sdk/platform-tools/adb -s emulator-5554 shell getevent -p | grep -e "0035" -e "0036"
                0031  0032  0033  0034  0035  0036  0037  0038 
                0035  : value 0, min 0, max 32767, fuzz 0, flat 0, resolution 0
                0036  : value 0, min 0, max 32767, fuzz 0, flat 0, resolution 0
>>> int('0x00005439',16)
21561
>>> int('0x0000347e',16)
13438
>>> 1080*21561/32767.0
710.6503494369335
>>> 1920*13438/32767.0
787.4068422498245
 ~/Library/Android/sdk/platform-tools/adb -s emulator-5554 shell input tap 710 787
```


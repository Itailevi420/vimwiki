
To turn off disk devices write protect, we use the low level system utility
` hdparm ` like this:

```sh
sudo apt-get install hdparm
sudo hdparm -r0 /dev/sdb
```



where we asume that /dev/sdb is the Physical disk device we're working on.
If the device has partitions that are mounted as read-only, you should
re-mount'em as read-write in order to write data to them.

Hope that helps.

*source from:*
https://askubuntu.com/questions/101637/usb-turn-write-protection-off
😊 ✈ 👽 ❤



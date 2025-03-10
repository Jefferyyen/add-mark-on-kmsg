# add-mark-on-kmsg

create a systemd service:

## 1.Create a new service file:
```
sudo nano /etc/systemd/system/kmsg-log.service
```

## 2.Add the following content:
```
[Unit]
Description=Log custom message to dmesg
After=network.target

[Service]
Type=oneshot
ExecStart=/bin/bash -c 'echo "123456" | tee /dev/kmsg'
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
```
Save and exit: Ctrl + X, press Y, then Enter.
## 3.enable, and start the service:
``` 
sudo systemctl enable kmsg-log.service
```

```
sudo systemctl start kmsg-log.service
```
reboot system

## 4. After rebooting, check:
```
sudo dmesg | grep 123456
```
input sudo dmesg > dmesg.txt
>generate and copy this file
```
sudo dmesg > dmesg.txt
```

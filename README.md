# How to connect HC-05 to Beagleplay via UART near USB-C plug
To identify BeaglePlay onboard UARTs, we use the follwoing commands:
```
debian@BeagleBone:~$ ls /dev/ttyS*
```
You should see something like this: 
```
/dev/ttyS0  /dev/ttyS2  /dev/ttyS5  /dev/ttyS7  /dev/ttyS9
/dev/ttyS1  /dev/ttyS3  /dev/ttyS6  /dev/ttyS8
```
In my case, the UART pins are of `/dev/ttyS2`. To check which serial device is the one you are using, short the RX and TX pins. Then, open `screen` serial monitor with the following command:
```
sudo screen /dev/ttyS<one number from your listed devices> 9600
```
Usually, it's either `/dev/ttyS2` or `/dev/ttyS5`. When ou type something on the `screen` shell, it should return what you typed in becuase the Rx and TX are shorted. Otherwise, you are on another serial device.

```markdown
> [!CAUTION]
> When wiring HC-05 to BeaglePlay UART, make sure RX is going to TX and TX is going to RX. Wrong pin configuration will fry the conenctions permanently 
```

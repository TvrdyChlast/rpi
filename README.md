# rpi
all shit for rpi nas

# activate penta sata
Edit 

``` 
/boot/firmware/config.txt
``` 
and add

 ```
 dtparam=pciex1
```
to the end of the file, save and reboot.


# Force Gen 3
Edit 
``` 
/boot/firmware/config.txt
```
and add 
```
dtparam=pciex1_gen=3
```
save and reboot.

# Top hat

```
sudo apt update
```
```
sudo apt install wget
```
```
wget https://github.com/radxa/rockpi-penta/releases/download/v0.2.2/rockpi-penta-0.2.2.deb
```
```
sudo apt install -y ./rockpi-penta-0.2.2.deb
```
# Config Top hat

edit the configuration file 
```
/etc/rockpi-penta.conf
```

```
[fan]
# When the temperature is above lv0 (35'C), the fan at 25% power,
# and lv1 at 50% power, lv2 at 75% power, and lv3 at 100% power.
# When the temperature is below lv0, the fan is turned off.
# You can change these values if necessary.
lv0 = 35
lv1 = 40
lv2 = 45
lv3 = 50

[key]
# You can customize the function of the key, currently available functions are
# slider: oled display next page
# switch: fan turn on/off switch
# reboot, poweroff
# If you have any good suggestions for key functions,
# please add an issue on https://rock.sh/rockpi-sata
click = slider
twice = switch
press = none

[time]
# twice: maximum time between double clicking (seconds)
# press: long press time (seconds)
twice = 0.7
press = 1.8

[slider]
# Whether the oled auto display next page and the time interval (seconds)
auto = true
time = 10

[oled]
# Whether rotate the text of oled 180 degrees, whether use Fahrenheit
rotate = false
f-temp = false
```
After modifying the configuration, run the 
``` 
sudo systemctl restart rockpi-penta.service
```
command to restart the service for the configuration to take effect.


# OMV install script

```
wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/preinstall | sudo bash
```


#
#
#
#

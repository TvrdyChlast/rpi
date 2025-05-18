# rpi
all shit for rpi nas

set up wifi 
edit
```
/etc/wpa_supplicant/wpa_supplicant.conf
```
```
network={
ssid="wifssidnumberone"
Priority=35
psk="secretpassword"
}
network={
ssid="numbertwoSSID"
priority=70
psk="pswdsecret"
}
```

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
```
wget -O - https://github.com/OpenMediaVault-Plugin-Developers/installScript/raw/master/install | sudo bash

```

# ZeroTier

install
```
curl -s https://install.zerotier.com | sudo bash

```
add network

```
zerotier-cli join <network-id>

```
edit photoprism in pod

```
sudo docker exec -ti photoprism-photoprism-1 /bin/bash

```
```
photoprism convert
```

CLI Command	Description
```
photoprism users ls
```
 [search]	Searches existing user accounts
```
photoprism users legacy
```
 [search]	Searches legacy user accounts
```
photoprism users add
```
 [options] [username]	Adds a new user account
```
photoprism users show
```
 [username]	Displays user account information
```
photoprism users mod
```
 [options] [username]	Modifies an existing user account
```
photoprism users rm
```
 [username]	Removes a user account
```
photoprism users reset
```
 --yes	Removes all accounts and resets the database
Command Flag	Description
--name NAME, -n NAME	full NAME for display in the interface
--email EMAIL, -m EMAIL	unique EMAIL address of the user
--password PASSWORD, -p PASSWORD	PASSWORD for local authentication (8-72 characters)
--role value, -r value	user account ROLE (admin, user, viewer or guest) (default: "admin")
--auth PROVIDER, -A PROVIDER	authentication PROVIDER (default, local, oidc or none)
--auth-id ID	authentication ID e.g. Subject ID or Distinguished Name (DN)
--superadmin, -s	make user super admin with full access
--no-login, -l	disable login on the web interface
--webdav, -w	allow to sync files via WebDAV
--upload-path value, -u value	upload files to this sub-folder
--disable-2fa	deactivate two-factor authentication


#
#
#

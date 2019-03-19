

## First steps

1. Install ansible on your laptop.
2. Enable ssh on your pi. You should be able to `ssh pi@raspberrypi.local`.
  1. If setup is headless: mount `boot` partition in laptop and just create empty `ssh` file in `/`.
3. Connect pi to your network
	1. If setup is headless and you're connecting to wifi:
		1. Mount `rootfs` partition on laptop
		2. Enable wifi and specify path to wifi config by editing `/etc/network/interfaces`:
		```
		auto wlan0
		allow-hotplug wlan0
		iface wlan0 inet dhcp
    		wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
		```
		3. Configure network in `wpa_supplicant.conf` (example):
		```
		network={
 			ssid="my_ssid"
 			key_mgmt=WPA-PSK
 			psk=lkjalfkjklj24NKLhj2l4j0B2vkjh2jh2klj4lkjlktjl2k4jtlk2jlk
		}
		```		
		4. The raspberrypi will take about a minute to boot up and connect to the network.

## Run playbook

`ansible-playbook -i inventory hab.yaml`

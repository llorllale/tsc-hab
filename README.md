
## First steps

1. A bootable microSD card with [Raspbian Stretch Lite](https://www.raspberrypi.org/downloads/raspbian/)
   * You can use [Etcher](https://www.balena.io/etcher/) to burn the boot image to the SD card
2. Install ansible on your laptop.
3. Enable ssh on your pi. You should be able to `ssh pi@raspberrypi.local`.
   * If setup is headless: mount `boot` partition in laptop and just create empty `ssh` file in `/`.
4. Connect pi to your network
   * If setup is headless and you're connecting to wifi:
	    <ol>
		  <li>Mount `rootfs` partition on laptop</li>
      <li>Enable wifi and specify path to wifi config by editing `/etc/network/interfaces`:
		  ```
		  auto wlan0
		  allow-hotplug wlan0
		  iface wlan0 inet dhcp
      		wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
	  	```</li>
		  <li>Configure network in `wpa_supplicant.conf` (example):
		  ```
		  network={
 	  		ssid="my_ssid"
   			key_mgmt=WPA-PSK
   			psk=lkjalfkjklj24NKLhj2l4j0B2vkjh2jh2klj4lkjlktjl2k4jtlk2jlk
  		}
  		```</li>
		  <li>The raspberrypi will take about a minute to boot up and connect to the network.</li>
			</ol>

## Run playbook

`ansible-playbook -i inventory hab.yaml`

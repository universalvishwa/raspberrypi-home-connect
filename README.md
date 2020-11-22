# Raspberry pi Home Connect

## Overview
- This repository describes how to setup a Github Action workflow to manage a Raspberry Pi (or other Linux Home server).
- In this scenario we are considering the _Port-forwarding_ feature available in your Home Router.
- The object is to directly interact with Raspberry from Github Actions.
    - There are other more secure methods exist by using 3rd party services.
    - e.g. [remote.it](https://remote.it/)
- The `Home router` needs to be setup with _Port forwarding_ to connect with Home server's SSH port (Default: 22) and private IP address.
    - Source port: Something not port 22
    - Destination port: 22

### Misc: Setting Raspberry Pi Power saving mode OFF
- Link: [Does Your Raspberry Pi 3 Lose WiFi Connections After a While](http://qdosmsq.dunbar-it.co.uk/blog/2016/03/does-your-raspberry-pi-3-lose-wifi-connections-after-a-while/)
- Check Power saving mode status,
```bash
$ sudo iw dev wlan0 get power_save
>>
power_save: on
```
- Disable power saving mode,
```bash
$ sudo iw dev wlan0 set power_save off
```

# Raspberry pi Home Connect

## Overview
- This repository describes how to setup a Github Action workflow to manage a Raspberry Pi (or other Linux Home server).
- In this scenario we are considering the _Port forwarding_ feature available in your Home Router.
- The objective is to directly interact with Raspberry Pi from Github Actions.
    - However more secure and feature rich methods exist by using 3rd party services. e.g. [remote.it](https://remote.it/)
- The `Home router` needs to be setup with _Port forwarding_ to connect with Home server's SSH port (Default: 22) and private IP address.
    - Source port: Something not port 22
    - Destination port: 22
- _**NOTE:**_ The workflow uses SSH keys instead of Passwords to connect to the Raspberry pi.
    - Generate an SSH key pair in the Raspberry Pi and add the _**id_rsa.pub**_ to `~/.ssh/authorized_keys`.
    - Use the _**id_rsa**_ file for `SSH_PRIVATE_KEY` Github secret.

### Github Secrets
- `HOST`: Home router's public NAT IP. i.e. The result of "What's my IP'.
- `USERNAME`: Raspberry pi user
- `PORT`: Forwarding Port (Source port) setup at the Home router.
- `SSH_PRIVATE_KEY`: Private key of authorized SSH key.

### Misc: Setting Raspberry Pi Power saving mode OFF
- Raspberry Pi may lose the WiFi connection after a period of inactivity if the _Power saving mode is turned ON_.
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
- Link: [Does Your Raspberry Pi 3 Lose WiFi Connections After a While](http://qdosmsq.dunbar-it.co.uk/blog/2016/03/does-your-raspberry-pi-3-lose-wifi-connections-after-a-while/)

### References
- GitHub Action: [SSH Remote Commands](https://github.com/marketplace/actions/ssh-remote-commands)
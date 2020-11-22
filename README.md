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
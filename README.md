# home-automation

## Introduction
According to the research and tests documented in repo https://github.com/gabrielfaleiro/lxc-haos-vm, Home Assistant is not a simple tool to virtualize. The most complete installation, to enjoy every functionality, must be performed by the provided operating system.

Other points to move from home assistante:
- Node-RED is the more capable way of implementing complex automations. It is not easily scalable and maintainable for advanced users.
- SONOFF integration is not straigth forward.

Thus, OpenHAB is going to be validated.

## OpenHAB

Results:
- Installation: easy, using snap. Valid for Ubuntu Core.
- Integrations
- Sonoff: 
    - https://community.openhab.org/t/ewelink-sonoff-binding-new-binding-without-flashing/116141
    - https://github.com/delid4ve/openhab-3.x-sonoff
    - Using snap, addons can be integrated in '/var/snap/openhab/1946/addons' directory.
    - Download file with *sudo wget https://github.com/delid4ve/openhab-sonoff-compiled/raw/main/org.openhab.binding.sonoff-3.2.0-SNAPSHOT_2.5R10.jar*
    - Install addons: https://www.openhab.org/docs/configuration/addons.html
    - OR use the "Json 3rd Party Add-on Service" from Settings (NOT EXPLORED)
    - You should now be able to create a thing with label "Sonoff Account Thing"
    - Run discovery to create the cache required for all devices. Add a thing, select SONOFF integration and click on scan. Several scans were necessary in my case.
        - https://www.openhab.org/docs/concepts/discovery.html
- Automations
- Backup: Easy with command *openhab.backup*
    - https://community.openhab.org/t/docs-on-how-to-backup-openhab/100182/2
- Console: using command *openhab.client*
        - Ref: https://www.openhab.org/docs/administration/console.html
- Users: Not handled through UI, only cli
    - https://community.openhab.org/t/is-openhab-3-multiuser/111277/5
- Cache: **TODO**: how to clean cache in snap deployments
    - https://community.openhab.org/t/clear-the-cache/36424
    - sonoff cache: https://community.openhab.org/t/ewelink-sonoff-binding-new-binding-without-flashing/116141/228
    - /var/snap/openhab/1946/userdata/cache
    - /var/snap/openhab/1946/userdata/tmp
    - /var/snap/openhab/1946/userdata/sonoff

## openvpn

There is not a snap build for handling a openvpn client connection.

Snap easy-openvpn seems to be a server openvpn implementation: https://gist.github.com/popey/60f9f3b99c31ba120f0ae7ca140bc73e

OpenVPN client installation: https://openvpn.net/cloud-docs/openvpn-3-client-for-linux/?_ga=2.181589601.777374592.1670254755-1715325116.1670254755

Setup on boot: https://openvpn.net/blog/openvpn-3-linux-and-auth-user-pass/


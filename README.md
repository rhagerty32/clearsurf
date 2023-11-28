<!-- markdownlint-configure-file { "MD004": { "style": "consistent" } } -->
<!-- markdownlint-disable MD033 -->
#

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://pi-hole.github.io/graphics/Vortex/Vortex_Vertical_wordmark_darkmode.png">
    <source media="(prefers-color-scheme: light)" srcset="https://pi-hole.github.io/graphics/Vortex/Vortex_Vertical_wordmark_lightmode.png">
    <img src="https://pi-hole.github.io/graphics/Vortex/Vortex_Vertical_wordmark_lightmode.png" width="168" height="270" alt="Pi-hole website">
  </picture>
    <br>
    <strong>Network-wide ad blocking via your own Linux hardware</strong>
</p>

<!-- markdownlint-enable MD033 -->

# ClearSurf Installation Guide

## Here are the steps to help setup your ClearSurf Pi-Hole. Keep in mind, all these commands are for MacOS and might be different for windows.

1. Install Raspberry PiOS on your device:
    - Install Pi Imager from here: https://www.raspberrypi.com/software/
    - Select applicable device
    - Select the standard OS (the top on I believe)
    - Choose external storage (Micro SD card that will go in the Pi)
    - If it asks, say no to using the keychain for the wifi password
    - Say yes to adjusting settings and change the password to "pihole"
    - Then begin writing (should a few minutes)
2. Insert Micro SD into Pi. Then give it power and connect ethernet
3. Open up terminal on your computer and SSH into the Pi (find IP through pinging "Pihole.local")
4. Enter password "pihole"
5. Create a bash script by running this command: `sudo nano piStartup.sh`
6. Enter this code into the file:\
    `#!/bin/bash`

    `#Get initial network coonnection`\
    `sleep 10`

    `#Clone Clear-Surf Software`\
    `git clone https://github.com/rhagerty32/clearsurf.git`

    `#Navigate to correct Directory`\
    `cd ~/pi-hole/'automated install'/`

    `#Initialize Pi-Hole Installation Script`\
    `bash basic-install.sh &`
    
7. Go into boot file by running this command: `sudo crontab -e`
8. At the bottom enter: `@reboot bash piStartup.sh`

After following this process you now have a device that is ready to be restarted. When that happens, it should auto install and configure Pi-Hole on your network. You can initiate this by running "sudo reboot" or, you can just run the command manually by typing "bash piStartup.sh"

-----

The Pi-hole® is a [DNS sinkhole](https://en.wikipedia.org/wiki/DNS_Sinkhole) that protects your devices from unwanted content without installing any client-side software.

- **Easy-to-install**: our dialogs walk you through the simple installation process in less than ten minutes
- **Resolute**: content is blocked in _non-browser locations_, such as ad-laden mobile apps and smart TVs
- **Responsive**: seamlessly speeds up the feel of everyday browsing by caching DNS queries
- **Lightweight**: runs smoothly with [minimal hardware and software requirements](https://docs.pi-hole.net/main/prerequisites/)
- **Robust**: a command-line interface that is quality assured for interoperability
- **Insightful**: a beautiful responsive Web Interface dashboard to view and control your Pi-hole
- **Versatile**: can optionally function as a [DHCP server](https://discourse.pi-hole.net/t/how-do-i-use-pi-holes-built-in-dhcp-server-and-why-would-i-want-to/3026), ensuring _all_ your devices are protected automatically
- **Scalable**: [capable of handling hundreds of millions of queries](https://pi-hole.net/2017/05/24/how-much-traffic-can-pi-hole-handle/) when installed on server-grade hardware
- **Modern**: blocks ads over both IPv4 and IPv6
- **Free**: open source software that helps ensure _you_ are the sole person in control of your privacy

-----

**Please be sure to check the FAQs** before starting a new discussion, as we do not have the spare time to reply to every request for assistance.

- [Frequently Asked Questions](https://discourse.pi-hole.net/c/faqs)
- [Feature Requests](https://discourse.pi-hole.net/c/feature-requests?order=votes)
- [Reddit](https://www.reddit.com/r/pihole/)
- [Twitter](https://twitter.com/The_Pi_hole)

-----

## Breakdown of Features

### [Faster-than-light Engine](https://github.com/pi-hole/ftl)

[FTLDNS](https://github.com/pi-hole/ftl) is a lightweight, purpose-built daemon used to provide statistics needed for the Web Interface, and its API can be easily integrated into your own projects. As the name implies, FTLDNS does this all _very quickly_!

Some of the statistics you can integrate include:

- Total number of domains being blocked
- Total number of DNS queries today
- Total number of ads blocked today
- Percentage of ads blocked
- Unique domains
- Queries forwarded (to your chosen upstream DNS server)
- Queries cached
- Unique clients

### The Web Interface Dashboard

This [optional dashboard](https://github.com/pi-hole/web) allows you to view stats, change settings, and configure your Pi-hole. It's the power of the Command Line Interface, with none of the learning curve!

Some notable features include:

- Mobile-friendly interface
- Password protection
- Detailed graphs and doughnut charts
- Top lists of domains and clients
- A filterable and sortable query log
- Long Term Statistics to view data over user-defined time ranges
- The ability to easily manage and configure Pi-hole features
- ... and all the main features of the Command Line Interface!

There are several ways to [access the dashboard](https://discourse.pi-hole.net/t/how-do-i-access-pi-holes-dashboard-admin-interface/3168):

1. `http://pi.hole/admin/` (when using Pi-hole as your DNS server)
2. `http://<IP_ADDRESS_OF_YOUR_PI_HOLE>/admin/`

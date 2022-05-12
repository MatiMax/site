---
description: Documentation of various projects using Raspberry Pi single board computers.
---

# Raspberry Pi

## Introduction

The Raspberry Pi Foundation has been doing an outstanding job in brining the joy of micro-computers not only back to children's hands after the British educational computing era, but also in empowering enthusiats with their vast range of very affordable computing-products to build their ideas in both hardware and software.

## Tips for your Raspberry Pis

The following sections might give you some hints on using your Pi effectively and maybe even tackle a specific problem.

### Raspberry Pi Zero

#### Switching HDMI Video On and Off

1. This step would only be necessary if you don't use or even have disabled the default `pi` user on your device.\
   \
   Make sure that your user is in the `video`group. If not, add this group to your user with the following command\
   \
   `sudo adduser <your-user-name> video`\
   \
   replacing \<your-user-name> with the actual name of your login-user you want to be able to execute this command.&#x20;
2. The `vcgencmd` command is used to switch the HDMI signal on and off like so:\
   `vcgencmd display_power 0` to turn the display off, and\
   `vcgencmd display_power 1` to turn the display on respectively.

{% hint style="info" %}
You might want to do some shell scripting in order to come up with a more comfortable way of using those not easy to remember commands. As I'm using the brilliant [Fish shell](https://fishshell.com), I gladly share my user function definition with you.
{% endhint %}

```bash
# Fish shell function to switch HDMI display on and off on your Raspberry Pi Zero
function display
   switch $argv
      case on
         vcgencmd display_power 1 >/dev/null
      case off
         vcgencmd display_power 0 >/dev/null
      case '*'
         echo "Usage: display on|off"
   end
end
```

#### Using the Raspberry Pi Zero as a VPN Server with WireGuard

The most useful application of running a cheap Raspberry Pi Zero as a full-fledged VPN server is overshadowed by the sheer complexity of setting up a VPN service within Raspberry Pi OS using the standard approaches like OpenVPN daemons or an installation of StrongSwan.

In case you just want a bunch of devices to be able to connect securely to your home network in times when you are far, far away, or even only sipping a nice cup of tea over at your neighbours house where WiFi reception of your home's router might be pour and all your are left with is internet on your mobile phone, WireGuard comes to the rescue.

Instead of repeating an incredibly well written documentation on how to install WireGuard _per se_, I'll instead link to the resource of Mikkel Høgh's most excellent blog post:

{% embed url="https://mikkel.hoegh.org/2019/11/01/home-vpn-server-wireguard" %}
Setting up a WirteGuard VPN Server by Mikkel Høgh
{% endembed %}

### Raspberry Pi Zero 2 W

More to come soon.

### Raspberry Pi 400

More to come soon, too.

### Raspberry Pi Pico

More to come soon as well.


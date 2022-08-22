# Mullbot
Mullbot is an interactive bash script for setting up and controlling a Mullvad VPN connection on an OpenWrt router running [Dropbear](https://matt.ucc.asn.au/dropbear/dropbear.html).

Mullbot requires [jq](https://stedolan.github.io/jq/), [OpenSSH](https://www.openssh.com/), and [GNU coreutils](https://www.gnu.org/software/coreutils/), and was developed and tested with [GNU bash](https://www.gnu.org/software/bash/) 5.1.16, and [OpenWrt](https://openwrt.org/) 21.02.3.

## Control your Mullvad connection
Mullbot incorporates a set of functions for controlling a [Wireguard](https://www.wireguard.com/) connection to [Mullvad VPN](https://mullvad.net/), and can quickly create a Wireguard connection according to [Mullvad's instructions](https://mullvad.net/en/help/running-wireguard-router/). It also enables quick switching between servers.

## AutoLuCI
For a bit of added security, you can enable AutoLuCI, which will enable the uHTTPd service on the router when the script starts, and disable it when the script exits, with an optional exit trap. Commands are issued via SSH, so if you set up SSH authentication with a key and disable password authetication, this can serve as a roll-your-own 2FA option for your router's web interface.

For more info about securing your SSH setup with a Yubikey, see [DrDuh's guide](https://github.com/drduh/YubiKey-Guide).

## Screenshots
Simple interface:

![Main menu](https://www.drewbert.co.za/mullbot/mullbot1.jpeg)

Convenient VPN control and status indicators:

![Mullbot menu](https://www.drewbert.co.za/mullbot/mullbot2.jpeg)

Easy server selection:

![Mullbot menu](https://www.drewbert.co.za/mullbot/mullbot3.jpeg)

### Notes
Only tested with OpenWrt 21.02.3 and Bash 5.1.16

When you first run the script, it will download a backup of your router config to your home dir.
Only the network, dhcp, and firewall files in /etc/config/ will be changed.
If your router config gets broken, reset the device and upload the backup config.

All Mullbot's config files will be saved locally in ~/.mullbot/

Your router's network, dhcp, and firewall files will be copied to ~/.mullbot/configs/

with the file names appended with .bkp

Your chosen VPN settings will be written into new versions of these files and saved to new files appended with .mullbot
If something goes wrong, and you still want to use this script, simply put your non-VPN versions of these files into ~/.mullbot/configs with .bkp at the end of the file names, and your working VPN configs into the .mullbot files.

When you select "Toggle VPN" the script checks whether you're connected to Mullvad and overwrites your router's config files with the appropriate local copies.

Please note that if the script hangs after the toggle operation, simply exit the script and reconnect to your router.

I made script to learn bash, git, and awk, and to get to grips with using OpenWrt.

I figured this would be a good way to learn, and make something that I'd find useful. Maybe you will too.
While I've tried to test it, it isn't guaranteed to work.

-- [Drewbert](https://www.drewbert.co.za/mullbot/)

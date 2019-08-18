# gcp-vpn
Automation to configure an OpenVPN node on a Google Cloud Platform instance

## Purpose:
VPN services are pretty popular these days, but their popularity makes them
targets for bad-guys.  This package tries to lower the barrier to run your
own VPN service hosted in Google's cloud.

It's not perfect.  Google still knows what sites your VPN node is hitting,
and it knows that the owner of your credit card is associated with this
traffic, but that's no worse than the commercial VPN services.  Except now
your IP address is some random GCP IP address, and you can change it whenever
you want by destrying and rebuilding the VPN node.  Also, being the single
user of your VPN service, you make a less lucrative target for bad-guys.

The default resources used are intended to generally fit within Google Cloud
Platform's ["Always Free" tier](https://cloud.google.com/free/docs/gcp-free-tier).
The only limit you are likely to run over is the 1GB egress traffic limit.
More info on [Google's Network pricing](https://cloud.google.com/compute/network-pricing).

That being said, this tool will automate the creation of resources which may
cost you money.  If you're planning on watching videos using this VPN, make
sure you do the math, so you're not surprised by the bandwidth bill.

## Quick Start
  * `git clone https://github.com/gregorydulin/gcp-vpn.git`
  * `cd gcp-vpn`
  * Optional: modify `group_vars/all/common_vars.yaml`
  * `./gcp-vpn`
  * Download Google's
    [Cloud Console](https://play.google.com/store/apps/details?id=com.google.android.apps.cloudconsole)
    from the Google Play Store to make fetching the .ovpn files easier
  * In the Cloud Console app, browse to your storage bucket and download an .ovpn file
  * Download one of these OpenVPN clients from Google Play Store
    * [OpenVPN for Android](https://play.google.com/store/apps/details?id=de.blinkt.openvpn)
    * [OpenVPN Connect](https://play.google.com/store/apps/details?id=net.openvpn.openvpn)
  * Load the .opvn file in the OpenVPN client
  * ...
  * Profit

## Destroy your VPN node so you can build a new one with a fresh IP address:
  * `./gcp-vpn --destroy`

## Supported platforms

### Probably supported
This script should execute successfully on the following oprating systems:
  * Google Cloud Shell
  * Google Chromebook Linux

### Possibly supported
This script may execute successfully on the following operating systems:
  * Ubuntu 18.04 LTS
  * Other Debian-based GNU/Linux distros


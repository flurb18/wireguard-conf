# Wireguard-conf

A set of shell scripts to manage a simple wireguard server.

# Installation

run 
```
git clone https://github.com/flurb18/wireguard-conf.git
cd wireguard-conf
cp config.env.example config.env
```
Edit conifg.env to your desired settings. See Configuration below. Then run
```
./init
```
to generate your server wireguard configuration file, by default named wg0.conf.

# Configuration

The wireguard server takes the IP range associated with the first three numbers in the config variable "```serveraddress```", with the last number as a wildcard.
For example, if ```serveraddress=10.8.0.1``` (the default value), the assigned ips will fall in the range ```10.8.0.0/24``` - all ips starting with ```10.8.0.``` .

The following options are available in config.env :

wgifname: The interface name of the wireguard server, and the name of the server's configuration file. Defaults to ```wg0```.
serveraddress: The ip address on the wireguard network of the server.
endpointip: The ip address on the public internet of the server.
listenport: The port wireguard should listen to.
dns: Allowed to be unset. If set, should point to a valid DNS server IP.
defaultallowedips: See wireguard documentation on the ``AllowedIPs`` setting. This is the default value written to your user configurations, by default ```0.0.0.0/0```.

You may also need a PostUp and PostDown script for your Wireguard server. To enable these set the postenabled variable. 
Alternatively configure your firewall to forward the appropriate traffic.

# Credits

me


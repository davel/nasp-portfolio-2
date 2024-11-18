# Building the network

![Network diagram](assets/NASP Network diagram.drawio.svg)

## On the VirtualBox host

In the VirtualBox host the three virtual machines were created. The TrueNAS and desktop
computers were assigned an "internal" network interface, each placed on a
different network. The gateway router was given three interfaces, two internal
one NAT.

## The router

Ubuntu was chosen as a server OS because it is capable of what we need, well
documented and has a predictable maintenance and release cadence.

The router was installed from the Ubuntu supplied ISO image.

The router's network interfaces were all configured via Netplan. The external
connection was configured to use DHCP.

### NAT

A complication is granting Internet access to nodes on the two internal
networks. Even though the router's Internet connection is NAT, VirtualBox
will not route packets addressed to the two private subnets.

To grant access we need to make the packets all appear to come from the
gateway router. This was achieved by using `nftables` to perform network address
translation on the gateway router's external interface.

That itself has is behind at least two more NAT routers, inside VirtualBox
and on the classroom's connection, before the publicly addressed Internet.

## TrueNAS

TrueNAS was chosen as an application server to try a non-Linux based open
source OS. It comes with a web interface built making it easy for us to
observe working from the desktop.

The static IPv4 configuration was set up using the text mode interface offered
during the initial install from the ISO image.

## Ubuntu desktop

Ubuntu desktop was chosen as it is a common and well documented open source
desktop OS.

The static IPv4 configuration was set up using the GUI.

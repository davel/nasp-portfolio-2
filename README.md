# Building the network

![Network diagram](assets/NASP Network diagram.drawio.svg)

## On the VirtualBox host

## The router

### NAT

A complication is granting Internet access to nodes on the two internal
networks. This was acheived by using nftables to perform network address
translation on the gateway router's external interface.

That itself has is behind at least two more NAT routers, inside VirtualBox
and on the classroom's connection, before the publically addressed Internet.

## TrueNAS

## Ubuntu desktop

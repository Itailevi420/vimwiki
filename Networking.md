## Gateway setup
* Source https://help.ubuntu.com/community/Internet/ConnectionSharing *

the commands that worked for me on my system to share internet access to RaPI0w
via USB (pwnagotchi)

```sh
uname -a
#Linux pop-os 6.2.6-76060206-generic #202303130630~1685473338~22.04~995127e SMP PREEMPT_DYNAMIC Tue M x86_64 x86_64 x86_64 GNU/Linux

ip addr show
# 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
#     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
#     inet 127.0.0.1/8 scope host lo
#        valid_lft forever preferred_lft forever
#     inet6 ::1/128 scope host
#        valid_lft forever preferred_lft forever
# 2: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
#     link/ether 28:7f:cf:25:90:27 brd ff:ff:ff:ff:ff:ff
#     altname wlp0s20f3
#     inet 192.168.137.82/24 brd 192.168.137.255 scope global dynamic noprefixroute wlo1
#        valid_lft 3489sec preferred_lft 3489sec
#     inet6 2a02:6680:210b:a95b:773b:7881:3833:2094/64 scope global temporary dynamic
#        valid_lft 7067sec preferred_lft 7067sec
#     inet6 2a02:6680:210b:a95b:22e0:5db0:2a53:cfcc/64 scope global dynamic mngtmpaddr noprefixroute
#        valid_lft 7067sec preferred_lft 7067sec
#     inet6 fe80::339e:907d:21a:13fa/64 scope link noprefixroute
#        valid_lft forever preferred_lft forever
# 3: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
#     link/ether 52:54:00:6a:c2:c0 brd ff:ff:ff:ff:ff:ff
#     inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
#        valid_lft forever preferred_lft forever
# 4: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
#     link/ether 02:42:4b:fa:a7:c6 brd ff:ff:ff:ff:ff:ff
#     inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
#        valid_lft forever preferred_lft forever
# 5: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
#     link/ether 9e:59:d1:fb:dd:1f brd ff:ff:ff:ff:ff:ff
#     inet 10.0.0.1/24 brd 10.0.0.255 scope global noprefixroute usb0
#        valid_lft forever preferred_lft forever
#     inet6 fe80::f7ed:91cc:4d29:9485/64 scope link noprefixroute
#        valid_lft forever preferred_lft forever

sudo iptables -A FORWARD -o wlo1 -i usb0 -s 10.0.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -F POSTROUTING
sudo iptables -t nat -A POSTROUTING -o wlo1 -j MASQUERADE
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```

Ubuntu Internet Gateway Method (iptables)

You will need two network cards in the gateway computer, or a PPP interface
and a network card. One network card (or PPP interface) connects to the Internet.
We will call this card eth0. The other card connects to your internal network.
We will call this eth1. It is also possible to do ICS with a single network card.
In this case, use eth0 for the Internet and eth0:0 for the internal network.

 1. Internet <<==>> eth0 <> Ubuntu gateway <> eth1 <<==>> Client PC

 2. Internet <<==>> ppp0 <> Ubuntu gateway <> eth1 <<==>> Client PC

 3. Internet <<==>> eth0 <> Ubuntu gateway <> eth0:0 <<==>> Client PC


 ### Gateway set up

The following example will focus on the most common gateway setup:
an Ubuntu computer with two wired network adapters
(eth0 and eth1) hosting ICS to a static internal network configured for the
192.168.0.x subnet.

For this example, eth0 is used to represent the network card connected to the
Internet, and eth1 represents the network card connected to a client PC. You
can replace eth0 and eth1 as needed for your situation. Also, any private IP
subnet can be used for the internal network IP addresses.

In summary:

    eth0 = the network adapter with internet (external or WAN).
    eth1 = the network adapter to which a second computer is attached (internal or LAN).
    192.168.0.x = IP subnet for eth1

Your setup may be different. If so, make sure to change them accordingly in the following commands.

#### Configure internal network card

Configure your internal network card (eth1) for static IP like so:
```sh
sudo ip addr add 192.168.0.1/24 dev eth1
```

**The external and internal network cards cannot be on the same subnet.**

*Configure NAT*

Configure iptables for NAT translation so that packets can be correctly routed
through the Ubuntu gateway.
```sh
sudo iptables -A FORWARD -o eth0 -i eth1 -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
sudo iptables -t nat -F POSTROUTING
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
> The first rule allows forwarded packets (initial ones).
> The second rule allows forwarding of established connection packets (and those related to ones that started).
> The third rule does the NAT.

IPtables settings need to be set-up at each boot *(they are not saved automatically*),
with the following commands:

  1. Save the iptables:
   ```sh
    sudo iptables-save | sudo tee /etc/iptables.sav
   ```

  2. Edit /etc/rc.local and add the following lines before the "exit 0" line:
  ```sh
  iptables-restore < /etc/iptables.sav
  ```

*Enable routing*

 3. Configure the gateway for routing between two interfaces by enabling IP forwarding:
 ```sh
 sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
 ```

 4. Edit `/etc/sysctl.conf`, and (up to **10.04**) add these lines:
```sh
  net.ipv4.conf.default.forwarding=1
  net.ipv4.conf.all.forwarding=1
```

The `/etc/sysctl.conf` edit is required because of the following bug in Hardy and later releases: Launchpad Bug Report

 5. From 10.10 onwards, it suffices to edit /etc/sysctl.conf and uncomment:
```sh
  #net.ipv4.ip_forward=1
```

... so that it reads:
```sh
  net.ipv4.ip_forward=1
```

Client set up   TODO

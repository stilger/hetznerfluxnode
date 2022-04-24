# hetznerfluxnode

From: https://medium.com/@oGGoldie/flux-multi-node-server-setup-7cd8887fe268

Gather Interface:

``` ip -o link```

```
cp -p /etc/network/interfaces /etc/network/interfaces.orig
vi /etc/network/interfaces
```
```
source /etc/network/interfaces.d/*
auto lo 
iface lo inet loopback
  
iface <NIC NAME (WILL BE SOMETHING LIKE "enp7s0")> inet manual  
auto vmbr0 
iface vmbr0 inet static   
  address <HOST IP/CIDR (THIS WILL BE PRESENT WHEN YOU FIRST OPEN THE FILE>
  gateway <GATEWAY IP (PROVIDED BY HETZNER, MOUSE OVER YOUR SERVER'S IP FOR INFO)>  
  bridge-ports <NIC NAME>  
  bridge-stp off   
  bridge-fd 1   
  hwaddress <MAC (PREVIOUSLY RECORDED)>
  pointopoint <GATEWAY IP>

auto vmbr100 
iface vmbr100 inet manual   
  bridge-ports none   
  bridge-stp off   
  bridge-fd 0
```

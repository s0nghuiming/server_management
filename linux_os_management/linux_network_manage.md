https://help.ubuntu.com/lts/serverguide/network-configuration.html
ip a
lshw -class network
ethtool eth4
ip addr add 10.102.66.200/24 dev enp0s25
ip link set dev enp0s25 up/down
ip address show dev enp0s25
ip route add default via 10.102.66.1
ip route show
ip addr flush eth0


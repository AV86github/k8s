nmcli connection modify ens18 IPv4.method manual IPv4.gateway 192.168.31.1 IPv4.address 192.168.31.212/24 IPv4.dns 192.168.31.200 IPv4.dns-search avl.home

nmcli connection modify ens18 IPv4.dns 192.168.31.200 IPv4.dns-search avl.home

nmcli con down ens18 && nmcli con up ens18

nmcli connection modify ens18 IPv4.dns 192.168.31.1
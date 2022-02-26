![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IP-BlockList-v4** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/scriptzteam/IP-BlockList-v4/master/ips.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ips
ipset -q create ips hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/scriptzteam/IP-BlockList-v4/master/ips.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ips $ip; done
iptables -I INPUT -m set --match-set ips src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).
Wall of shame (2022-02-26)
----

|IP|Number of (black)lists|
|---|--:|
185.100.87.174|10
89.185.85.100|9
45.9.20.73|9
185.220.102.243|9
171.25.193.78|9
45.153.160.2|9
23.154.177.5|9
171.25.193.25|9
89.185.85.253|9
185.220.102.252|9
80.67.167.81|9
45.154.168.39|9
5.183.209.217|8
5.2.76.207|8
116.105.212.31|8
179.43.175.170|8
185.220.102.244|8
185.220.102.248|8
185.220.102.249|8
162.247.74.74|8
5.2.69.50|8
171.25.193.77|8
198.98.49.20|8
185.220.101.4|8
185.254.75.32|8
23.154.177.21|8
23.154.177.20|8
185.100.87.72|8
185.220.102.4|8
185.220.102.8|8
46.19.139.18|8
122.194.229.45|8
205.185.116.59|8
116.235.92.247|8
107.189.29.207|8
171.25.193.20|8
209.141.58.240|8
185.220.102.254|8
185.220.102.253|8
64.113.32.29|8
112.85.42.229|8
185.56.80.65|8
45.153.160.133|8
81.17.18.59|8
62.102.148.68|8

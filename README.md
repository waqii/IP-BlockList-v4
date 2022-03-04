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
Wall of shame (2022-03-04)
----

|IP|Number of (black)lists|
|---|--:|
23.154.177.5|9
166.70.207.2|9
171.25.193.25|9
171.25.193.20|9
179.43.187.173|8
128.31.0.13|8
185.117.215.9|8
89.234.157.254|8
179.43.175.170|8
114.241.52.59|8
162.247.74.74|8
5.2.69.50|8
165.22.211.85|8
171.25.193.77|8
171.25.193.78|8
45.154.255.147|8
136.144.41.22|8
112.85.42.87|8
209.141.54.195|8
23.154.177.21|8
185.100.87.174|8
185.165.168.229|8
192.42.116.18|8
185.220.102.8|8
179.43.168.126|8
122.194.229.40|8
162.247.74.217|8
107.189.29.207|8
213.202.216.189|8
80.67.172.162|8
64.113.32.29|8
112.85.42.229|8
80.67.167.81|8
62.102.148.69|8
62.102.148.68|8
89.185.85.253|8
45.153.160.133|8
37.123.163.58|8

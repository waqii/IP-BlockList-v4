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
Wall of shame (2021-10-31)
----

|IP|Number of (black)lists|
|---|--:|
162.247.74.74|10
185.220.102.247|9
141.98.10.60|9
67.205.170.72|9
205.185.126.71|9
209.141.54.35|9
45.153.160.140|9
171.25.193.20|9
171.25.193.25|9
141.98.10.81|9
141.98.10.82|9
209.141.59.184|9
185.100.87.202|9
128.31.0.13|8
162.247.74.204|8
89.234.157.254|8
185.107.47.215|8
89.163.249.192|8
162.247.74.27|8
185.220.102.244|8
185.220.102.242|8
185.220.102.248|8
141.98.10.63|8
5.2.69.50|8
171.25.193.77|8
167.88.161.219|8
141.98.10.121|8
185.100.87.72|8
198.144.121.93|8
45.135.232.159|8
185.220.103.7|8
185.100.86.74|8
185.73.124.253|8
148.72.247.147|8
185.38.175.132|8
185.220.102.254|8
185.220.102.253|8
185.220.102.252|8
68.183.180.46|8
64.113.32.29|8
209.141.55.232|8
185.56.80.65|8
185.129.61.1|8
209.127.17.234|8
185.220.102.241|8
45.153.160.137|8
45.153.160.136|8
185.220.100.242|8
199.195.253.210|8
185.220.101.32|8
185.220.100.240|8
159.223.24.19|8
185.220.102.250|8

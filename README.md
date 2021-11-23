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
Wall of shame (2021-11-23)
----

|IP|Number of (black)lists|
|---|--:|
171.25.193.77|11
45.88.137.253|10
179.43.187.37|10
185.31.175.226|9
185.31.175.220|9
199.19.224.231|9
162.247.74.74|9
205.185.123.252|9
136.144.41.3|9
45.153.160.2|9
45.61.186.123|9
45.153.160.129|9
185.220.100.253|9
89.163.249.244|9
198.144.121.93|9
212.192.241.37|9
141.98.10.246|9
185.31.175.231|9
221.131.165.33|9
209.141.47.245|9
221.131.165.75|9
185.220.102.250|9
80.67.172.162|9
195.133.18.210|9
179.43.187.36|9
45.153.160.133|9
45.153.160.135|9
205.185.119.40|9
205.185.119.112|9
185.31.175.243|9
221.181.185.111|9
209.141.62.185|9
162.247.74.206|8
5.183.209.217|8
89.234.157.254|8
185.107.47.215|8
162.247.74.27|8
185.220.102.244|8
185.220.102.242|8
205.185.122.230|8
171.25.193.20|8
141.98.10.63|8
221.131.165.62|8
205.185.114.87|8
5.2.69.50|8
171.25.193.78|8
178.20.55.16|8
199.19.224.157|8
212.192.241.124|8
209.127.17.242|8
209.141.33.193|8
209.141.51.224|8
192.160.102.170|8
185.220.100.252|8
185.220.100.255|8
185.220.100.254|8
83.149.87.180|8
185.31.175.252|8
94.230.208.147|8
185.165.168.229|8
192.42.116.16|8
185.220.102.4|8
185.130.44.108|8
45.153.160.140|8
185.31.175.213|8
23.183.82.135|8
209.141.44.165|8
141.98.10.179|8
193.142.146.242|8
205.185.120.71|8
185.31.175.235|8
162.247.74.217|8
205.185.115.39|8
171.25.193.25|8
195.133.18.24|8
209.141.33.121|8
185.220.102.253|8
185.220.102.252|8
64.113.32.29|8
221.131.165.50|8
199.195.250.77|8
209.141.32.141|8
185.56.80.65|8
62.102.148.69|8
104.244.76.13|8
176.10.99.200|8
45.153.160.131|8
45.88.137.100|8
185.31.175.240|8
23.183.82.180|8
45.153.160.139|8
198.98.51.189|8
185.31.175.215|8
221.10.33.104|8
212.192.246.95|8
107.189.8.65|8

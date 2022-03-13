![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2022-03-13)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
45.9.20.73|-|9
162.247.74.206|rosaluxemburg.tor-exit.calyxinstitute.org|8
185.117.215.9|tor3.digineo.de|8
89.234.157.254|marylou.nos-oignons.net|8
185.107.47.215|tor-exit.r1.ci.ax|8
171.25.193.77|tor-exit1-readme.dfri.se|8
185.220.101.4|berlin01.tor-exit.artikel10.org|8
185.220.100.254|tor-exit-3.zbau.f3netze.de|8
185.220.100.255|tor-exit-4.zbau.f3netze.de|8
80.67.167.81|nosoignons.cust.milkywan.net|8
179.43.168.126|-|8
185.129.62.62|tor01.zencurity.dk|8
112.85.42.74|-|8
2.56.57.187|-|8
179.43.187.173|-|7
128.31.0.13|tor-exit.csail.mit.edu|7
218.92.0.221|-|7
122.194.229.37|-|7
122.194.229.38|-|7
116.105.212.31|-|7
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|7
112.85.42.119|-|7
112.85.42.15|-|7
5.2.69.50|-|7
171.25.193.78|tor-exit4-readme.dfri.se|7
185.107.47.171|tor-exit.r2.ci.ax|7
185.220.101.1|berlin01.tor-exit.artikel10.org|7
45.154.255.147|cust-147.keff.org|7
136.144.41.22|mx22.getcoopers.com|7
112.85.42.88|-|7
112.85.42.87|-|7
112.85.42.128|-|7
45.67.34.253|-|7
91.149.225.172|-|7
45.153.160.129|-|7
61.177.172.89|-|7
199.249.230.87|tor38.quintex.com|7
185.165.168.229|-|7
185.220.102.4|communityexit.torservers.net|7
185.220.102.8|185-220-102-8.torservers.net|7
116.105.216.128|-|7
45.153.160.140|-|7
46.19.139.18|-|7
61.177.172.154|-|7
122.194.229.40|-|7
122.194.229.45|-|7
36.110.228.254|-|7
162.247.74.217|perry.fellwock.tor-exit.calyxinstitute.org|7
116.110.3.253|-|7
144.22.251.63|-|7
171.25.193.20|tor-exit0-readme.dfri.se|7
171.25.193.25|tor-exit5-readme.dfri.se|7
80.67.172.162|algrothendieck.nos-oignons.net|7
112.85.42.229|-|7
112.85.42.227|-|7
112.85.42.124|-|7
179.43.150.82|-|7
45.153.160.133|-|7
45.153.160.139|-|7
61.177.172.92|-|7
185.220.100.249|tor-exit-10.zbau.f3netze.de|7
185.220.101.32|tor-exit-32.for-privacy.net|7
192.42.116.26|this-is-a-tor-exit-node-hviv126.hviv.nl|7
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|7
122.194.229.54|-|7
185.220.100.247|tor-exit-8.zbau.f3netze.de|7
112.85.42.73|-|7
185.34.33.2|tor.laquadrature.net|7

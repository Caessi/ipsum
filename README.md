![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

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
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2019-04-28)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
197.231.221.211|exit1.ipredator.se|12
80.82.77.33|sky.census.shodan.io|10
171.25.193.77|tor-exit1-readme.dfri.se|10
171.25.193.78|tor-exit4-readme.dfri.se|10
80.82.77.139|dojo.census.shodan.io|10
171.25.193.25|tor-exit5-readme.dfri.se|10
31.220.40.54|exit4.tor-network.net|10
185.244.25.205|-|10
171.25.193.20|tor-exit0-readme.dfri.se|10
185.220.101.1|-|9
89.234.157.254|marylou.nos-oignons.net|9
185.220.101.3|-|9
185.220.101.46|-|9
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|9
185.220.102.8|-|9
18.85.192.253|wholesomeserver.media.mit.edu|9
54.36.222.37|ip37.ip-54-36-222.eu|9
171.25.193.235|tor-exit3-readme.dfri.se|9
65.19.167.131|-|9
23.129.64.102|-|9
65.19.167.132|-|9
64.113.32.29|tor.t-3.net|9
42.61.24.202|-|9
62.102.148.67|-|9
111.53.76.186|-|9
104.248.95.188|-|8
23.24.163.78|23-24-163-78-static.hfc.comcastbusiness.net|8
151.53.243.41|-|8
58.42.228.170|-|8
164.132.51.91|91.ip-164-132-51.eu|8
206.189.217.240|-|8
178.73.215.171|178-73-215-171-static.glesys.net|8
94.102.49.190|flower.census.shodan.io|8
51.75.145.219|ns3130724.ip-51-75-145.eu|8
112.197.172.233|-|8
176.31.208.193|tor-exit1.netnik.xyz|8
185.220.101.33|-|8
198.96.155.3|exit.tor.uwaterloo.ca|8
185.220.101.5|-|8
176.10.104.240|tor1e1.digitale-gesellschaft.ch|8
185.220.101.44|-|8
71.6.146.185|pirate.census.shodan.io|8
46.165.245.154|-|8
58.135.224.36|-|8
192.160.102.170|ogopogo.relay.coldhak.com|8
109.201.133.100||8
185.220.102.4|-|8
104.192.3.226|tor-exit-node.drivingwitha.buzz|8
202.100.182.250|-|8
46.165.230.5|tor-exit.dhalgren.org|8
37.187.129.166|ns316491.ip-37-187-129.eu|8
193.32.163.89|-|8
77.247.181.162|chomsky.torservers.net|8
77.247.181.163|lumumba.torservers.net|8
80.13.251.203|lstlambert-658-1-232-203.w80-13.abo.wanadoo.fr|8
157.230.177.134|-|8
142.93.228.105|-|8
192.81.219.158|-|8
217.115.10.132|tor2.anonymizer.ccc.de|8
162.244.83.122|nyctorexit002.greyponyit.com|8
80.211.52.246|host246-52-211-80.serverdedicati.aruba.it|8
185.193.125.42|tor-exit2.0day.to|8
45.119.212.105|-|8
35.0.127.52|tor-exit.eecs.umich.edu|8
80.67.172.162|algrothendieck.nos-oignons.net|8
112.254.115.124|-|8
104.248.80.173|-|8
31.220.0.225|exit3.tor-network.net|8
212.21.66.6|tor-exit-4.all.de|8
162.243.160.215|-|8
87.120.36.157|no-rdns.mykone.info|8
5.199.130.188|tor.piratenpartei-nrw.de|8
77.247.181.165|politkovskaja.torservers.net|8
89.248.167.131|mason.census.shodan.io|8
178.128.160.212|-|8
139.59.151.149|salonatcom.com|8
185.220.101.34|-|8
139.59.154.219|-|8
206.189.152.215|randisgb.nolepstore.id|8
192.160.102.166|chaucer.relay.coldhak.com|8
195.206.105.217|zrh-exit.privateinternetaccess.com|8
165.227.183.88|-|8
185.254.122.114|-|8
89.197.161.164|89-197-161-164.virtual1.co.uk|8
185.100.87.206|geri.enn.lu|8

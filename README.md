# CoreDNS-Directory-Structure-Working-
CoreDNS Directory Structure (Working)


docker run -d \
  -p 53:53/udp \
  -p 53:53/tcp \
  -v ./coredns:/etc/coredns \
  coredns/coredns:latest \
  -conf /etc/coredns/Corefile
---------------------------------------
Directory Structure
[coredns]
	Corefile
	[zones]
		yourdomain.conf
		yourdomain.db
---------------------------------------
Sample Code Corefile:-
. {
    log
    errors
    reload 10s
    forward . 8.8.8.8 8.8.4.4
}

import /etc/coredns/zones/*.conf
-----------------------------------------------------------
Sample Code yourdomain.conf:-
. {
    log
    errors
    reload 10s
    forward . 8.8.8.8 8.8.4.4
}

import /etc/coredns/zones/*.conf

------------------------------------------------------------------------------------

Sample Code YourOwnNameServer:-

$ORIGIN vishalmahawar.shop.
$TTL 3600
@   IN  SOA ns1.vishalmahawar.shop. admin.vishalmahawar.shop. (
        2025012201 ; Serial
        3600       ; Refresh
        1800       ; Retry
        1209600    ; Expire
        86400      ; Minimum TTL
    )
    IN  NS  ns1.vishalmahawar.shop.
    IN  NS  ns2.vishalmahawar.shop.
    IN  NS  ns3.vishalmahawar.shop.
    IN  NS  ns4.vishalmahawar.shop.
    IN  NS  ns5.vishalmahawar.shop.

ns1 IN  A   65.21.145.81
ns2 IN  A   65.21.145.81
ns3 IN  A   65.21.145.81
ns4 IN  A   65.21.145.81
ns5 IN  A   65.21.145.81
www IN  A   65.21.145.81
mail IN A   65.21.145.81
may2-2025 IN A 65.21.145.81

-----------------------------------------------------------------------------------------

Sample Code YourOwnNameServer:-

$ORIGIN suhebalisabri.shop.
$TTL 3600
@   IN  SOA ns1.suhebalisabri.shop. admin.suhebalisabri.shop. (
        2025012201 ; Serial
        3600       ; Refresh
        1800       ; Retry
        1209600    ; Expire
        86400      ; Minimum TTL
    )
    IN  NS  ns1.suhebalisabri.shop.
    IN  NS  ns2.suhebalisabri.shop.
    IN  NS  ns3.suhebalisabri.shop.
    IN  NS  ns4.suhebalisabri.shop.
    IN  NS  ns5.suhebalisabri.shop.

ns1 IN  A   65.21.145.81
ns2 IN  A   65.21.145.81
ns3 IN  A   65.21.145.81
ns4 IN  A   65.21.145.81
ns5 IN  A   65.21.145.81
www IN  A   65.21.145.81
mail IN A   65.21.145.81
may2-2025 IN A 65.21.145.81

-----------------------------------------------------------------------------------------
Sample Code of suhebalisabri.shop.conf

suhebalisabri.shop {
    log
    errors
    bind 0.0.0.0
    file /etc/coredns/zones/suhebalisabri.shop.db
}

------------------------------------------------------------------------------------

may2-2025.suhebalisabri.shop

Directory Structure
[coredns]
	Corefile
	[zones]
		vishalmahawar.shop.conf
		vishalmahawar.shop.db
		suhebalisabri.shop.conf
		suhebalisabri.shop.db




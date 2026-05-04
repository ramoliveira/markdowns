# Networking Functions

## Content Delivery Network (CDN)

## Virtual Private Network (VPN)

## Quality of Service (QoS)

## Time to Live (TTL)

## Routing Loops

## IP (Internet Protocol)

## Examples

```
> nslookup www.professormesser.com

Non-authoritative answer:
Name:	www.professormesser.com
Address: 172.66.174.118
Name:	www.professormesser.com
Address: 104.20.22.204
```

```
> dig www.professormesser.com

; <<>> DiG 9.10.6 <<>> www.professormesser.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12054
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;www.professormesser.com.	IN	A

;; ANSWER SECTION:
www.professormesser.com. 137	IN	A	172.66.174.118
www.professormesser.com. 137	IN	A	104.20.22.204

;; Query time: 3 msec
;; SERVER: fe80::1%12#53(fe80::1%12)
;; WHEN: Wed Apr 29 17:11:42 -03 2026
;; MSG SIZE  rcvd: 73
```

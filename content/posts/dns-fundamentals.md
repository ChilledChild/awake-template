---
title: DNS Fundamentals
subtitle: Yes, DNS is on port 53.
category:
  - Networking
author: Danny Child
date: 2021-02-04T08:00:00.000Z
featureImage: /uploads/annie-spratt-afb6s2kibuk-unsplash.jpg
---
Domain Name System (DNS) is an application protocol found at ISO layer 7 and TCP/IP layer 5. It is used to associate IP addresses and domain names whenever a host requests the network location of another host. A DNS record can be stored on a dedicated DNS server, router, computer, or browser. There are multiple pieces of relational data that are stored in a DNS record, along with unique formats that provide an advantage based on the circumstance. While each type of record has its own name, in practice they are all generally referred to as a DNS record.

## What does DNS look like?

Using the Linux command `dig google.com` or the PowerShell command `Resolve-DnsName google.com`, the "A record" will be presented with the corresponding IP address. Additional parameters can be added to give a more detailed entry. All records will contain the fully qualified domain name (FQDN), record type, class code, Time-to-live (TTL), length of associated data, and the associated data (IP address, domain name, etc.).

| Name       | Type | TTL | Section | IPAddress                |
| ---------- | ---- | --- | ------- | ------------------------ |
| google.com | AAAA | 37  | Answer  | 2607:f8b0:4007:800::200e |
| google.com | A    | 150 | Answer  | 172.217.4.142            |

## DNS and rDNS

A DNS record states that google.com can be found at 8.8.4.4. However, using the previous commands with the IP address replacing the hostname will show a different type of record. The IP address will be reversed and presented as an FQDN (4.4.8.8.in-addr.arpa), and the destination will show the outward-facing Google DNS server (dns.google). The pointer (PTR) record is the relative opposite of the A or AAAA record. For simplicity, this is commonly known as reverse-DNS (rDNS).

| Name                 | Type | TTL   | Section | NaneHost   |
| -------------------- | ---- | ----- | ------- | ---------- |
| 4.4.8.8.in-addr.arpa | PTR  | 58138 | Answer  | dns.google |

## Common types of records

Understanding how IP addresses and domain names are associated, unique record types can be created for different data associations.

* A – Lookup a hostname to find the IPv4 address.
* AAAA – Lookup a hostname to find the IPv6 address.
* PTR – Lookup an IPv4 or IPv6 address to find the hostname.
* CNAME – Lookup a hostname alias.
* MX – Lookup servers for sending mail.
* NS – Lookup the DNS zone a domain is delegated to.
* SOA – Lookup the DNS server that supplies zone data.

## Where are these records?

DNS record are stored in multiple locations across multiple systems. Not only is there a dedicated server whose role is to answer DNS requests across the network, these records also exist in each host, network device, and browser. The “original” DNS record will exist in the DNS authoritative server, or the server that claims to have the "true" knowledge for where a resource is located. If no other DNS servers have the requested DNS record, this is the server that responds to requests and appropriately distributes a copy of the record.

## Why are the TTLs different lengths?

For availability! The TTL length (in seconds) depends on what is being requested and who is responding. In a correctly designed network, the server that is sure to have a statically assigned IP will have a longer TTL than the server that could change. For an organization that uses multiple DNS servers, High Availability (HA) will be implemented so DNS requests are assigned between DNS servers which are no longer overburdened. Once the TTL reaches 0, a new record will replace the expired record when the related resource is requested.

## Why is DNS split up in zones?

Networks can be segmented to increase security and administrative control. DNS zones are organized by domain while DNS functions can be combined with other network and security capabilities per zone. While a single DNS domain can function for a flat network, this would not be appropriate for a demilitarized zone (DMZ). Multiple zones can exist in one network segment, while another segment is dedicated for a specific purpose and requires separated technology.

The root zone is the highest-level domain that an administrator can control. In the example of [mitre.org](https://mitre.org), the MITRE web administrator will have control over mitre.com and [attack.mitre.com](https://attack.mitre.com), but not over `.com`, which is currently operated by [Verisign](https://www.verisign.com). In regards to hierarchy, `.com` is a top-level domain (TLD) while `mitre` is the second-level domain. For mitre, the organization could have a zone for mitre.org, and attack.mitre.org can have its own zone. Attack.mitre.org is considered a subdomain or mitre.org, but once the separate zone is created, traffic can be distinguished and be treated as two different sites. While similar in appearance, [mitre.com](https://mitre.com) offers equipment that is a little more athletic than technologic.

## How is DNS sent across a network?

At a basic level, DNS is sent over port 53. While most commonly seen over transport protocol UDP, DNS can use TCP and UDP to ensure consistency or speed across networks. UDP packets have a size limit of 512 bytes, so DNS related queries such as DNS zone transfers, IPv6 requests, DNSSEC, and many other DNS related protocols will use TCP due to size. If TCP is blocked for that port, the traffic can be sent over UDP in fragments, with varying success. DNS can be encapsulated with other protocols for security, which can also result in limited traffic visibility if not scoped correctly. With this encapsulation, DNS can also occur over ports 8080, 853, 5353.

There are many more aspects of DNS that will be covered in later posts. Additional reading by IETF and Cloudflare provides additional insight into DNS fundamentals.

[DNS Terminology (RFC 8499)](https://tools.ietf.org/html/rfc8499)

[Domain Names – Concepts and Facilities (RFC 1034)](https://tools.ietf.org/html/rfc1034)

[Cloudflare – What is DNS?](https://www.cloudflare.com/learning/dns/what-is-dns/)
The F5® Distributed Cloud DNS Reference Architecture
===================================================

# Contents

- [Introduction](#Introduction)
- [DNS Services Are Critical to Availability](#DNS-Services-Are-Critical-to-Availability)
- [Growing Pains](#Growing-Pains) 
- [Security Issues](#Security-Issues) 
- [The Traditional Solution](#The-Traditional-Solution) 
- [Solutions for a Changing Landscape](#Solutions-for-a-Changing-Landscape) 
- [Referece Architecture](#Referece-Architecture) 
- [Architecture Overview](#Architecture-Overview) 

# Introduction
The Domain Name System (DNS) was created in 1983 to enable people to easily identify all the computers, services, and resources connected to the Internet by name—instead of by Internet Protocol (IP) address, an impossible-to-memoris
e string of binary information.

A DNS server translates the domain names you type into a browser into an IP address, which allows your device to find the service or site you're looking for on the Internet.

Arguably the primary technology enabling the Internet, DNS is also one of the most important components in networking infrastructure. In addition to delivering content and applications, DNS also manages a distributed and redundant architecture to ensure high availability and fast user response time—so it is critical to have an available, intelligent, secure, and scalable DNS infrastructure. If DNS goes down, most web applications will stop working properly, affecting your business—and your brand.

This reference architecture provides guidelines for designing and implementing a Domain Name System (DNS) infrastructure using the F5® Distributed Cloud DNS SaaS platform.  

## DNS Services Are Critical to Availability
When a user requests a web page, that request is passed to a local DNS server, which in turn communicates with the main DNS servers. Everything works well until a traffic surge or an attacker floods the server with DNS query requests. If your main DNS server gets overloaded, it will stop responding, which can render your website unavailable.

DNS failures account for 41 percent of web infrastructure downtime, so it's essential to keep your DNS available. According Gartner [^1] , organizations lose between $140,000 and $540,000 for every hour their services are down. Downtime negatively affects customers, can lead to loss of revenue, and can even affect employees trying to access corporate resources, such as email.

That's why the importance of a strong DNS foundation can’t be overstated. Without one, your customers may not be able to access your content and applications when they want to—and if they can't get what they want from you, they'll likely go elsewhere.

[^1]: https://blogs.gartner.com/andrew-lerner/2014/07/16/the-cost-of-downtime/

## Growing Pains
There are many reasons why DNS requirements are growing so quickly. Over the last five years [^2] , the number of internet users has grown by over one billion and the number of DNS queries between 2016 and 2020 grew by over 300% from 40 billion per day to over 120 billion per day! [^3] 

[^2]: https://datareportal.com/reports/digital-2022-global-overview-report
[^3]: https://blog.apnic.net/2020/09/28/scaling-the-root-of-the-dns/

In addition, nearly 60 percent of web users say they expect a website to load on their mobile phone in three seconds or less.

Organizations are experiencing rapid growth in terms of applications as well as the volume of traffic accessing those applications. Plus, the web applications themselves are growing and continually becoming more complex. Every icon, URL, and piece of embedded content on a web page requires a DNS lookup. Simple smartphone apps can require numerous DNS queries just to load, but loading complex sites may require hundreds of DNS queries.


## Security Issues
If DNS is the backbone of the Internet—answering all the queries and resolving all the numbers so you can find your favorite sites—it’s also one of the most vulnerable points in your network. Due to the crucial role it plays, DNS is a high-value target for attackers. DNS DDoS attacks can flood your DNS servers to the point of failure or hijack and redirect requests to a malicious server. To prevent this, a distributed high-performing, secure DNS architecture is required.

A typical DNS server is capable of handling up to 150,000 DNS queries per second. High-performance DNS servers can handle around 200,000 queries per second. Malicious attacks can easily exceed those rates, as exemplified by DNS outages affecting, Dyn, The New York Times, LinkedIn, Network Solutions, and Twitter.

To address DNS surges and DNS DDoS attacks, companies add more DNS servers, which are not really needed during normal business operations. This costly solution also often requires manual intervention for changes. In addition, traditional DNS servers require frequent maintenance and patching, primarily for new vulnerabilities.

## The Traditional Solution
When looking for DNS solutions, many organizations select BIND (Berkeley Internet Naming Daemon), the Internet's original DNS resolver. Installed on approximately 80 percent of the world's DNS servers, BIND is an open-source project maintained by Internet Systems Consortium (ISC). ISC is a non-profit organization with a for-profit consulting arm called DNS-CO, which offers 4 different levels of subscriptions and support services.

Despite its popularity, BIND requires significant maintenance multiple times a year primarily due to vulnerabilities, patches, and upgrades. It can be downloaded freely, but needs servers (an additional cost, including support contracts) and an operating system. In addition, BIND typically scales to only 50,000 responses per second (RPS), making it vulnerable to both legitimate and malicious DNS surges.

## A Cloud Native SaaS-Based Solution 
The F5® Distributed Cloud DNS reference architecture provides a smarter way to respond and scale to DNS queries and takes into account a variety of network conditions and situations to distribute user application requests and application services based on business policies, data center conditions, network conditions, and application performance.

Instead of worrying about DNS outages and purchasing additional DNS infrastructure to combat surges, streamline your application deployment and management with automation and SaaS-based DNS from F5. Achieving a high-performance, responsive app experience requires consistent, scalable DNS functionality. Distributed Cloud DNS provides just that—so you can deliver fast, secure, and available applications across hybrid and multi-cloud environments.

# Referece Architecture 

<!-- ![F5® Distributed Cloud DNS Referece Architecture Diagram](https://github.com/s-archer/reference-architectures/blob/main/dns/XC%20DNS%20Reference%20Architecture%20Diagrams.jpeg) -->
![F5® Distributed Cloud DNS Referece Architecture Diagram](XC%20DNS%20Reference%20Architecture%20Diagrams.jpeg)

## Architecture Overview
The DNS infrastructure consists of the following main components:
- LDNS
- Root Server
- TLD Servers
- Threat Intelligence
- F5® Distributed Cloud Platform 
    - Built on a high-performance global anycast network to provide highly available and responsive DNS from our global points of presence (PoPs). 
- F5® Distributed Cloud Console
    - Part of the global controller for F5® Distributed Cloud Platform - Using this SaaS console, customers can provision services, obtain global observability, centralize logs and metrics, and create customized dashboards. The Console provides APIs that can be used for automation or integration with external services like Datadog, Splunk, etc.
- [Optional] DNS Hidden Primary Authoritative Servers
    - A stealth server that is a primary server for zone transfers. In this arrangement, the master name server that processes the updates is unavailable to general hosts on the Internet; it is not listed in the NS RRset. [^4]
- Origin Applications

[^4]: 'DNS Terminology' https://www.rfc-editor.org/rfc/rfc8499.html 

## Scale on Demand
BIG-IP DNS hyperscales to 100 million RPS, which means that even large surges of DNS requests (including the malicious ones) won’t disrupt your content or affect the availability of critical applications. Your network administrators can rest easier, knowing that your site will respond to all DNS queries and remain available even during an attack. Your brand is protected, and your company can avoid an embarrassing front-page story.

## Enhance Availability with BIG-IP DNS
The F5® Intelligent DNS Scale reference architecture helps ensure that your applications and content are continuously available to your users. One of the most important pieces of this architecture is the specifically designed DNS Express query response feature in BIG-IP DNS, which manages authoritative DNS queries by transferring zones from the primary DNS server to its own RAM.

BIG-IP DNS only has to open the DNS query packet once, as long as the request is for an address that’s in the zone that was transferred to DNS Express, simplifying the process and significantly improving performance and response times of your DNS architecture.

With DNS Express, the individual core of each BIG-IP device can answer approximately 125,000 to 200,000 requests per second, scaling up to more than 50 million query RPS, greater than 12 times the capacity of a typical primary DNS server.

## The BIG-IP Platform: Your Firewall in the DMZ
Each BIG-IP device is ICSA Labs Certified as a network firewall. By intelligently evaluating the reputation of Internet hosts, the BIG-IP device can prevent attackers from knocking your DNS offline with a DNS DDoS attack, stealing data, compromising corporate resources, or otherwise disrupting your business. 

In addition, DNSSEC can protect your DNS infrastructure, including cloud deployments, from cache poisoning attacks and domain hijacks. With DNSSEC support, you can digitally sign and support your DNS query with encrypted responses, enabling the resolver to determine the authenticity of the response and preventing DNS hijacking and cache poisoning. The F5® IP Intelligence service enhances your overall security by denying access to IP addresses known to be infected with malware, in contact with malware distribution points, and with poor reputations.

## DNS Services at the Edge of the Network
The F5® Intelligent DNS Scale reference architecture also helps keep your content and applications available by responding to DNS queries from the edge of the network, rather than from deep within your critical infrastructure. When you offload DNS responses to the BIG-IP platform, requests don’t reach the back end of your network, which greatly increases your ability to scale and respond to DNS surges along with protecting your DNS infrastructure.

By increasing the speed, availability, scalability, and security of your DNS infrastructure, the F5® Intelligent DNS Scale reference architecture makes sure your customers, and your employees, can access your critical web, application, and database services whenever they need them.

## Distributed DNS
This also applies to cloud deployments or infrastructures where DNS is distributed. Organizations can replicate their high-performance DNS infrastructure in almost any environment. They may have cloud DNS for disaster recovery/business continuity, or even a cloud DNS service with signed DNSSEC zones. F5® DNS Services enhanced AXFR support offers zone transfers from a BIG-IP device to any DNS service, enabling organizations to replicate DNS in physical, virtual, and cloud environments. The DNS replication service can be sent to other BIG-IP devices or other general DNS servers in data centers or clouds that are closest to the users.

In addition, organizations can send users to a site that will give them the best experience. BIG-IP DNS services use a range of load balancing methods and intelligent monitoring for each specific app and user. Traffic is routed according to your business policies, as well as current network and user conditions. BIG-IP DNS services includes an accurate, granular geolocation database, giving you control of traffic distribution based on user location.


## BIG-IP DNS and DNS Services
BIG-IP DNS is a global DNS solution, providing name services at the very edge of your service delivery and access networks. By employing geographic location services, it can direct users to the best service delivery data center based on their physical location.

BIG-IP DNS provides the following name services:

DNS services at the edge of the network for all internal and external services.
Geolocation services for pinpoint application or service delivery accuracy based on location of the mobile user.
The IP Intelligence service safeguards infrastructures by detecting and stopping access from IP addresses associated with malicious activity.
A single point of control for management of all global and local name services.
Additional BIG-IP intelligent services solutions such as global application delivery, policy enforcement, NAT64 and DNS64 translation, health monitors, and the F5® scripting language, iRules.
Support for global DNS services
Integration with DNS iRules for granular DNS decisions and name service delivery.
Support for service provider–specific protocols such as ENUM requests for SIP transactions.
BIG-IP LTM and DNS Services
Within the data center, BIG-IP Local Traffic Manager (LTM) can ensure that your applications and content remain highly available by creating a fault-tolerant architecture from the mobile edge through to the service. In addition to providing high availability, BIG-IP LTM also supports service provider–specific applications such as load balancing ENUM requests for SIP transactions.

BIG-IP LTM solutions for naming services include:

Integration with BIG-IP DNS to extend rich naming services into the local data center and services network.
Load balancing support for both local DNS and recursive DNS.
Support for service provider–specific protocols such as ENUM requests for SIP transactions.
Transparent health monitors to evaluate service health before sending users to the service. BIG-IP LTM can relay health information back to BIG-IP DNS to bring application awareness to the edge of the SDN.
Integration with iRules for granular DNS decisions and name service delivery.

## Deploying a Complete Service Delivery Infrastructure
The F5® Intelligent DNS Scale reference architecture adjusts for high-availability and high-volume applications while simultaneously supporting millions of user requests per second. They work together with other BIG-IP service delivery features, such as the iRules scripting language, transparent application monitoring, , and other IP-related services to create a complete service delivery infrastructure: the F5® Service Delivery Network. Seamless scale and flexibility is achieved by leveraging the intelligent service delivery platform common to all BIG-IP devices.

## Conclusion
By using the F5® Intelligent DNS Scale reference architecture, organizations can:

Increase the speed, availability, scalability, and security of their DNS infrastructure.
Reduce complexity and cost by eliminating unnecessary additional DNS servers.
Enjoy the peace of mind that comes with knowing their site will respond to all DNS requests.
The F5® Intelligent DNS Scale reference architecture is an end-to-end DNS delivery solution that improves web performance by reducing DNS latency, protects your web properties and brand reputation by mitigating DNS DDoS attacks, reduces data center costs by consolidating DNS infrastructure.  Most importantly, it directs your customers to the best performing components for optimal application and service delivery.

The F5® Intelligent DNS Scale reference architecture also delivers the peace of mind that comes with knowing that your web applications will respond to all DNS queries—keeping your content and applications available to your users wherever and whenever they want to access them.

F5® Distributed Cloud DNS:tfd
https://f5cloud.zendesk.com/hc/en-us/sections/7057223802519-DNS-Management
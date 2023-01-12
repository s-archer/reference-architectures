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
    - [Scale on Demand](#Scale-on-Demand)
    - [Enhanced Availability](#Enhanced-Availability)
    - [DNS Security](#DNS-Security)
    - [DNS Services at the Edge](#DNS-Services-at-the-Edge)
    - [Distributed DNS](#Distributed-DNS)
- [F5® Distributed Cloud DNS Services](#F5®-Distributed-Cloud-DNS-Services)
    - [Deploying a Complete Application Delivery Infrastructure](#Deploying-a-Complete-Application-Delivery-Infrastructure) 
    - [Conclusion](#Conclusion)


# Introduction
The Domain Name System (DNS) was created in 1983 to enable people to easily identify all the computers, services, and resources connected to the Internet by name—instead of by Internet Protocol (IP) address, an impossible-to-memorise string of binary information.

A DNS server translates the domain names you type into a browser into an IP address, which allows your device to find the service or site you're looking for on the Internet.

Arguably the primary technology enabling the Internet, DNS is also one of the most important components in networking infrastructure. In addition to delivering content and applications, DNS also manages a distributed and redundant architecture to ensure high availability and fast user response time—so it is critical to have an available, intelligent, secure, and scalable DNS infrastructure. If DNS goes down, most web applications will stop working properly, affecting your business—and your brand.

This reference architecture provides guidelines for designing and implementing a Domain Name System (DNS) infrastructure using the F5® Distributed Cloud DNS SaaS platform.  

## DNS Services Are Critical to Availability
When a user requests a web page, that request is passed to a local DNS server, which in turn communicates with the main DNS servers (DNS Root Server, Top-Level Domain Servers, Second-Level Domain Servers and so on). Everything works well until a traffic surge or an attacker floods the server with DNS query requests. If your main DNS server gets overloaded, it will stop responding, which can render your website unavailable.

DNS failures account for 41 percent of web infrastructure downtime, so it's essential to keep your DNS available. According Gartner [^1] , organisations lose between $140,000 and $540,000 for every hour their services are down. Downtime negatively affects customers, can lead to loss of revenue, and can even affect employees trying to access corporate resources, such as email.

That's why the importance of a strong DNS foundation can’t be overstated. Without one, your customers may not be able to access your content and applications when they want to—and if they can't get what they want from you, they'll likely go elsewhere.

[^1]: https://blogs.gartner.com/andrew-lerner/2014/07/16/the-cost-of-downtime/

## Growing Pains
There are many reasons why DNS requirements are growing so quickly. Over the last five years [^2] , the number of internet users has grown by over one billion and the number of DNS queries between 2016 and 2020 grew by over 300% from 40 billion per day to over 120 billion per day! [^3] 

[^2]: https://datareportal.com/reports/digital-2022-global-overview-report
[^3]: https://blog.apnic.net/2020/09/28/scaling-the-root-of-the-dns/

In addition, according to Google, 53 percent of visits to a mobile web sites are abandoned if it takes longer than 3 seconds to load the page. [^4]

[^4]: https://www.thinkwithgoogle.com/consumer-insights/consumer-trends/mobile-site-load-time-statistics/ 

Organisations are experiencing rapid growth in terms of applications as well as the volume of traffic accessing those applications. Plus, the web applications themselves are growing and continually becoming more complex. Every icon, URL, and piece of embedded content on a web page requires a DNS lookup. Simple smartphone apps can require numerous DNS queries just to load, but loading complex sites may require hundreds of DNS queries.


## Security Issues
If DNS is the backbone of the Internet—answering all the queries and resolving all the IP addresses so you can find your favorite sites—it’s also one of the most vulnerable points in your infrastructure. Due to the crucial role it plays, DNS is a high-value target for attackers. DNS DDoS attacks can flood your DNS servers to the point of failure or hijack and redirect requests to a malicious server. To prevent this, a distributed high-performing, secure DNS architecture is required.

A typical DNS server is capable of handling up to 150,000 DNS queries per second. High-performance DNS servers can handle around 200,000 queries per second. Malicious attacks can easily exceed those rates, as exemplified by DNS outages affecting, Dyn, The New York Times, LinkedIn, Network Solutions, and Twitter.

To address DNS surges and DNS DDoS attacks, companies add more DNS servers, which are not really needed during normal business operations. This costly solution also often requires manual intervention for changes. In addition, traditional DNS servers require frequent maintenance and patching, primarily for new vulnerabilities.

## The Traditional Solution
When looking for DNS solutions, many organisations select BIND (Berkeley Internet Naming Daemon), the Internet's original DNS resolver. Installed on approximately 80 percent of the world's DNS servers, BIND is an open-source project maintained by Internet Systems Consortium (ISC). ISC is a non-profit organisation with a for-profit consulting arm called DNS-CO, which offers 4 different levels of subscriptions and support services.

Despite its popularity, BIND requires significant maintenance multiple times a year primarily due to vulnerabilities, patches, and upgrades. It can be downloaded freely, but needs servers (an additional cost, including support contracts) and an operating system. In addition, BIND typically scales to only 50,000 responses per second (RPS), making it vulnerable to both legitimate and malicious DNS surges.

## A Cloud Native SaaS-Based Solution 
The F5® Distributed Cloud DNS provides a smarter way to respond and scale to DNS queries and takes into account a variety of network conditions and situations to distribute user application requests and application services based on business policies, data center conditions, network conditions, and application performance.

Instead of worrying about DNS outages and purchasing additional DNS infrastructure to combat surges, streamline your application deployment and management with automation and SaaS-based DNS from F5. Achieving a high-performance, responsive app experience requires consistent, scalable DNS services. F5® Distributed Cloud DNS provides just that—so you can deliver fast, secure, and available applications across hybrid and multi-cloud environments.

# Referece Architecture 

## Architecture Overview
The DNS infrastructure consists of the following main components:
- Legitimate User [The Resolution Client]
    - Is the initiator that needs to resolve a DNS name (and record type[^5]), for example the fully qualified domain name (FQDN) for www.example.com.  
- LDNS (Local DNS)
    - Recursive resolver or full-service resolver configured as the primary resolver for the resolution client.
- Root Servers
    - The DNS is a hierarchy; the root zone is the zone that has no parent, as it stands at the top of the DNS hierarchy. Root servers are the authoritative name servers that answer queries for the contents of the root zone.  The root zone (.) contains all the information needed to find top-level domains (.com or .uk for example).
- TLD Servers
    - Top-Level Domain servers are the authoritative name servers that answer queries for the contents of the top-level domain zone.  The top-level domain zone (.) contains all the information needed to find second-level domains (example.com).
- Threat Intelligence
    - Using a frequently updated list of threat sources and high-risk IP addresses, Threat Intelligence delivers contextual awareness and analysis of IP requests to identify threats from multiple sources across the Internet. The service draws on the expertise of a global threat-sensor network to detect malicious activity and IP addresses.
- F5® Distributed Cloud Platform 
    - Built on a high-performance global anycast network to provide highly available and responsive DNS from F5's global points of presence (PoPs).  The platform is protected by F5 DDoS mitigation services that protect against large-scale volumetric DDoS in real time, defending the DNS services.
    - F5® Distributed Cloud DNS can be configured as Primary Authoritative DNS for your zone files or as a Secondary DNS with copies of your zone files that are read-only.
    - F5® Distributed Cloud DNS can perform DNS Load-Balancing, also known as Global Server Load-Balancing (GSLB).
- F5® Distributed Cloud Console
    - Part of the global controller for F5® Distributed Cloud Platform - Using this SaaS console, customers can provision services, obtain global observability, centralise logs and metrics, and create customised dashboards. The Console provides self-service creation of API credentials, and APIs that can be used for automation or integration with external services like Datadog, Splunk, etc.
- [Optional] DNS Hidden Primary Authoritative Servers
    - A stealth server that is a primary server for zone transfers. In this arrangement, the master name server that processes the updates is unavailable to general hosts on the Internet; it is not listed in the NS RRset[^6].  
- Origin Applications
    - The endpoint[s] hosting the application identified by the FQDN.

[^5]: '3.2.2. TYPE values' https://www.ietf.org/rfc/rfc1035.html
[^6]: 'DNS Terminology' https://www.rfc-editor.org/rfc/rfc8499.html 

<!-- Insert blank lines using &nbsp; followed by a blank line -->

&nbsp;

&nbsp;

![F5® Distributed Cloud DNS Referece Architecture Diagram](XC%20DNS%20Reference%20Architecture%20Diagrams.jpeg)

## Scale on Demand
F5® Distributed Cloud DNS hyperscales to millions of RPS, which means that even large surges of DNS requests (including the malicious ones) won’t disrupt your content or affect the availability of critical applications. Your network administrators can rest easier, knowing that your site will respond to all DNS queries and remain available even during an attack. Your brand is protected, and your company can avoid an embarrassing front-page story.

## Enhanced Availability
As a SaaS-based, cloud-delivered solution, F5® Distributed Cloud DNS offers global auto-scaling, so you keep up with demand as the number of applications increases, traffic patterns change, and request volumes grow exponentially. Adjust DNS and security policies in real time and publish new apps with DNS instantaneously, all
while only paying for what you use, with no added overhead or costs.

F5® Distributed Cloud DNS helps ensure that your applications and content are continuously available to your users. Built-in redundancy makes your system available even with primary failures.

## DNS Security
High-performance applications must be kept secure. That means ensuring
not only uptime and availability but also protection from exploitation. With built-in
DDoS protection, automatic failover, TSIG authentication, and DNSSEC capabilities,
this service helps protect your applications from DDoS attacks and other threats.

By intelligently evaluating the reputation of Internet hosts, F5® Distributed Cloud DNS can prevent attackers from knocking your DNS offline with a DNS DDoS attack, stealing data, compromising corporate resources, or otherwise disrupting your business. 

In addition, DNSSEC can protect your DNS infrastructure, including cloud deployments, from cache poisoning attacks and domain hijacks. With DNSSEC support, you can digitally sign and support your DNS query with encrypted responses, enabling the resolver to determine the authenticity of the response and preventing DNS hijacking and cache poisoning. 

## DNS Services at the Edge
F5® Distributed Cloud DNS helps keep your content and applications available by responding to DNS queries from the edge of the network, closer to your customers, and your employees,  rather than from deep within your critical infrastructure. When you offload DNS responses to F5® Distributed Cloud Platform, requests don’t reach the back end of your network, which greatly increases your ability to scale and respond to DNS surges along with protecting your DNS infrastructure.

By increasing the speed, availability, scalability, and security of your DNS infrastructure, the F5® Distributed Cloud DNS makes sure your customers, and your employees, can access your critical web, application, and database services whenever they need them.

## Distributed DNS
Organisations can send users to a site that will give them the best experience. F5® Distributed Cloud DNS services use a range of load balancing methods and intelligent monitoring for each specific app and user. Traffic is routed according to your business policies, as well as current network and user conditions. F5® Distributed Cloud DNS services includes an accurate, granular geolocation database, giving you control of traffic distribution based on user location.

In addition, F5® Distributed Cloud DNS Services AXFR supports automatic zone transfers from any DNS service, enabling organisations to replicate DNS in physical, virtual, and cloud environments. 

# F5® Distributed Cloud DNS Services
F5® Distributed Cloud DNS is a global DNS solution, providing name services at the very edge of your service delivery and access networks. By employing geographic location services, it can direct users to the best service delivery data center based on their physical location.

F5® Distributed Cloud DNS provides the following name services:

- DNS services at the edge of the network for all external services.
- Geolocation services for pinpoint application or service delivery accuracy based on the location of the mobile user.
- The Threat Intelligence service safeguards infrastructures by detecting and stopping access from IP addresses associated with malicious activity.
- A single point of control for management of all global and local name services.
- Support for global DNS services


## Deploying a Complete Service Delivery Infrastructure
F5® Distributed Cloud DNS enables high-availability and high-volume applications while simultaneously supporting millions of user requests per second. It works seamlessly with the suite of F5® Distributed Cloud Application Delivery and Application Security SaaS services to create a complete application delivery infrastructure:

- Security
    - DDoS Mitigation
    - Web Application Firewall (WAF)
    - Bot Defense
    - API Security
    - WAAP (a combination of the four previous services)
    - Application Infrastructure Protection (CWPP)
    - Client-Side Defense
    - Aggregator Management
- Fraud and Risk
    - Account Protection
    - Authentication Intelligence
- Multi-Cloud Networking
    - Load-Balancer and K8s Gateway
    - Multi-Cloud Transit
    - Global Network
    - Private Link
- Performance and Reliability
    - CDN 
    - Observability

## Conclusion
By using F5® Distributed Cloud DNS, organisations can:

- Deploy and deliver primary DNS in minutes. Configure and provision primary and secondary DNS inminutes, powered by a cloudbased, globally distributed
anycast network.
- Accelerate release velocity.  Integrate DNS into CI/CD pipelines using REST-based declarative APIs.
- Maintain high availability.  Redundancy keeps your system available even with primary failures.
- Add resilience to your existing DNS infrastructure.  Ensure high availability of your DNS environments with seamless failover to F5 Distributed Cloud DNS.
- Scale instantly.  Automatically scale to respond to large query volumes.
- Secure applications.  Prevent distributed denialof-service (DDoS) attacks or manipulation of domain responses with built-in protection.
- Get utility-based pricing.  Pay only for what you use.  Pricing is based on the number of zones, and options include an Individual Plan, Teams Plan, and Organization Plan, with a free monthly version available. 

DevOps-friendly F5® Distributed Cloud DNS delivers the high performance, security, and global resiliency—across clouds, geographies, and availability zones—that your users expect from your apps in today’s demanding marketplace.

F5® Distributed Cloud DNS reference architecture also delivers the peace of mind that comes with knowing that your web applications will respond to all DNS queries—keeping your content and applications available to your users wherever and whenever they want to access them.

[F5® Distributed Cloud DNS](https://www.f5.com/cloud/products/dns)
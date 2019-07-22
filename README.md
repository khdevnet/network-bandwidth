# Network Fundamentals
* [Glossary](#glossary)
* [HTTP](#http)
* [Comparing Use Cases For REST, GraphQL, Webhooks, and gRPC](#comparing-use-cases-for-rest-graphql-webhooks-and-grpc)
* [Network-bandwidth](#network-bandwidth)

## HTTP
* HTTP is an Application Protocol for transferring Resources across the internet.
* URL (Uniform Resource Locator) is a unique identifier used to locate a resource on the internet
* HTTP messages are how data is exchanged between a server and a client. There are two types of messages: requests sent by the client to trigger an action on the server, and responses, the answer from the server. (HTTP Request + HTTP Response = HTTP Transaction)
* A media type (also known as a Multipurpose Internet Mail Extensions or MIME type) is a standard that indicates the nature and format of a document, file, or assortment of bytes. It is defined and standardized in IETF's RFC 6838.
* HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to the user's web browser. The browser may store it and send it back with the next request to the same server. Typically, it's used to tell if two requests came from the same browser — keeping a user logged-in, for example. It remembers stateful information for the stateless HTTP protocol.
* HTTP has a **persistent connection* function that allows the channel to remain open rather than be closed after a requested exchange of data. Can be use to improve performance of http.
* A proxy server is a computer that acts as an intermediary between the user's computer and the Internet. It allows client computers to make indirect network connections to other network services. 

### HTTP connections
![](https://github.com/khdevnet/network-fundamentals/blob/master/docs/connections.png)
* **Parallel Connections** web browser can open multiple connections and perform multiple HTTP transactions in parallel.
* **persistent connections** TCP connections that are kept open after transactions complete are called persistent
connections. Nonpersistent connections are closed after each transaction. Persistent connections stay
open across transactions, until either the client or the server decides to close them. There are two types of persistent connections: the older HTTP/1.0+ "keep-alive" connections and the modern HTTP/1.1 "persistent" connections. **[Keep-alive]**(https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Keep-Alive) is deprecated and no longer documented in the current HTTP/1.1 specification.
HTTP/1.1 **persistent connections** are active by default. HTTP/1.1 assumes all connections are persistent unless otherwise indicated. HTTP/1.1 applications have to explicitly add a Connection: close.

HTTP/1.1 permits optional **request pipelining over persistent connections**. This is a further performance optimization over keep-alive connections. Multiple requests can be enqueued before the responses arrive. While the first request is streaming across the network to a server on the other side of the globe, the second and third requests can get underway. This can improve performance in highlatency
network conditions, by reducing network round trips.

## Comparing Use Cases For REST, GraphQL, Webhooks, and gRPC

* REST: A stateless architecture for data transfer that is dependent on hypermedia. REST can tie together a wide range of resources that might be requested in a variety of formats for different purposes. REST is fundamentally concerned with stateless resource management, so it’s best used in such situations. Systems requiring rapid iteration and standardized HTTP verbiage will find REST best suited for their purposes.
* gRPC: A nimble and lightweight system for requesting data. gRPC, on the other hand, is best used when a system requires a set amount of data or processing routinely, and in which the requester is either low power or resource-jealous. The IoT is a great example of this.
* GraphQL: An approach wherein the user defines the expected data and format of that data. GraphQL is from Facebook, and that pedigree demonstrates its use case well — situations in which the requester needs the data in a specific format for a specific use. In those cases, those data formats and the relations between them are vitally important, and no other solution provides the same level of interconnected provision of data.
* Webhooks: Data updates to be served automatically, rather than requested. Finally, Webhooks are best used when the API in question primarily updates clients. While such APIs can also have other functions, even RESTful ones, the primary use of a Webhook microservice should be to update clients and provide updated, provisioned data upon the creation of the new, updated resource.

## Network-bandwidth
Bandwidth is the capacity of a wired or wireless network communications link to transmit the maximum amount of data from one point to another over a computer network or internet connection in a given amount of time -- usually one second. Synonymous with capacity, bandwidth describes the data transfer rate.

The maximum capacity of a network connection is only one factor that affects network performance. **Packet loss, latency and jitter** can all degrade network throughput and make a high-capacity link perform like one with less available bandwidth. An end-to-end network path usually consists of multiple network links, each with different bandwidth capacity. As a result, the link with the lowest bandwidth is often described as the bottleneck, because the lowest bandwidth connection can limit the overall data capacity of all the connections in the path.

### Packet loss
Packet loss is the failure of one or more transmitted packets to arrive at their destination. This event can cause noticeable effects in all types of digital communications.
* In data, packet loss produces errors.
* In videoconference environments it can create jitter.
* In pure audio communications, such as VoIP, it can cause jitter and frequent gaps in received speech.
* In the worst cases, packet loss can cause severe mutilation of received data, broken-up images, unintelligible speech or even the complete absence of a received signal.

### Latency
Latency is the delay from input into a system to desired outcome; the term is understood slightly differently in various contexts and latency issues also vary from one system to another. Latency greatly affects how usable and enjoyable electronic and mechanical devices as well as communications are.    

Latency in communication is demonstrated in live transmissions from various points on the earth as the communication **hops** between a ground transmitter and a satellite and from a satellite to a receiver each take time. People connecting from distances to these live events can be seen to have to wait for responses. This latency is the wait time introduced by the signal travelling the geographical distance as well as over the various pieces of communications equipment.

### hop
In a packet-switching network, a hop is the trip a data packet takes from one router or intermediate point to another in the network. On the Internet (or a network that uses TCP/IP), the number of hops a packet has taken toward its destination (called the "hop count") is kept in the packet header. A packet with an exceedingly large hop count is discarded.

### Jitter
Jitter is any deviation in, or displacement of, the signal pulses in a high-frequency digital signal. The deviation can be in terms of amplitude, phase timing or the width of the signal pulse. Among the causes of jitter are electromagnetic interference (EMI) and crosstalk with other signals. Jitter can cause a display monitor to flicker, affect the ability of the processor in a desktop or server to perform as intended, introduce clicks or other undesired effects in audio signals, and loss of transmitted data between network devices. The amount of allowable jitter is highly dependent on the application.


Jitter in IP networks is the variation in the latency on a packet flow between two systems, when some packets take longer to travel from one system to the other. Jitter results from network congestion, timing drift and route changes.

## Glossary
* A TCP socket is an endpoint instance defined by an IP address and a port in the context of either a particular TCP connection or the listening state.

* A port is a virtualisation identifier defining a service endpoint (as distinct from a service instance endpoint aka session identifier).

* A TCP socket is not a connection, it is the endpoint of a specific connection.

There can be concurrent connections to a service endpoint, because a connection is identified by both its local and remote endpoints, allowing traffic to be routed to a specific service instance.
There can only be one listener socket for a given address/port combination.

# Resources
* [Simple Web Server](https://codehosting.net/blog/BlogEngine/post/Simple-C-Web-Server)
* [bandwidth](https://searchnetworking.techtarget.com/definition/bandwidth)
* [packet-loss](https://searchnetworking.techtarget.com/definition/packet-loss)
* [latency](https://whatis.techtarget.com/definition/latency)
* [hop](https://whatis.techtarget.com/definition/hop)
* [jitter](https://searchunifiedcommunications.techtarget.com/definition/jitter)
* [when-to-use-what-rest-graphql-webhooks-grpc](https://nordicapis.com/when-to-use-what-rest-graphql-webhooks-grpc/)

# Distributed web infrastructure

![Image of a simple web stack](https://github.com/doncarbon/alx-system_engineering-devops/blob/d8b21df5555b301e73ec36c550abc667216ef824/0x09-web_infrastructure_design/2-secured_and_monitored_web_infrastructure.jpg)


# Description

This is a 3-server web infrastructure that is secured, monitored, and serves encrypted traffic.

# Details

+ Firewalls: Firewalls are added to enhance the security of the infrastructure by controlling incoming and outgoing traffic based on predetermined security rules. Each firewall provides an additional layer of protection against unauthorized access and malicious attacks.

+ SSL Certificate and HTTPS: An SSL certificate is added to enable HTTPS, which encrypts the traffic between the client's browser and the web server. This encryption ensures that sensitive information exchanged between the client and the server remains secure from interception or tampering.

+ Monitoring Clients: Monitoring clients are installed on each server to collect performance metrics, log data, and other relevant information. These clients send data to a centralized monitoring system (e.g., Sumo Logic) for analysis and alerting. Having monitoring clients on each server allows for comprehensive monitoring of the entire infrastructure.

+ Monitoring: Monitoring is used to track the health, performance, and availability of the web infrastructure components. It helps identify issues proactively, optimize performance, and ensure uninterrupted service for users.

+ QPS Monitoring: To monitor the web server's Queries Per Second (QPS), you can configure the monitoring tool to track the incoming requests and measure the rate at which the server processes them. This helps identify performance bottlenecks and scale resources accordingly.

+ Load Balancer (HAproxy): Added to distribute incoming traffic among multiple web servers, ensuring high availability and scalability.

+ Additional Web and Application Servers: Added for redundancy and to handle increased traffic load.

+ Server: A server is a computer program or device that provides functionality for other programs or devices, known as clients. In this context, it refers to a physical or virtual machine that hosts the web infrastructure components.

+ Domain Name: The domain name (www.foobar.com) is a human-readable address that maps to the IP address of the server (8.8.8.8 in this case). It allows users to access the website using a memorable and easy-to-use name rather than typing the IP address directly.

+ www DNS Record: The www DNS record is a type of DNS record called a CNAME (Canonical Name) record. It is used to alias the domain name to another domain name, in this case, pointing www.foobar.com to the server's IP address.

+ Web Server (Nginx): The web server handles incoming HTTP requests from users' browsers and serves static content (HTML, CSS, JavaScript files) directly. It may also act as a reverse proxy, passing requests to the application server for dynamic content.

+ Application Server: The application server executes the application code (e.g., PHP, Python, Node.js) and generates dynamic content in response to client requests. It interacts with the database to retrieve and store data as needed.

+ Database (MySQL): The database stores and manages the website's data. It allows for efficient storage, retrieval, and manipulation of structured data, such as user accounts, posts, or product information.

+ Communication with User's Computer: The server communicates with the user's computer over the internet using the HTTP protocol. When a user types www.foobar.com into their browser, the browser sends an HTTP request to the server, which responds with the requested web page.

## Load Balancer Configuration:

+ Distribution Algorithm: HAproxy is configured with a round-robin distribution algorithm. This algorithm routes each new connection to the next available server in a circular manner, evenly distributing the load among all available servers.

+ Active-Active or Active-Passive Setup: The load balancer enables an Active-Active setup, where all web servers are actively serving traffic simultaneously. In Active-Passive setup, only one server is actively serving traffic, while others act as backups and take over only if the active server fails.

## Database Primary-Replica Cluster:

+ How it Works: In a Primary-Replica (Master-Slave) cluster, the Primary node (Master) handles all write operations and replicates data changes to Replica nodes (Slaves). The Replica nodes serve read-only queries, improving read scalability and providing redundancy in case the Primary node fails.

+ Difference between Primary and Replica: The Primary node handles write operations, ensuring data consistency and integrity. The Replica nodes serve read queries, distributing read load and improving performance. In case of Primary node failure, one of the Replica nodes can be promoted to Primary to maintain database operations.



## Issues

+ Terminating SSL at Load Balancer Level: Terminating SSL at the load balancer exposes decrypted traffic within the internal network, potentially compromising sensitive information if the internal network is compromised.

+ Single MySQL Server for Writes: Having only one MySQL server capable of accepting writes creates a single point of failure. If this server goes down, the application won't be able to write data to the database, leading to service interruptions or data loss.

+ Uniform Server Components: Using servers with all the same components (database, web server, and application server) might lead to issues if one of the components has a vulnerability or experiences a failure. It's advisable to have a diverse mix of server types to mitigate such risks.
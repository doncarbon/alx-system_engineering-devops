# Simple Web Stack

![Image of a simple web stack](https://github.com/doncarbon/alx-system_engineering-devops/blob/20b6ada2ee562608052ca0405016e38462869d55/0x09-web_infrastructure_design/0-simple_web_stack.jpg)


## Description

A lot of websites are powered by simple web infrastructure, a lot of time it is composed of a single server with a LAMP stack. This is one server web infrastructure that hosts the website that is reachable via www.foobar.com.

## Details

+ Server: A server is a computer program or device that provides functionality for other programs or devices, known as clients. In this context, it refers to a physical or virtual machine that hosts the web infrastructure components.

+ Domain Name: The domain name (www.foobar.com) is a human-readable address that maps to the IP address of the server (8.8.8.8 in this case). It allows users to access the website using a memorable and easy-to-use name rather than typing the IP address directly.

+ www DNS Record: The www DNS record is a type of DNS record called a CNAME (Canonical Name) record. It is used to alias the domain name to another domain name, in this case, pointing www.foobar.com to the server's IP address.

+ Web Server (Nginx): The web server handles incoming HTTP requests from users' browsers and serves static content (HTML, CSS, JavaScript files) directly. It may also act as a reverse proxy, passing requests to the application server for dynamic content.

+ Application Server: The application server executes the application code (e.g., PHP, Python, Node.js) and generates dynamic content in response to client requests. It interacts with the database to retrieve and store data as needed.

+ Database (MySQL): The database stores and manages the website's data. It allows for efficient storage, retrieval, and manipulation of structured data, such as user accounts, posts, or product information.

+ Communication with User's Computer: The server communicates with the user's computer over the internet using the HTTP protocol. When a user types www.foobar.com into their browser, the browser sends an HTTP request to the server, which responds with the requested web page.

## Issues

+ Single Point of Failure (SPOF): Since all components are hosted on a single server, any failure of that server would result in the entire website becoming inaccessible.

+ Downtime During Maintenance: Deploying new code or performing maintenance on the web server would require restarting the server, causing downtime and interrupting service for users.

+ Limited Scalability: With only one server, the infrastructure cannot easily scale to handle a large volume of incoming traffic. As traffic increases, the server may become overloaded, leading to poor performance or downtime.

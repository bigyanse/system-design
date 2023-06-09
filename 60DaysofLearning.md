# 60DaysOfLearning

### Day01

- Software Architecture and Different Tiers of Applications
    - [Insights Into Software Architecture](https://blog.bigyandahal.com/insights-into-software-architecture)

### Day02

- Need of Different Tiers of Applications
    - Single Responsibility
    - Separation of Concerns
- Layers vs Tiers
    - Layers(Code Level Separation)
    - Tiers(Physical Separation)
- Web Architecture
    - Components
        - Database
        - Message Queue
        - Cache
        - User Interface
        - Others that form an online service
- Client-Server Architecture
    - Request-Response Model
- Peer-to-Peer Architecture

### Day03

- Types of Client
    - Thin Client
        - Client has access to only UI interface(no business logic) and for every action a request to the backend server needs to be sent
    - Thick Client (Fat Client)
        - Client has access to UI interface and some or all parts of business logic
        - Online Games, Utility Apps
- Server
    - Receive requests and send responses
    - Each service online needs server to run
    - Servers running web applications are called application server
- Types of Server
    - Application Server
    - Proxy Server
    - Mail Server
    - File Server
    - Virtual Server
    - All components of web applications need server to run
- Server side rendering
    - Interface is rendered in the backend and sent to the client

### Day04

- Communication Between Client and Server
    - Request-Response Model: Client sends request, server responds with the data
    - HTTP Protocol:
        - Entire communication happens over the HTTP protocol
        - Stateless request-response protocol
        - REST(Representational State Transfer)
            - API(software) architectural style
            - Web services using REST: RESTful web services
        - REST API
            - API adhering to REST architectural constraints
            - HTTP protocol
            - REST allows caching the response
            - Stateless process, every connection must have the complete data to make it successful like auth data
            - Backend and frontend are decoupled: Different frontend can be used for a single backend like for web, ios, android applications
            - Before REST, web applications were tightly coupled
            - Acts as a gateway to the system, handles everything and provides access to the resources

### Day05

- Modes of data transfer between client and server
    - HTTP Pull
        - Client sends request and server responds with data
        - If there is no updated data in the server, it would keep sending requests, causing waste of resources(bandwidth)
    - HTTP Push
        - Client requests for first time and server keeps pushing updates to the client
        - Also called callback
        - Eg: User Notifications
        - Technologies for HTTP Push: AJAX Long Polling, Web Sockets, Server-side events, HTML5 Event Source, Message Queues, Streaming over HTTP
    - HTTP Pull - Polling with AJAX
        - AJAX: Asynchronous JavaScript And XML
        - XMLHttpRequest object is used for sending requests to the server which is built-in the browser
        - Continuously requesting information from the server at regular intervals is called Polling
    - TTL(Time To Live)
        - There is TTL for every request
        - If client does not receive response within TTL, browser kills the connection and client has to resend the request
        - Open connections consume resources and there is a limit to it
        - If only new connections are introduced then server will run out of memory, so to solve this we have TTL
    - Persistent Connections
        - Enables HTTP Push-based communication
        - Browser kills open connections every X seconds so, we have Heartbeat Interceptors
        - Heartbeat Interceptors: Blank request responses between client and server to prevent killing the connection
        - Resource intensive

### Day06

- HTTP Push-Based Technologies
    - Websockets
        - Runs over TCP not HTTP
        - Persistent Bidirectional Low Latency Data Flow between client and server
        - Messaging, Chat Applications, Real-time social streams, browser based massive multiplayer games
    - AJAX Long Polling
        - Lies in-between AJAX and Websockets
        - Server holds the response until it finds an update to be sent to the client
        - Connection stays open a bit longer than polling
        - Smaller number of requests than regular polling
        - Used in simple asynchronous data fetch use cases when we don't want to poll server every now and then
    - HTML5 Event Source API And Server Side Events
        - Server automatically pushes the data to the client whenever there is an update available
        - Incoming messages from server are treated as events
        - Clients need to establish the initial connection with initial request
        - In the User Interface(UI), HTML5 Event Source API is used
        - Eg: Real time feed (in Twitter), displaying stock quotes, real-time notifications
    - Streaming Over HTTP
        - Ideal for streaming large data over HTTP
        - Large data is broken down into smaller chunks
        - Used for streaming multimedia contents like images, videos
        - Partially downloaded videos(chunks of the full video) can be played while being downloaded
        - Client and server agrees on some streaming settings to help figure out when stream begins and ends over HTTP request-response model
        - Possible with HTML5 and JavaScript Stream API

### Day07

- Client-Side Rendering
    - The response from the server is rendered on the window by the client
    - Browser has several components to render the response to the window
        - Browser Engine
        - Rendering Engine
        - JavaScript Interpreter
        - Networking and UI Backend
        - Data Storage, etc
    - Rendering Engine constructs the DOM tree, renders and paints the construction
- Server-Side Rendering
    - The response from the server directly generates HTML page and sends it to the client
    - Faster rendering of the UI
    - Faster loading
    - Less rendering and assembling time for the UI
    - More bandwidth
    - Not so smooth user experience
    - SEO Friendly

### Day08

- Scalability
    - Ability of the application to  handle and withstand increased worklaoad without sacrificing the latency
    - Eg: it should take x second to respond to a user request and the same for million concurrent requests
    - Backend infrastructure should not crash on million concurrent requests and should scale well when subjected to heavy traffic load and should maintain the latency of the sytem
- Latency
    - Amount of time a system takes to respond to a user request
    - No matter how much traffic load is, the latency should not build up
    - If latency is same for all amount of requests, the application can said to be scaled well
    - Types
        - Network latency: time to send a data packet from point A to B, using CDN can reduce network latency
        - Application latency: time to process user request, running stress and load test to figure out bottlenecks and remove it
    - Latency determines if the visitor to a website engages or bounces off to another website
    - We should aim for zero latency even if it is not practically possible
    - MMO games, algorithmic trading services, fintech companies, needs low latency else there will be consequences like bad user experience, or losses
    - Huawei and Hibernia Atlantic in 2011 layed fibre optic link across Atlantic Ocean between London and New York to save traders 6 milliseconds of latency for $300M approx
- Types of Scaling
    - Vertical Scaling
        - Scaling up
        - Adding more power to the server
        - Simple to scale; It does not require code refactoring and complex configurations
        - It requires pre-planning and stipulated time to pull off
        - Availability risk
        - Eg: RAM upgrade from 16G to 32G
    - Horizontal Scaling
        - Scaling out
        - There is a limit to vertical scaling, so horizontal scaling
        - Adding more hardware to the existing hardware resource pool
        - Provides ability to dynamically scale in real-time as the traffic increases or decreases over time
        - Application needs to be stateless because if one server gets down all data is lost
        - Persistent memory like a key-value pair
        - That is why functional programming got popular with distributed systems
- Cloud Elasticity
    - Ability to scale up or down dynamically, only pay for the resources required and used
    - Can add more server nodes if heavy traffic and remove when there is not much
    - High Availability: if some server gets crashed, other stays online

### Day09

- Primary Bottlenecks That Hurt Scalability
    - Databases
        - If the application is scalable and highly available but if the database is single monolith, then the application will still have latency and low response time
        - Database also needs to scale well
        - Can be done with database partitioning, sharding, use multiple database servers
    - Application Architecture
        - Common mistake is not using asynchronous processes and modules
        - Sending confirmation email, notifications to the user must be done asynchronously
        - Such tasks should be forwarded to messageing server rather than doing it on the server and synchronously
    - Not using caching wisely
    - Inefficient configurations and setup of load balancers
    - Adding business logic to the database: moving from one database to another makes it inefficient
    - Not picking the right database: use relational if transactions and consistency, if need horizontal scaling use non relational
    - Bottlenecks at the code level
        - Unnecessary loop, too many nested loops
        - tightly coupled code
        - not paying attention to Big-O complexity
- Improve Scalability
    - Improving performance
        - Application scalablity is directly proportional to its performance
        - Profiling
            - Dynamic analysis of the code to measure the space and time complexity, to figure out issues like concurrency errors, memory errors
            - Profile each aspect of the application, find the bottlenecks and fix it
        - Cachine
        - CDN
        - Data Compression
        - Avoid unnecessary client-server requests
    - Testing scalability of the application
        - Testing can be done on hardware or software level
        - Different parameters such as CPU usage, network bandwidth consumption, throughput, no of requests processed within a stipulated time, latency, memory usage of the program, end user experience when system is under heavy load, are taken into account
        - Simulated traffic can be routed to the sustem to study how the ssystem will behave under heavy load and plan for contingencies
        - JMeter is used to run concurrent user test
        - Sports website should prepare for sports event day, ecommerce for festival season,etc
        - Cadvisor, Prometheus, Grafana are use to track the system via web based dashboards
        - Pre-production monitoring tools

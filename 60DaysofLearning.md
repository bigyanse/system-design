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

- 

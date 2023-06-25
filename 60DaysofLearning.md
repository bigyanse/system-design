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

### Day10

- High Availabiity
    - Ability of the system to stay online despite failures at the infrastructure level
    - Mission critical systems like aircraft systems, spacecrafts, mining machines, hospital servers, finance stock market systems rely on high availability so do our lives
    - Highly available systems are fault-tolerant and redundant
- Reasons for System Failures
    - Software Crashes
    - Hardware Failures
    - Human Errors
    - Planned Downtime: Updates, Maintenance operations, Software Patches, Hardware Upgrades
- Fault Tolerance
    - Ability of the system to stay up depite taking hits and one of the way to achieve high availability
    - At application HA can be achieved by architecturally breaking into loosely coupled smaller services called microservices
    - Benefits of microservices
        - Easier management and development
        - Ease of adding new features and maintenance
        - High availability
- Redundancy
    - Duplicating components or instances to keep them on standby to take over in case the active ones go down
    - Active Passive HA mode: active sets of nodes are replaced by passive nodes on standby in case of failures
    - Getting rid of single point of failure
        - Distributed systems over Monolithic architecture
        - Getting rid of Bottlnecks in application level
    - System should be monitored in real-time to detect single point of failures

### Day11

- Replication
    - Having no of similar nodes running the workload together so that if few goes doqwn, there are remaining nodes bear the load of the service (like load balancing)
    - Also known as active-active high availability mode, all components are active all the time
    - Geographical Distribution Of Workload
- High Availability Clustering
    - Also known as the Fail-over cluster
    - Nodes in the cluster are connected by a private network called Heartbeat Network, that monitors the health and status of each node in the cluster
    - Single state is maintained across all the nodes with the help of a shared distributed memory and a distributed co-ordination service like the Zookeeper
    - To ensure the availability, HA clusters use several techniques such Disk mirroring/RAID Redundant Array of Independent Disks, redundant network connections, redundant electrical power, etcin multiple geographical zone
    - The network connections are made redundant so if the primary network goes down, the backup network takes over
    - Multiple HA clusters run together in one geographical zone ensuring minimum downtime and continual service
- Monolithic Architecture
    - Self contained, single-tiered software application that contains the entire application code in a single codebase
    - Simple to build, test, deploy in comparison to microservice architecture
    - Moving from monolithic to microservice has its own cost, so if there is a plan to scale in the future, loosely coupled stateless microservices architecture should be used right from the start, as rewriting can be costly
    - Pros
        - Simplicity
    - Cons
        - Continuous Deployment
        - Regression Testing
        - Single Points of Failure
        - Scalability Issues
        - Cannot Leverage Heterogeneous Technologies
        - Not Cloud Ready, Hold State
    - Only choose monolithic architecture if requirements are simple
    - Can scale out to a distributed microservices architecture if the requirements change, or is the need of scaling

### Day12

- Microservice Architecture
    - Different features, tasks are split into separate respective modules/codebases which work in conjunction with each other forming a large service as a whole
    - Follows Single Responsibility and Separation of Concerns
    - Easy maintenance, feature development, testing and deployment
    - Different modules can be assigned to different teams as they are separated by their varying functions
    - Designed to scale
    - Pros
        - No Single Points of Failure
        - Leaverages the heterogeneous technologies
        - Independent and continuous deployments
    - Cons
        - Complexities in Management
        - No strongn consistency
- Three approaches that can be followed
    - Picking a monolithic architecture
    - Picking a microservice architecture
    - Starting with a monolithic architecture and then later scale out to a microservice architecture

### Day13

- Database
    - Component required to persist data
    - Types of data
        - Structured
            - Having certain structure, stored in normalized fashion in the database
            - No need for data preparation logic, direct interaction with data
            - Managed by SQL
        - Unstructured
            - No definite structure
            - Hetergeneous data comprising text, image, video, multimedia, pdf, blob, documents, etc
            - Data often in data analytics from IoT devices, social networks, web portals, etc
            - Need data preparation logic before interacting with it
       - Semi-structured
            - Mix of structured and unstructured data
            - Often stored in XML or JSON formats User state data
            - Information of all the activity which the user performs on the website
            - Improves user browsing experience and the conversion rate for the business

### Day14

- Relational Database
    - Database saves data containing relationships
    - 1-1, 1-M, M-M, M-1, here M=many
    - SQL is used
    - Relationships
    - ACID Transactions
        - Atomicity: Either transaction occurs fully or not at all
        - Consistency: Ram sends 10 to Shyam, Ram account negates 10, Shyam's adds 10
        - Integrity: Permanent changes
        - Durability: Can be retained for longer period of time
    - Pros
        - ACID transactions
        - Large community
        - Storing relationships
    - Popular databases
        - MySQL
        - PostgreSQL
        - MS SQL
        - MariaDB
        - Google Cloud SQL
        - Oracle SQL
        - Amazon Aurora

### Day15

- NoSQL Database
    - No SQL, built for high frequency read and writes
    - Why choose NoSQL database over relational database?
        - Scalability
        - Clustering
    - Less consistent and sacrifice ACID transactions
    - Built to run clusters in a distributed environment
    - Pros
        - Gentle learning curve
        - Schemaless
    - Cons
        - Inconsistency
        - No support for ACID transactions
        - Transactions in distributed systems come with terms and conditions applied
    - Eg: MongoDB, Redis, Neo4j, Cassandra
    - When to pick NoSQL database?
        - Handling a large number of read write operations
        - Flexibility with data modeling
        - Eventual consistency over strong consistency
        - Running data analytics
    - A well designed SQL will always be more performant than a not so well-designed NoSQL store
    - Leveraging the power of multiple databases is called polyglot persistence

### Day16

- Polyglot Persistence
    - Polyglot persistence means using several different persistence technology to fulfill different persistence requirements in an application
    - Let's consider the use cases for a social network like Facebook
        - Relational Database
            - To store relationships like persisting friends of a user, friends of friends, all preferences of them, etc
        - Key Value Store
            - For low latency of all the frequently accessed data, we implement cache like key-value store like redis or memcache
        - Wide Column Database
            - To understand user behaviour, we need to setup an analytics system to run analytics on the data generated by the users, which can be done in wide-column database like Cassandra or HBase
        - ACID Transactions and Consistency
            - Ads for business need a payment system, we need a relational database that implements ACID transactions and ensure strong consistency
        - Graph Database
            - To enhance user experience we would implement a recommendation system for which Graph database is the best fit
        - Document Oriented Store
            - To implement search, we can use document oriented datastore like ElasticSearch where all search-related data can be persisted
    - Since it is more complex to monitor and manage different technologies together, we use something simpler called multi-model databases
- Multi-Model Databases
    - Multi-model databases are those that have the ability to use different data models in a single database system
    - Avert the need of managing multiple persistence technologies in a single service, reduce complexity by notches
    - Arango DB, Cosmos DB, Orient DB, Couchbase

### Day17

- Eventual Consistency
    - Model which enables the data store to be highly available, also known as optimistic replication and is very important in distributed systems
    - Datastores for sites are spread across the world whcih is used for persisting data, so there is not single point of failure. Let's think of a like service is used by people across the globe. The count of likes in a post does not change at the same time. People at America and Japan may see different like counts at the same time. But eventually, the like counts get even after being updated at all the datastores as the data needs time to travel from one datastore to another, which is called eventual consistency
    - It makes the system highly available
    - It is suitable for use cases where the accuracy of valaues does not matter much
    - Eg: Live stream of videos user watching count
    - Not suitable for live data for banking, stock markets, we need strong consistency
- Strong Consistency
    - Data has to be strongly consistent at all times
    - Locking down nodes while data is being updated
    - Lifting locks when the nodes reach consensus
    - Stock market applications
    - Queuing the requests is a way to make a system consistent
    - CAP theorem is a key to implement consistency models
    - Hits the capability of the system to be highly available
    - Needs to be ACID compliant
- CAP theorem
    - Consistency, Availablity, Partition Tolerance(Fault Tolerance)
    - CAP theorem states that in case of a network failure, when a few nodes of the system are down, we have to make a choice between availability and consistency

### Day18

- Document-Oriented Database
    - Main types of NoSQL databases
    - Store data in document-oriented model in independent documents
    - Semi-structured and stored in JSON like format
    - MongoDB, CouchDB, Google Cloud Datastore, Amazon Document DB
    - Real-time feeds, live sport apps, writing product catalogues, inverntory management, storing user comments, web-based multiplayer games
    - Provides horizontal scalability

### Day19

- Graph Database
    - Part of NoSQL database family, which store data in node/vertices and edges in the form of relationships
    - Each node in a graph database represents an entity, edge represents the relationship between the entities
    - Features
        - Better visualization of data and their relationships
        - Low-latency, faster as not calculated at query time (not like joins in SQL)
    - Eg used in: Google Maps
    - When to use Graph Database?
        - Social, knowledge, network graph
        - Writing AI-based apps, recommendation engines, fraud analysis app, storeing genetic data
    - Eg: Neo4J
- Key-value Database
    - Part of NoSQL family, which uses simple key-value method to store and quickly fetch the data with minimum latency
    - Features
        - Low latency
        - Unique identifier with value of any complex type
        - O(1) time complexity
    - Eg: Redis, Hazelcast, Riak, Voldemort, Memcache
    - When to use Key-value Database?
        - Caching
        - Persisting user state
        - Persisting user sessions
        - Managing real-time data
        - Implementing queues
        - Creating leaderboards in online games and web apps
        - Implementing a pub-sub system

### Day20

- Time Series Database
    - Databases that are optimized for tracking and persisting time series data
    - Time series data are data containing data points associated with the occurrence of an event with respect to time, that are tracked, monitored and then finally aggregated based on certain business logic
    - It is generally ingested from IoT devices, self-driving vehicles, industry sensors, social networks, stock market financial data
    - Use cases
        - Track the behaviour of the system, analysis and monitoring
        - Helps to study patterns, anomalies and how things change over time
        - Running analytics, deducting conclusions, and making future business decisions looking at the results of the analytics
        - Managing real-time data continually over a long period of time
        - Anonymous trading platform which deals with changing stock prices in real time
    - Eg: InfluxDB, TimescaleDB, Prometheus
- Wide-column Database
    - Part of NoSQL family, used to handle massive amounts of data, technically called the Big Data
    - Perfect for analytical use cases as they have a high performance and a scalable architecture
    - Store data in a record with a dynamic number of columns, can store billions of columns
    - Eg: Cassandra, HBase, Google BigTable, ScyllaDB
    - Use cases
        - Need to grapple with Big Data, to ingest it or to run analytics on it
        - To manage Big Data ensuring scalability, performance and high availability

### Day21

- Caching
    - Copying frequently accessed data from disk to RAM
    - For better response time, low latency and high throughput
    - To keep users from bouncing off to other websites
    - Dynamic data is cached with an expiry time or TTL(Time To Live), after TTL ends data is purged from the cache and newly updated data is stored in it, it is known as cache invalidation
    - Static files are cached in client side, browser, local memory, also on CDNs

### Day22

- Where to use caching?
    - Database caching, to alleviate the stress on the databased
    - Cache frequently accessed data from the database to cut down load on the database
    - Caching can be used in the client browser, databases, REST API, heavy compute processing
    - Cache can also maintain high availability if database goes down
    - Cross module communication in a microservices architecture by saving shared data which is commonly accessed by all the services, backbone for microservice communication
    - Key-value databases are mainly used for caching, used in in-memory data stream processing and running analytics
- Caching Strategies
    - Cache Aside
        - Most common caching strategy, cache works along with the database trying to reduce the hits on it as much as possible
        - Data is lazy-loaded in the cache, first of all data is searched through the cache when user first request for particular data, if it is not present in the cache then it is loaded from the database, cache is updated and provided to the user
        - Best for read-heavy workloads, not so frequently data updating system
        - Data is directly written to the database, so cache have TTL because the cache could get inconsistent
    - Read-through cache
        - Similar to cache aside strategy except that the cache stays consistent with the database
        - Cache is lazy-loaded, i.e. only when user requests it, first time is cache miss, but can be preloaded
    - Write-through cache
        - Each and every information to the database goes through cache, first cache is updated and then the database
        - High consistency, added latency due to overheads
        - Useful for optimized performance
    - Write-back cache
        - Data is directly written to cache instead of database, and after some time, it is written to the database
        - Useful for heavy write application systems
        - Risky if the cache fails before the databasee
        - Used with other caching strategies to make most out of it
        - Optimizes costs significantly

### Day23

- Message Queue
    - Queue which routes messages from the source to the destination, sender to receiver
    - It follows FIFO policy as queue
    - Messsages may have priority, making them a priority queue
    - Feature
        - Facilitates asynchronous behavior, which allows modules to communicate with each other in the background without hindering their primary tasks
        - Facilitates cross-module communication which is a key in service-oriented or microservices architecture, allows communication in heterogeneous environment
        - Provides temporary storage for messages until they are processed and consumed by the consumer
    - Use cases
        - Email sending
        - Confirmation email in a registering process of website
        - Running batch jobs, eg: to update stock prices at regular interval

### Day24

- Publish-Subscribe Model
    - Model where multiple consumers receive the same message sent from a single or multiple producers, many to one relationship
    - Eg: real world  newspaper service, youtube subscription service, etc
    - Exchanges
        - To implement pub-sub pattern message queues have exchanges which further push the messages to the queues based on the exchange type and the rules which are set
        - Exchanges are like telephone exchanges which route messages from sender to the receiver through the infrastructure based on a certain logic
        - Different types of exchanges are available in message queues, some of them are direct, topic, headers, fanout
        - Relationship between exchange and the queue is known as binding
- Point-to-Point Model
    - Model where message from the producer is consumed by only one consumer, One to one relationship
    - According to the requirements, we can setup multiple combinations in this model like adding multiple producers and consumers to the queue, but only one consumer will consume the message sent by producer
    - Not broadcast but entity to entity communication
- Messaging protocols
    - AMQP(Advanced Message Queue Protocol)
    - STOMP(Simple or Streaming Text Oriented Message Protocol)
    - Technologies
        - Apache Kafka
        - ActiveMQ
        - RabbitMQ

### Day25

- Notification System using Message Queue
    - Pull Based Approach: regular polling to the server and database
    - Push Based Approach: pushing updates from message queue to user
- We can use Message Queues for handling of concurrent requests
- Data-Driven Systems
    - Data Stream Processing: IoT devices in industry sensors, smart cities, electronic devices, wearable healthcare body sensors
    - Massive amount of streaming data needs to be gathered for meaningful information by the backend systems
    - So we need reliable system with high availablity, low latency for efficient data-driven systems

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
    - Ability of the application to handle and withstand increased worklaoad without sacrificing the latency
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
        - Such tasks should be forwarded to messaging server rather than doing it on the server and synchronously
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
        - Simulated traffic can be routed to the system to study how the system will behave under heavy load and plan for contingencies
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

### Day26

- Data Ingestion
    - The process of collecting data streaming-in from several different sources and making ready to be processed by the system
    - In data processing system, the data is ingested from IoT devices and other sources, into the system to be analysed
    - Data is routed to different components/layers through data pipelines, algorithms are run on it and is eventually archived
- Layers of Data Processing Setup
    - Data collection layer
    - Data query layer
    - Data processing layer
    - Data visualization layer
    - Data storage layer
    - Data security layer
- Data Standardization
    - Data is streamed from different sources which may come in different sizes, speed, and every stream of data has different semantics
    - In order for the data to be fit for processing, it has to be collected and converted into a standardized format to avoid any future processing issues, this process occurs in the Data collection and preparation layer
- Data Processing
    - After data is transformed into a standard format it is routed to the Data processing layer where it further processed based on the business requirements, generally classified into different flows, routed to different destinations
- Data Analysis
    - After being routed, analytics is run on the data which includes execution of different analytics model such as predictive modeling, statistical analysis, text analysis, etc, which all occur in Data analytics layer
- Data Visualization
    - Once the analytics are run and we have valuable intel from it, it is routed to the Data visualization layer to be presented before the stakeholders in web-based dashboard
    - Eg: Kibana
- Data Storage and Security
    - Moving data is highly vulnerable to security breaches
    - Data security layer ensures the secure movement of data
    - Data storage layer ensures that the data persists for long time without being lost

### Day27

- Ways to ingest data
    - Real-time
        - Preferred in systems reading medical data like a heartbeat, blood pressure via wearable IoT sensors, financial data like stock market events, where the time is of critical importance
    - Batches
        - Systems that read trends over time, we can always ingest data in batches, estimating the popularity of a sport in a region over a period of time
- Challenges with Data Ingestion
    - Slow Process
        - Conversion of data is a slow and tedious process which takes a lot of computing resources and time
        - Flowing data has to be staged at several stages in the pipeline and then moved ahead
        - At each and every stage data has to be authenticated and verified to meet the organization's security standards
        - With traditional data cleansing processes, it takes weeks if not months to get useful information on hand
        - Traditional data ingestion systems like ETL are not that effective anymore, but modern data processing is evolving
        - Real-time data processing is not accurate and holistic than Batches, which is more accurate and holistic as it accounts the entire dataset
        - Lambda and Kappa architectures of data processing
    - Complex and Expensive
        - Entire data flow process is resource-intensive
        - Linkedin uses Gobblin for data ingestion
    - Moving data around is risky
- Use Cases of Data Ingestion
    - Moving Big Data into Hadoop (Data processing framework) for analysis and stuff
    - Streaming Data from Databases to Elasticsearch Server
        - Elastic search is an open-source, defacto search framework in the industry for implementing search in web applicaitons due to its advanced features and open-source, enabling business to write their own custom solutions
    - Log Processing: Ingest logs to central server to run analytics on it with the help of solutions like ELK Elastic LogStash Kibana stack, etc
    - Stream Processing Engines for Real-Time Events
        - Message queues like Kafka, Stream computation frameworks like Apache Storm, Apache Nifi, Apache Spark, Samza, Kinesis, etc are used to implement the real-time large-scale data processing features in online applications

### Day28

- Data Pipelining
    - Data pipelines are the core component of a data processing infrastructure, which facilitate the efficient flow of data from one point to another and also enable developers to apply filters on the data sreaming-in in real time
    - Today's enterprise is data-driver so data pipelines play important tole in implmeneting scalable analytics systems
    - Features of Data Pipelines
        - Ensures smooth flow of data
        - Enables the business to apply filters and business logic on streaming data
        - Avert any bottlenecks and redundancy in the data flow
        - Facilitate parallel processing of data
        - Avoid data being corrupted
    - Pipelines work on a set of rules predefined by the engineering teams and the data is routed accordingly without any manual intervention
    - Data extraction, transformation, combination, validation, converging of data from multiple streams into one
    - Facilitate parallel processing of data via managing multiple streams
    - ETL is traditionally used to handle all the movement of data but it does not support real-time streaming data handling
- ETL (Extract Transform Load)
    - Extract means fetching data from single or multiple sources
    - Transform means transforming the extracted heterogeneous data into a standardized format based on the rules set by the business
    - Load means moving the tranformed data to a data warehouse or another data storage location for further processing of data
    - ETL flow is the same as data ingestion flow, movement of data is done  in batches instead of streaming it, through data pipelines in real-time
    - Both real-time and batch data processing are leveraged based on th eproject requirements
    - All data processing tools have one thing in common, they facilitate processing of data in a cluster, in a distributed environment via data pipelines

### Day29

- Distributed Data Processing
    - Diverging large amounts of data to several different nodes, running in a cluster for parallel processing
    - All the nodes execute the task allotted parallely, working in conjunction with each other co-ordinated by a node co-ordinator like Apache Zookeeper helps achieve scalability and high availability, data redundancy and replication
    - Less amount of time for processing opposed to centralized data processing system
- Distributed Data Processing Technologies
    - MapReduce - Apache Hadoop
        - MapReduce is a programming model written for managing distributed data processing across several different machines in a cluster, distributing tasks to several machines, running work in parallel, managing all the communication and data transfer within different parts of the system
        - Map part of the model involves sorting the data based on a parameter and the Reduce part involves summarizing the sorted data
        - Apache Hadoop is the example of MapReduce programming model, used by Twitter for running analytics and Facebook for storing big data
    - Apache Spark
        - Open-source cluster computing framework, which provides high performance for both batch and real-time in-stream processing, and can work with diverse data sources and facilitates parallel executing of work in a cluster
        - Has cluster manager and distributed data storage
        - Facilitates communication between different nodes running together in a cluster whereas the distributed storage facilitates storage of big data
        - Seamlessly integrates with the distributed data stores like Cassandra, HDFS, MapReduce File System, Amazon S3, etc
    - Apache Storm
        - Distributed stream processing framework, primarily used for processing massive amounts of streaming data, which has several use cases such as real-time analytics, machine learning, distributed remote procedure calls, etc
    - Apache Kafka
        - Open-source distributed stream processing and messaging platform, written using Java and Scala and was developed by LinkedIn
        - Storage layer of Kafka involves a distributed scalable pub/sub message queue, which helps read and write streams of data like a messaging system
        - Used in the industry to develop real-time features such as notification platforms, messaging streams of massive amounts of data, monitoring website activity and metrics, messaging, log aggregation
        - Preferred for batch processing of data whereas Spark, Kafka and Storm are preferred for processing real-time streaming data

### Day30

- Lambda Architecture
    - Distributed Data Processing architecture that leverages both the batch and real-time streaming data processing approaches to tackle the latency issues arising out of the batch processing approach, joins the results from both the approaches before presenting it to the end user
    - Batch processing takes considerable time but have high accuracy and comprehensive result
    - Real-time streaming data processing provides quick insights, but the accuracy is low and results are not comprehensive
    - Layers of the Lambda Architecture
        - Three layers
            - Batch Layer: deals with results acquired via batch processing the data
            - Speed Layer: gets data from the real-time streaming data processing
            - Serving Layer: combines the results obtained from both the Batch and the Speed layers
- Kappa Architecture
    - Data flows through a single data streaming pipeline as opposed to the Lambda Architecture which has different data streaming layers that converge into one
    - Reduces the complexity of managing separate layers for processing data
    - Layers of Kappa Architecture
        - Speed: streaming processing layer
        - Serving: final layer
    - Not an alternative for lambda, both have their own use cases
- Kappa is preferred if the batch and the streaming analytics results are fairly identical in a system, Lambda is preferred if they are not
- Distributed System does not promise Strong Consistency of data

### Day31

- Events
    - Two kinds of processes in applications:
        - CPU intensive
        - I/O intensive:
            - in context of web applications I/O means events
            - tweet, click of a button, HTTP request, ingested messages, change in value of a variable, etc are events
            - Request-response events between client and server, stream of events, etc
- Event-Driven Archietecture (EDA)
    - Blocking Operations: the flow of execution is blocked waiting for a process to complete, until the process is completed, it cannot move on
    - Non-Blocking Operations:
        - Also known as the reactive or Event-Driven Architecture (EDA)
        - the flow of execution is not blocked, even though the function may return a response or an error, it will be sequenced to run next
        - facilitates the I/O intensive operations(network, disk, hardware based operations and communications)
        - capable of handling a big number of concurrent connections with minimal resource consumption
        - built to run on a cluster, handle large scale concurrent scenarios, tackle problems
        - enable us to write code without worrying about multi-threads, thread lock, out of memory issues due to high I/O, etc
    - Technologies for implementing EDA
        - Spring Reactor, NodeJS, Play, Akka.io

### Day32

- Web Hooks
    - Web Hooks enables communication between two services without a middleware
    - Web Hooks are like call-backs, when some event occurs, other services are notified that are interested in that events
    - Web Hooks are used in scenario when triggering API endpoints are costly and redundant, instead when some event happens instead it notifies to the interested parties
    - Working
        - Consumers register an HTTP endpoint with the service with a unique API key, like a phone number, when an event occurs, it calls on that endpoint once
        - Whenever a new information is available on the backend, the server fires an HTTP event to all the registered endpoints of the consumers, notifying them of the new update
        - Browser notifications are a good example of Web Hooks. Insted of visiting the websites every now and then for new info, the websites notify us when they publish new content
- Shared Nothing Architecture
    - When several modules work in conjunction with each other they often share RAM also known as shared memory, they share disk(i.e database), and they share nothing, the architecture of the system where the modules or the services sharing nothing is called the Shared Nothing Architecture
    - Shared Nothing means eliminating all single points of failure, every modules has its own memory, disk so even if several modules go down, other will stay online, helping scalability and performance

### Day33

- Hexagonal Architecture
    - Components
        - Ports
        - Adapters
        - Domain
    - Focused on making components of the application: independent, loosely coupled and easy to test
    - The application should be designed in a way such that it can be tested by humans, automated tests, with mock databases, mock middleware, with and without a UI, without making any changes or adjustments to the code
    - Architectural pattern
        - Domain: Business logic
        - Ports: API
        - Adapters: Interface
    - Hexagonal shape doesn't have anything to do with the pattern logic, ports and adapters are named after the work they do
    - Can be said as evolved layered architecture, difference being that in layered approach business logic gets scattered all over the layers making testing, refactoring and pluggability of new entities difficult, just like stored procedures in the databases and the business logic coupled with the UI in JSP
    - JSP and stored procedures have UI, persistence layer separate but business logic is tightly coupled with these layers
    - Hexagonal pattern holds business logic and outside layer, the Ports and Adapaters which involve the databases, message queues, APIs and stuff

### Day34

- Peer-to-Peer Architecture (P2P)
    - A network in which computers(nodes) can communicate with each other without the need of a central server
    - P2P architecture is the base of blockchain tech, torrent, etc
    - No single point of failure due no absence of central server
    - All node acts as a seeder and a leecher at the same time, so even if some of the nodes go down, the network and the communication is still up
    - A seeder is a node which hosts the data on its system and provides bandwidth to upload the data to the network, a leecher is a node which downloads the data from the network
- Downsides of Centralized Systems 
    - Central server has access to all of the information of the users, so communication and security issues is prevalent, data may be breached, sold, or data may get lost due to disasters, or the server plans to go down along with all your hardships on the platform for creating that data(assume facebook page with following of 1M+)
- Decentralized Architecture
    - P2P network is based on decentralized architecture, in which nobody has control over a user's data, nobody can delete the data, everyone has equal rights
    - Even during disasters, P2P is useful in case all the infrastructure goes down
- Advantages of P2P Network
    - P2P file sharing with no limits
    - Torrenting
    - Communicating
- Working of P2P
    - Nodes taking part equally acting as both client and server in the network
    - Data is exchanged over TCP/IP like that over the HTTP protocol in a client-server model
    - P2P design has an overlay network over TCP/IP which enables the users to connect directly which takes care all of the complexities and heavy lifting
    - Nodes/Peers are indexed and discoverable in this overlay network
    - Files are transferred between the nodes by being divided into chunks of equal size in a non-sequential order
    - Segmented P2P file transfer: a node download a file in chunks, making it available for downloading for other nodes in the network
- Types of P2P Networks
    - Unstructured
        - Nodes/peers keep connecting with each other randomly, so there is no structure, they simply connect and grow the network
        - No indexing of the nodes, to search through data, we have to scan through each and every node of the network, O(n) complexity, n is the nodes in the network, which is very resource-intensive
        - Protocols of the unstructured network: Gossip, Kazaa, Gnutella
    - Structured
        - Holds proper indexing of the nodes or the topology, making it faster and easier to search for specific data
        - Implements Distributed Hash Table to index the nodes, just like index of a book
        - Eg: BitTorrent
    - Hybrid
        - Majority of blockchain startups have a hybrid model, cherry-picking the good stuff from distributed architecture and models like P2P, client-server model, etc
        - Client-server model have control over the data and the network, P2P network offer more availability, less storage, less bandwidth, more scalable as everything is distributed and shared
        - No third party intervention, data is secure
        - Eg: Cryptocurrency
        - P2P applications: Tradepal, P2P digital cryptocurrencies like Bitcoin, Peercoin, GitTorrent(decentralized github which used bittorrent and bitcoin), Twister(decentralized microblogging service, which uses WebTorrent for media attachments), Diaspora(decentralized social network implementing federated architecture)

### Day35

- Decentralized Social Network
    - Decentralized social networks have servers spread out across the globe, hosted by normal users, nobody has control over the network
    - Eg: Minds, Mostodon, Diaspora, Freiendica, Sola, etc
- Features of Decentralized Social Network
    - Bring Your Own Data
    - Ensuring the Safety of Our Data
    - Economic compensation to the parties involved in the network
        - People sharing their computing power to host the network get their compensation in the form of tokens or equity or whatever as per the economic policy of the network
        - Teams involved in moderating the network, developers writing new features get compensated by enabling content relevant ads on the network or by the token-based economy of the platform
    - Infrastructure Ease
        - Infrastructure cost should not be beared by a single entity since it is decentralized
        - No network downtime, no server cost worries, no data loss
        - Open-source protocols and software which can be improved by community contributions
        - Eg: ActivityPub, open-source decentralized social networking protocol which provides and API for modifying and accessing the content on the network, also for communication with other pods in the federation
- Federated Architecture
    - Extension to the decentralized architecture, it powers social networks like Mastodon, Minds, Diaspora, etc
    - Federated means a group of semi-autonomous entities exchanging information with each other, eg: looking at different states of a country which are managed by the state governments, they are partially self governing and exercise the power to keep information with each other and with a central government making a complete autonomous government
    - Federated model is under continual research, development and evolution from a technical standpoint, there are no standard rules
    - Developers, architects can have their own designs in place, as it is decentralized
- How is Social Networks implemented using Federated Architecture?
    - Federated Network has entities called servers or pods, a large number of nodes subscribe to the pods, there are several pods in the network that are linked to each other and share information with each other
    - The pods can be hosted by individuals as it is ideally archived in a decentralized network, and any new can be hosted and introduced to the network
    - If any pods break temporarily, the network is still up and nodes can still communicate with each other via the pods they are subscribed to
- Needs for Pods
    - It facilitates node discovery
    - In P2P network, node discovery is not possible, as we would have to scan through the network and try to discover, which is time-consuming and tedius task

### Day36

- Picking the Right Server-Side Technology
    - Real-time Data Interaction
        - Persistent connection between client and server, non-blocking technology on the back-end
        - Technologies: NodeJS, Python framework called Tornado, Java: Spring Reactor, Play, Akka.io
        - Uber uses NodeJS to write their core trip execution engine, using which they manage number of concurrent connections
    - P2P Web Application
        - For P2P Web App, P2P Distributed search engine or a P2P live TV radio service, similar to LiveStation by Microsoft, look into JavaScript, protocols like DAT, IPFS, FreedomJS framework to build P2P web apps that work in modern web browsers
    - CRUD-based regular application
        - For online movie booking portal, a tax filing app, etc, Use MVC frameworks like Spring MVC, Python Django, Ruby on Rails, PHP, Laravel, ASP .NET MVC
    - Simple, Small Scale Applications
        - PHP, Spring boot, Ruby on ails are ideal for simple use cases
    - CPU & Memory Intensive Applications
        - CPU, memory intensive, heavy computational task on the backend such as Big Data Processing, Parallel processing, running monitoring and analytics on large amount of data
        - Performance is critical in systems like that where it needs to handle massive amounts of data and has its cost, need low latency and memory consumption
        - C++, Rust, Java, Scala & Erlang that has high performance and safe concurrency
        - Elastic Search is an open source real-time search and analytics engine written in Java
        - Erlang is fucntional programming language with built-in support for concurrency, fault-tolerance and distribution. It facilitates the development of massive scalable systems
        - Go is developed by Google to write apps for multi-core machines and handling a large amount of data
        - Julia is a dynamically programmed language built for high performance and running computations and numerical analysis

### Day37

- Things to Remember When Picking the Tech Stack
    - Be thorough with the Requirements
    - See if what we already know fits the requirements
    - Does the tech we have picked has an active community? How is the documentation and the support?
    - Is the tech being used by big guns in production?
    - Check the license. Is it open source?
    - Availability of skilled resources on the tech

### Day38

- Case Study of Google Maps Like Service
    - A read-heavy application
    - Data Type: Spatial data
    - Databases: Spatial databases
    - Architecture: Client-server model
    - Backend Technology: Java, Go, Scala, Elixir/Erlang or Python
    - Microservice architecture: Since the system will be big, needs to be highly available, performant, low latency, and needs to scale well for high traffic spikes
    - Server Side Rendering
        - Can cache rendered image
        - Can create rendered image in advance and cache it
    - APIs
        - Direction API, Distance Matrix, Geocoding, Places, Roads, Elevation, Timezone, Custom Search API, etc
    - User Interface
        - OpenLayers
        - JavaScript
    - Real-Time Features

### Day39

- Case Study of Online Ticket Booking Application (General)
    - Database
        - Since we need ACID transactions, we go with relational databases
    - Concurrency
        - There will be surge of requests at some time so to handle that we need Message Queue using FIFO approach
        - Database Lock
            - We can also use database lock to maintain consistency and handle concurrency
            - Transaction Isolation level ensures that at a point in time only one transaction has access to resource in the database
            - Snapshot isolation
    - Caching
        - Redis, Memcache, Hazelcast
    - Backend
        - Python, Go, Scala, Java, etc
    - Notifications
        - RabbitMQ, Kafka
    - User Interface
        - Plain old HTML, CSS
        - UI Library or frameworks like React, Angular, Vue, Svelte

### Day40

- Mobile App Design
    - Today most of the services are focused towards mobile phone due to mobile phone mostly being in everyone's hand
    - Before designing mobile app if the business already has web app, we need to think before diving in as it may not be totally required and also it takes different approach than buiding/designing web app, as mobile phone has less power, resources than a computer
    - Different approach
        - Mobile Only
        - Mobile First: with major users being in mobile
        - Mobile Friendly: with major users being in desktop
    - Do we need mobile app?
        - Focus on what type of sevice is to be provided, maybe it needs mobile rather than opening web everytime for completing it
        - Do users use you service through mobile more? Study other similar business analytics
- Responsive Interface
    - Since there are different devices with different screen sizes like android, ios, desktop, TVs, etc, we need responsive interface to run across all devices which would lower development cost
- Types of Mobile Apps
    - Native App:
        - specific OS, android, ios, windows phone
        - full access to device resources
        - high performance
        - consistent interface
        - developed using native SDKs and APIs by native OS
        - Eg: Java, Kotlin, Swift, Objective C, Cocoa Touch framework
    - Hybrid App
        - Uses web technologies like HTML, CSS, JS
        - Eg: Cordova, Ionic, PhoneGap
    - Cross-platform App
        - React-native
        - Flutter
- Choosing between native and hybrid apps
    - If performance is needed go native else cross-platform hybrid should be fine
    - Or if you don't have specific needs to go native go cross-platform
    - Other factors like cost, time, also comes into play if these constraints then go cross-platform
- Progressive Web Apps(PWAs)
    - App like experience with a web application
    - Not an native app replacement
- Mobile Backend as a Service(MBaaS)
    - Cloud-based service that takes care of the backend infrastructures of our mobile app and enables us to focus on business logic and user interface
    - Features
        - User Authentication
        - Social Network Integration
        - Push-notifications
        - Real-time Database
        - caching
        - Data Storage
        - Messaging
        - Chat Integration
        - Integration of third party tools
        - Crash Reporting
    - Eg: Google Firebase, AWS Amplify, Parse
    - Pros
        - Can deploy and have mobile app running really fast
    - Cons
        - Vendor locking
    - Can use it side by side with on-premises structure or other backend infrastructure

### Day41

- Reverse Proxy (Web Server)
    - Web server that centralizes internal services and provides unified interfaces to the public
    - Requests from clients are forwarded to a server that can fulfill it before the reverse proxy returns the server's response to the client
    - Pros
        - Increased security
        - Increased scalability and flexibility
        - SSL Termination: no need to install X.509 certificates on each server
        - Compression
        - Caching
        - Serve static content directly
    - Cons
        - Increased complexity
        - Single point of failure of single reverse proxy introduces multiple reverse proxies which further adds complexity
    - Technologies: HAProxy, NGINX

### Day42

- Load Balancers
    - Distributes incoming client requests to computing resources such as application servers and databases and returns the response from the computing resource to the appropriate client
    - Effective at preventing request from going to unhealthy servers, preventing overloading resources, eliminate a single point of failure
    - Can either be implemented with hardware(expensive) or software
    - Benefits
        - SSL Termination
        - Session Persistence: issues cookies and route requests to same instance if web apps dont keep track of sessions
    - Can be effective with multiple load balancers either in active-passive or active-active mode in case of failures
    - Can route traffic based on various metrics:
        - Random
        - Least Loaded
        - Session/cookies
        - Round Robin or Weighted Round Robin
        - Layer 4
            - Focus on transport layer to decide how to distribute requests, involves source, destination ip address, ports in the header but not the contens of the packer
            - Forward network packets to and from the upstream server, performing Network Address Translation(NAT)
        - Layer 7
            - Focus on application layer to decide how to distribute requests, involves the header, message and cookies
            - Terminate network traffic, reads the message, makes a load-balancing decision, then open a connection to the selected server, for eg: it can direct video traffic to servers that host videos while directing more sensitive user billing traffic to security-hardened Servers
        - Layer 4 load balancing requires less time and computing resources than Layer 7, although performance impact can be minimal on modern commodity hardware
        - Horizontal Scaling
            - Load balancer help with horizontal scaling, improves performance and availability
            - Scaling out using commodity machines is more cost efficient and results in higher availability than scaling up a single server on more expensive hardware, called vertical scaling, easy to hire talent on commodity hardware than specialized enterprise systems
            - Cons
                - Introduces complexity
                    - Stateless servers
                    - Sessions should be stored in databases(SQL, NoSQL, Persistent Cache)
                - Downstream such as caches and databases need to handle more simultaneoous connections as upstream servers scale out
        - Cons of Load Balancer
            - Performance bottleneck if it does not have enough resources or if it is not configured properly
            - Increased complexity by single load balancer or multiple load balancers

### Day43

- Reverse Proxy vs Load Balancer
    - Load Balancer is useful when you have multiple servers, load balancers route traffic to a set of servers serving the same function
    - Reverse proxy is useful even with just one web server or application server
- NGINX Architecture
    - NGINX Process Model
        - Master Process:
            - Performs the priveleged operations such as reading configuration and binding to ports
        - Child Process
            - Shared memory is used for cache, session persistence, rate limits, session log
            - Worker processes handle HTTP and other network traffic
    - How does NGINX work?
        - Master process performs the privileged operations such as reading configuration and binding to ports and then creates a small number of child processes
        - The cache loader process runs at startup to load the disk-based cache into memory, and then exists. It is scheduled conservatively, so its resource demands are low
        - The cache manager process runs periodically and prunes entries from the ddisk caches to keep them within the configured sizes
        - The worker processes do all of the work. They handle network connections, read and write content to disk and communicate with upstream servers
        - When in auto configured worker_processes, one worker process is run per CPU core, and never leaves the CPU core due to expensive context switching process
        - When NGINX server is active, only the worker processes are busy. Each woker process handles multiple connections in a nonblocking fashion, reducing the number of context switches
        - Each worker process is single threaded and runs independently, grabbing new connections and processing them. Processes communicate using shared memory for shared cache data, session persistence data and other shared resources

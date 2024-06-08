# Source of information
The material gathered from LinkedIn from my favorites.

## ByteByteGo
https://www.linkedin.com/company/bytebytego/

### Top 5 Kafka use cases

Kafka was originally built for massive log processing. It retains messages until expiration and lets consumers pull messages at their own pace.

Let’s review the popular Kafka use cases.

Log processing and analysis
Data streaming in recommendations
System monitoring and alerting
CDC (Change data capture)
System migration
![](https://github.com/crackodeal/Learning/blob/main/ByteByteGo/images/1717774390456.gif )

### 12-Factor App

The "12 Factor App" offers a set of best practices for building modern software applications. Following these 12 principles can help developers and teams in building reliable, scalable, and manageable applications.

Here's a brief overview of each principle:

Codebase: Have one place to keep all your code, and manage it using version control like Git.

Dependencies: List all the things your app needs to work properly, and make sure they're easy to install.

Config: Keep important settings like database credentials separate from your code, so you can change them without rewriting code.

Backing Services: Use other services (like databases or payment processors) as separate components that your app connects to.

Build, Release, Run: Make a clear distinction between preparing your app, releasing it, and running it in production.

Processes: Design your app so that each part doesn't rely on a specific computer or memory. It's like making LEGO blocks that fit together.

Port Binding: Let your app be accessible through a network port, and make sure it doesn't store critical information on a single computer.

Concurrency: Make your app able to handle more work by adding more copies of the same thing, like hiring more workers for a busy restaurant.

Disposability: Your app should start quickly and shut down gracefully, like turning off a light switch instead of yanking out the power cord.

Dev/Prod Parity: Ensure that what you use for developing your app is very similar to what you use in production, to avoid surprises.

Logs: Keep a record of what happens in your app so you can understand and fix issues, like a diary for your software.

Admin Processes: Run special tasks separately from your app, like doing maintenance work in a workshop instead of on the factory floor.

![](https://github.com/crackodeal/Learning/blob/main/ByteByteGo/images/1717816789033.gif)

### high scalability, and high throughput

The diagram below is a system design cheat sheet with common solutions.

High Availability This means we need to ensure a high agreed level of uptime. We often describe the design target as “3 nines” or “4 nines”. “4 nines”, 99.99% uptime, means the service can only be down 8.64 seconds per day.
To achieve high availability, we need to design redundancy in the system. There are several ways to do this:

Hot-hot: two instances receive the same input and send the output to the downstream service. In case one side is down, the other side can immediately take over. Since both sides send output to the downstream, the downstream system needs to dedupe.

Hot-warm: two instances receive the same input and only the hot side sends the output to the downstream service. In case the hot side is down, the warm side takes over and starts to send output to the downstream service.

Single-leader cluster: one leader instance receives data from the upstream system and replicates to other replicas.

Leaderless cluster: there is no leader in this type of cluster. Any write will get replicated to other instances. As long as the number of write instances plus the number of read instances are larger than the total number of instances, we should get valid data.

High Throughput This means the service needs to handle a high number of requests given a period of time. Commonly used metrics are QPS (query per second) or TPS (transaction per second).
To achieve high throughput, we often add caches to the architecture so that the request can return without hitting slower I/O devices like databases or disks. We can also increase the number of threads for computation-intensive tasks. However, adding too many threads can deteriorate the performance. We then need to identify the bottlenecks in the system and increase its throughput. Using asynchronous processing can often effectively isolate heavy-lifting components.

High Scalability This means a system can quickly and easily extend to accommodate more volume (horizontal scalability) or more functionalities (vertical scalability). Normally we watch the response time to decide if we need to scale the system.

![](https://github.com/crackodeal/Learning/blob/main/ByteByteGo/images/1717648765296.gif )
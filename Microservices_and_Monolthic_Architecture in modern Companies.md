
                                **RESEARCH ON MONOLITHIC AND MICROSERVICES ARCHITECTURE IN MODERN COMPANIES.**

***Background Overview*****.**

Microservices architecture became dominant in software construction during the 2010s and fundamentally changed how organisations accomplished applications’ system’s design, deployment and scaling. Microservices allowed for single responsibility in which each small job has independently deployable services via APIs to be more efficient, while avoiding the tight coupling that all components had in monolithic systems.

**Reasons why Companies migrated to Microservices.**

**Monoliths have scalability bottlenecks:** Monolithic applications become increasingly difficult to scale as the company grows meaning over flooding one service module during peak traffic session like; a checkout module during peak shopping can force the entire application to be scaled rather than just the affected component leading to larger costs. 

**Deployment Velocity and Team Autonomy.** Monolith systems in large engineering teams frequently experience deployment conflicts amongst teams in which one team's release blocks another's. Microservices allows for each team to own, develop, and deploy their services independently thus reducing inter-team conflicts and frequency of deployment.

**Resilience and Fault Isolation.** In a monolith, a bug in one module can crash the entire application. Microservices contain failures within individual service boundaries. A failing recommendation engine, for instance, does not bring down the entire platform.

**Technology Flexibility.** Microservices permit polyglot programming — different services can be written in different languages and use different data stores, allowing teams to select the best tool for each specific problem.

**Cloud-Native Alignment.** The rise of cloud infrastructure (AWS, GCP, Azure) and containerisation tools (Docker, Kubernetes) made microservices operationally practical, giving organisations a strong infrastructure reason to migrate.

**Three Case Studies of Companies that migrated to Microservices and remained there.**

### **Case Study: Netflix**

Netflix began as a monolithic application until 2008, it had experienced a major database corruption incident that took down its DVD shipping operation for three days and this event was a turning point. Netflix leadership recognized a single point of failure in a monolith posed an existential risk to a company whose value proposition depended entirely on availability.

Between 2009 and 2012, Netflix undertook a full migration from its monolithic Java application to a cloud-based microservices architecture running on AWS. By 2012, the migration was largely complete. Netflix decomposed its platform into hundreds of microservices whereby each handled distinct functions such as user authentication, content recommendations, billing, playback, and search.

Thus, Netflix gained independent deployability, allowing engineering teams to push updates multiple times per day without affecting services across the entire platform. Horizontal scalability also became fine-grained during peak hours whereby the streaming service could scale up only the services under load rather than duplicating the entire platform.

Netflix operates at an extraordinary scale with over 230 million subscribers across 190 countries and the microservices architecture continues to support this. The investment in microservices tooling such as creating open-source frameworks like Hystrix (circuit breaker) and Eureka (service discovery) to solve the coordination challenges of distributed systems hence allowing better management of microservices complexity.

### **Case Study 2: Amazon**

 Amazon's early architecture, like many e-commerce platforms of the late 1990s, was a tightly coupled monolith and  as Amazon expanded into new product categories and geographic markets, the monolith bottleneck began to show. Amazon gradually decomposed its platform into services throughout the early 2000s, well before *microservices* had a formal name.

The architecture enabled what Amazon calls *two-pizza teams* that is to say small teams owning a service end-to-end. This accelerated innovation enormously whereby teams could experiment, release, and iterate on their services without waiting for a centralised release process. Critically, the internal services Amazon built while solving its own distributed systems problems became the foundation for *Amazon Web Services* (AWS), launched in 2006, which is now Amazon's most profitable business segment.

The service-oriented model is now inseparable from Amazon's engineering culture. As teams are structured around services, and the entire AWS product line is a direct commercial extension of the microservices architecture.

### **Case Study 3: Uber**

Uber started as a single monolithic application which managed rides, drivers, payments, and mapping within a single codebase. As Uber expanded to new cities and added new products such as *UberEats, freight, autonomous vehicles*, the monolith reached a bottleneck in which  deployments were slow, scaling was inefficient, and the codebase had grown so large that a single engineer could not understand its full scope. 

Around 2014–2016, Uber began decomposing its monolith. The migration was particularly complex because Uber had to maintain a real-time, high-availability platform while refactoring it. By 2020, Uber operated over 2,200 microservices, with services spanning dispatch, pricing, maps, payments, driver management, and fraud detection.

Microservices allowed Uber's engineering teams to spread across dozens of offices worldwide and to work independently on different aspects of the platform. It also supported Uber's aggressive multi-product expansion of products like UberEats could share core services like payments and geolocation without being coupled to the ride-sharing application logic. This architecture enabled language diversity as well, with teams adopting Go for high-performance services while retaining Python and Java elsewhere.

**Reasons why some Companies shifted away from Microservices.**

**Operational Complexity Overload.** Microservices multiply the number of deployable units dramatically. Where a monolith might require one deployment pipeline, 200 microservices require 200\. Monitoring, logging, tracing failures across distributed services, and managing inter-service communication add enormous operational overhead, especially for smaller teams without dedicated DevOps capacity.

**Distributed Systems Complexity.** Problems that are trivially solved in a monolith  such as a database transaction spanning multiple operations  become significantly harder in a distributed system. Engineers must contend with network latency, partial failures, data consistency challenges, and the complexities of eventual consistency models.

**Performance Overhead.** In-process function calls between modules in a monolith are nanoseconds fast. The equivalent cross-service HTTP or gRPC calls introduce latency, serialisation overhead, and failure modes. For performance-sensitive workflows, this overhead accumulates.

**Cost at Small Scale.** Each microservice requires its own compute resources, deployment pipeline, and monitoring. For small organisations or applications with modest traffic, the infrastructure cost outweighs the scalability benefit.

**Two Case Study of Companies that later migrated away frpm Microservices.**

### **Case Study 4: Segment**

Segment is a customer data platform that routes event data from applications to analytics and marketing tools. The company adopted microservices early, eventually running approximately 140 separate microservices. 

As Segment's engineering team grew and the volume of services increased, they discovered that the operational burden was disproportionate to the business value. Debugging a data pipeline failure required tracing events across dozens of services, and the tooling to do this effectively was expensive and complex to maintain. Many of the microservices were so small that they effectively contained just one or two functions commonly known as *nanoservices.* 

This meant microservices were  providing none of the scalability benefits of microservices while adding all the distributed systems complexity.

Engineers spent more time managing inter-service communication, handling cascading failures, and maintaining deployment infrastructure than building product features. The architecture had become an end in itself rather than a means to a business outcome.

In 2020, Segment publicly documented their decision to consolidate many of their microservices into a smaller number of larger services which effectively made a partial return to a modular monolith approach for their data pipeline infrastructure. They replaced a complex web of small services with a single, well-structured Go application they called Centrifuge. The result was a dramatic reduction in operational complexity, improved performance and faster development cycles. Segment's engineers noted that the new architecture (monolithic) was easier to reason about, test, and debug.

### **Case Study 5: Stack Overflow**

Stack Overflow is one of the most heavily trafficked websites in the world  serving hundreds of millions of developers monthly. Unlike many companies of comparable scale, Stack Overflow has been openly resistant to adopting a microservices architecture, and for a period considered expanding into one before ultimately reinforcing their commitment to a monolith.

Stack Overflow's engineering team evaluated microservices seriously and concluded that the architecture would be actively harmful to their operation. Their reasoning was detailed and instructive. Stack Overflow runs on a remarkably small and efficient infrastructure. At one point, a handful of on-premises servers handled the majority of their global traffic. This efficiency is partly a consequence of their monolithic architecture: in-process calls are fast, shared memory caching is simple, and the codebase is straightforward to reason about for a small engineering team.

The team identified that microservices would introduce latency in an application where response time is critical to user experience. Network calls would replace in-memory operations. They would need substantially more infrastructure  and at a higher infrastructure cost  to replicate at the service level what they accomplished with shared memory in a monolith. 

Stack Overflow retained and optimised its monolithic architecture, continuing to achieve exceptional performance at massive scale. Their engineering blog posts on this topic have become widely cited arguments in the broader industry debate about the appropriate use of microservices, contributing the important observation that microservices are not inherently superior — they are a solution to specific scaling and organisational problems that not every company faces.

 Stack Overflow demonstrates that the disadvantages of microservices of operational complexity, distributed systems overhead, infrastructure cost  can outweigh the advantages for companies whose scaling challenge is primarily about request efficiency rather than independent deployment velocity or team autonomy.


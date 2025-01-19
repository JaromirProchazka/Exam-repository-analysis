# Quality Requirement Scenario: Viewing Exam Results During High Traffic

## Scenario
- **Source of Stimulus**: Students accessing the results portal simultaneously.  
- **Stimulus**: A sudden surge of simultaneous requests to view exam results when they are released to all students.  
- **Artifact**: Exam Results Microservice (includes API Gateway, microservice instances, and database).  
- **Environment**: The system is under peak load during the results release period. The infrastructure is operational, but resources are heavily utilized.  
- **Response**: The system scales horizontally or optimizes database partitioning to handle the surge in requests efficiently.  
- **Measure**: Keeping the average response time for viewing results as low as possible, with a target of <= 5 seconds.  

## Solution
### **X-Axis Scaling (Horizontal Scaling)**
1. **Microservices Architecture**:  
   - The system uses a microservices architecture, enabling independent scaling to handle increased demand.  

2. **API Gateway**:  
   - Requests are directed by the API Gateway to multiple service instances, ensuring balanced load distribution.

3. **Request Handling**:  
   - A request queue is added to handle incoming requests when additional instances are created through horizontal scaling, ensuring that all requests are processed in order.  

### **Database Partitioning**
1. **Logical Partitioning**:  
   - The student data is partitioned logically (e.g., based on student ID ranges or course IDs) to reduce contention during peak periods.  

2. **Performance Optimization**:  
   - Requests are routed to the appropriate database partition, improving query performance.  

3. **Scalable Storage**:  
   - New partitions can be added as the student base grows, ensuring scalability and preventing performance bottlenecks.   

## Implementation
We have chosen to implement horizontal scaling to handle the increased traffic efficiently. This is achieved by adding a request queue that processes all incoming requests as more instances of the review grade container are created.

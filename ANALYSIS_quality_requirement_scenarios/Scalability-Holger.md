# Scenario
Viewing exam results may experience high traffic when all students try to access their results simultaneously.

## Solution

### X-axis Scaling
- **Horizontal Scaling**: Leverage a microservices architecture that allows the system to scale horizontally 
by adding more service instances during peak times.
- **API Gateway**: Use the API Gateway to efficiently distribute requests to different service instances, 
ensuring even traffic distribution.

### Shared Database
- **Database Partitioning**: Split the exam result data into logical partitions based on criteria like student ID ranges, 
course IDs. Each partition will store results for a subset of students, 
reducing the load on any single database instance.
- **Improved Performance**: This approach reduces the contention on database resources, allowing for faster query responses 
by ensuring that requests are evenly distributed across different partitions.
- **Scalability**: With database partitioning, as the number of students grows, new partitions can be added, 
allowing the system to scale more efficiently without significant impact on performance. 


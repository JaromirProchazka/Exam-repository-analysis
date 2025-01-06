# **Quality Requirement Scenario: Viewing Exam Results During High Traffic**

## **Stimulus**
- A sudden surge of simultaneous requests to view exam results when they are released to all students.

## **Source of Stimulus**
- Students accessing the results portal simultaneously.

## **Environment**
- The system is under peak load during the results release period.
- The infrastructure is operational, but resources are heavily utilized.

## **Artifact**
- Exam Results Microservice (includes API Gateway, microservice instances, and database).
- Shared Database (partitioned for scalability).

## **Response**

### **X-Axis Scaling (Horizontal Scaling)**
1. **Microservices Architecture**:
   - The system uses microservices to handle requests, allowing for independent scaling.

2. **API Gateway**:
   - Directs requests to multiple service instances, ensuring even load distribution.

### **Database Partitioning**
1. **Logical Partitioning**:
   - Student data is split into multiple partitions (e.g., based on student ID ranges or course IDs).

2. **Performance Optimization**:
   - Requests are routed to the appropriate partition, reducing contention and enabling faster query execution.

3. **Scalable Storage**:
   - New partitions are added as the number of students grows, ensuring continued scalability.

## **Response Measures**
Keeping the average response time for viewing result as low as possible <= 5 seconds.


## **Implementation**
We have chosen to implement the horizontal scaling to solve this problem. 
since the horizontal scaling means that a container can run in multiple instances it does not requrie large changes to the c4 model. 
As I am not adding anything new th the c4 model.


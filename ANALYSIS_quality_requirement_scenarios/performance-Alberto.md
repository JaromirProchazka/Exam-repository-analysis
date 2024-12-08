# Performance analysis of the review grades/credits service

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

### Scenario:

- when grades for a major course in a large faculty are released, all students simultaneously access the system to view their grades
- The system should be able to handle this load without significant performance degradation
- requirement: **The system should maintain an average response time of less than 3 seconds for grade retrieval during peak access times**

### Solution:

- Implement caching mechanisms for grade data to reduce load on the database during high-traffic periods.
- Distribute incoming requests across multiple servers to make sure no single server gets overloaded, ensuring smoother and faster responses for everyone.
- Optimize database queries and pre-process grading data to further improve response times during peak load.


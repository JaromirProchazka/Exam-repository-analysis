# Performance analysis of the Exam Module

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

### Scenario:

- when an exam date on big faculty is opened all the students are trying to register at the same time
    - Exam module should be able to respond in reasonable time to all the students
    - requirement: **request for an exam registration should have an average 2 seconds latency in peak**

### Solution:

- Because this scenario happens for a brief time relatively rarely, it is important to improve algorithms handling exam registrations as much as possible. This is the most performance-heavy operation in SIS (together with subject enrollment at the start of the semester), that is why the low-level architecture should focus on resolving this operation as fast as possible. Concurrent processing is also very important.

- Alternatively the problem can be handled by increasing resources. Faster processors, memory and networks can help. Because the performance is important only in these short periods of time quite rarely, a more money-efficient solution could be cloud hosting.
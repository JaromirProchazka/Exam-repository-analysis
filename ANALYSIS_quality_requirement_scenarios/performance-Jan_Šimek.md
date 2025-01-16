# Performance analysis of the Exam Module

## Scenario:

- **Source of stimulus:** Students (larger quantity)
- **Stimulus:** requests for registration to exam date
- **Environment:** Registration controller component
- **Response:** adequate response for the request 
- **Measure:** latency for each request should be max. 2s

## More details:

- When an exam date on big faculty is opened all the students are trying to register at the same time. This often leads to overwhelming the SIS servers.

- This is the most performance-heavy operation in SIS (together with subject enrollment at the start of the semester).

## Analysis of existing design:

- As-is all the services are deployed on one server, this might be bad for potencial horizontal scaling up. 

## Possible solutions:

1. **Algorithms**: Because this scenario happens for a brief time relatively rarely, it is important to improve algorithms handling exam registrations as much as possible. The low-level architecture should focus on resolving this operation as fast as possible. Concurrent processing is also very important.

2. **Scaling**: Alternatively the problem can be handled by increasing resources. Faster processors, memory and networks can help. If deployed separately rather than with other services, we can also scale horizontally.

3. **Cloud hosting**: Because the performance is important only in these short periods of time quite rarely, a more money-efficient solution could be cloud hosting, where the resources are paied only in this time-period when needed.
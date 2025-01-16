# Scalability analysis of the Exam Module

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

## Scenario
- **Source of Stimulus**: Strudent.  
- **Stimulus**: access system to register to exams at the end of the semester when traffic is relatively greatly increased.  
- **Artifact**: Exam Registration Service.  
- **Response**: Exam registration request is processed with the system being able to be scaled up if needed.  
- **Measure**: Performance and availability not impacted (keep the latency low, the registrations to be reliable).

## Solution:

- we need to queue requests before the service in another container to keep it reliable
- horizontal scaling already good enough because of the Microservice architecture
- at the end of the semester, we can create new instances of registration service and after that we can easily scale down 

# Modifiability analysis of the system when adding a new "Policy Adjustment Service"

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

### Scenario:

- A new grading policy is introduced and a new "Policy Adjustment Service" needs to be integrated into the system
- The system should allow the addition of the new service without requiring changes to existing services or the API Gateway logic
- requirement: **The integration of a new service should not take more than 5 development days and should not disrupt the operation of existing services**

### Solution:

- To achieve this, the system should adhere to modular design principles, with clearly defined interfaces for each service. The API Gateway should be designed to route requests dynamically based on configuration files or metadata rather than hardcoded logic.
- Additionally using a microservices architecture with loosely coupled services ensures that adding a new service requires minimal changes to the rest of the system.
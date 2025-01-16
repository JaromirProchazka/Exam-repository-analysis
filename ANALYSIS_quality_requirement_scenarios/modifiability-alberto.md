# Modifiability analysis of the system when adding a new "Policy Adjustment Service"

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

## Scenario:

A new grading policy is introduced, requiring the integration of a new "Policy Adjustment Service" into the system.

- **Source of stimulus**: System administrators or developers responsible for implementing policy updates.
- **Stimulus**: The need to add a new service to the system.
- **Artifact**: The overall system architecture, including existing services and the API Gateway.
- **Respose**: The system should enable the seamless addition of the new service without requiring modifications to existing services or the API Gateway logic.
- **Measure**: The integration process should take no more than 5 development days and must not disrupt the operation of existing services.
- 
## Solution:

- To achieve this, the system should adhere to modular design principles, with clearly defined interfaces for each service. The API Gateway should be designed to route requests dynamically based on configuration files or metadata rather than hardcoded logic.
- Additionally using a microservices architecture with loosely coupled services ensures that adding a new service requires minimal changes to the rest of the system.
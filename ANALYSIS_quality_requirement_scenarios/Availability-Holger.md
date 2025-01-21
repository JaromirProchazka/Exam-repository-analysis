# **Availability of the Exam Registration**

## Scenario
- **Source of Stimulus**: Students.  
- **Stimulus**: Thousands of students attempting to register simultaneously for exams.  
- **Artifact**: Exam registration system, including the database and data access layer.  
- **Environment**: Peak registration period, causing high traffic and potential database timeouts.  
- **Response**: The system temporarily queues the registration requests and provides feedback to students, ensuring smooth operation despite high load.  
- **Measure**: No request is lost. 

## Solution 
This scenario have been chosen to be implemented, but in a more general way. This scenario also works if the database 
breaks or timeouts. 


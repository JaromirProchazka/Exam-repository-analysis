# Availability scenario for Credit Assignment

## Scenario
- **Source of Stimulus**: Teacher.  
- **Stimulus**: Attempts to award credit to a student.  
- **Artifact**: Credit awarding service.  
- **Environment**: Normal operation, encountering a temporary database connectivity issue.  
- **Response**: The system detects the issue, recovers quickly, and completes the credit assignment without manual intervention.  
- **Measure**: Recovery is completed within 2 seconds, ensuring minimal disruption to the process.  


## Solution


1. **Fault Detection**:  
   - Use heartbeat messages or ping/echo mechanisms to detect database connectivity issues promptly.  

2. **Fault Recovery**:  
   - Implement retry logic to handle database faults by reattempting the credit assignment.   

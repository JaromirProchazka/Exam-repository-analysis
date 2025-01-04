# **Availability of the Exam Registration**

## **Scenario**
**Problem**: When the exam registration period opens, thousands of students attempt to register simultaneously, causing high traffic on the system. This can result in slow performance, database timeouts, or system crashes.

## **Artifacts**  
- **System database**  
- **Data access layer component**  

## **Response**  
1. **Failure Detection**: The system detects a database failure (e.g., timeout or unresponsiveness).  
2. **Request Handling**: The student’s registration request is stored temporarily in an in-memory queue or cache.  
3. **User Feedback**: The student receives a success notification, ensuring a smooth user experience.  
4. **Delayed Write**: Once the database becomes available, the system writes the pending registration requests to the database.  

## **Response Measures**  
- **Availability**: The system continues to accept and queue registration requests even when the database is down.  
- **Data Integrity**: The system ensures that no registration requests are lost during database outages.  
- **User Experience**: Students are immediately notified of successful registration, reducing anxiety or confusion during peak usage.  

## **Implementation**
This scenario have been chosen to be implemented, but in a more general way. This scenario also works if the database 
breaks or timeouts. 
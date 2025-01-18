# Availability Scenario for Deferred Grade Change Notifications

## Scenario

- **Source of Stimulus**: Entity using the Awarding Grade container.
- **Stimulus**: Requests to change a student grade.
- **Environment**: Notification System is down.
- **Response**: The notifications are sent out when the Notification System
    comes back up again.
- **Measure**: The notifications must be sent out within 30 minutes after
    the Notification System becomes available, and at least 200
    notifications must be supported for this deferred delivery.

## Solution

1. **Fault Recovery**:
    - An asynchronous queue for the notification system could be
    implemented as a separate container. Its responsibility
    would be to relay the notifications in the queue to the
    notification service to periodically retry sending the
    notification if the system fails.

2. **Fault Prevention**:
    - Rate limiting could be
    implemented, so that when the Notification System
    goes up again, the surge of pending notifications does not
    immediately put it under heavy load.

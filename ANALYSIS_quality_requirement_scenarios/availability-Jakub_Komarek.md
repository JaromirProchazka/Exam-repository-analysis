# Availability Scenario -- Deferred Grade Change Notifications

When the API Gateway relays a request to change a student grade
to the Awarding Grade container, this request must be processed
even if the Notification System is down. The notifications
should be sent out within 30 minutes of the Notification System
becoming available again. At least 200 notifications must
be supported for the deferred notification delivery.

## Solution

An asynchronous queue for the notification system could be
implemented as a separate container. Its responsibility
would be to relay the notifications in the queue to the
notification service to periodically retry sending the
notification if the system fails. Rate limiting could be
implemented, so that when the Notification System
goes up again, the surge of pending notifications does not
immediately put it under heavy load.

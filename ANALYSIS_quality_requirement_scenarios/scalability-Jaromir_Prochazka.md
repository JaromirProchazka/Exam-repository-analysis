# Scalability analysis of the Exam Module

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

## Scenario:

- At the end of the semester, the traffic is relatively greatly increased
- we want to make sure that the system can be if needed scaled up to
  - keep the latency low
  - the registrations to be reliable

### The horizontal scaling

- The micro-services architecture makes it easy to duplicate the Exam Registration Service in time of need
  - and in time of low to now traffic in the middle of semester to scale back down
  - the Gateway makes it possible to dynamically redirect request to new Registration services instances
- The services reliability in this scenario is limited, since there is now cashing of the registration Requests

## Solution:

- in this responsibility, speed isn't as important as reliability,
- it will be best to add a separate cache component to the Exam Registration service so that you do not miss any request

# Testability analysis of the Exam Module

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

## Scenario:

- *Source of Stimulus*: Developer
- *Stimulus*: Attempts to test students register for for an exam reliability
- *Artifact*: Exam Registering Service
- *Environment*: Testing Environment
- *Response*: System gives up tested users role and how the request changed the internal state
- *Measure*: System easily gives up this information and enables 100 role coverage test

## Solution:

- the senders requests must be logged for the tests to be run
- we create a local request storage
- the consequent change in the systems state is not easy to get because of the sharerd database
- so we should split the data base to local microservices databases, where the changes can be easily monitored
- create some logging mecahnism on each database to monitor state

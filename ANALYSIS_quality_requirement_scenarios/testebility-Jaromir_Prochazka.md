# Testability analysis of the Exam Module

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

## Docs

- Docs are provided in the C4 diagram in the [docs file](https://github.com/Metalystn/Exam-repository/blob/main/C4%20Model/C4-model-new.md)
- this makes testability better since the team can easily understand bigger the structure
- Although the docs only cover the Container level
  - bad for testability, since the Containers are what is most likely being tested and their structure isn't documented

## Overall testability

- (how easily the system under the tests will give up its faults, test efforts, coverage of possible cases)
- since micro services don't have their own databases but share one, they don't thus own their state, and it will be more difficult to monitor it
- but the micro-services themselves provide good decomposition
  - since there aren't any dependencies between the micro-services, this makes the input control good

## Scenario:

- we want to test the Exam Registering
  - that the roles of users are handled correctly (100% roles coverage)
  - that only the students that are enrolled in the subject and ticket can register
  - that the registration is reliable, it doesn't get lost

### Observability

- the state is saved to global database which is more difficult to monitor
- the presence of other services, changing the databases state can make the testing less deterministic

### System complexity

- The registration is separated into its own 1 container with little dependencies on others
  - simple to cover API possible calls
- services are logicaly split to components that can be quite easily unit tested
  - Eligibility Check component for the roles tests

## Solution:

- split the database into microservices databases
- create some logging mecahnism on each database to monitor state

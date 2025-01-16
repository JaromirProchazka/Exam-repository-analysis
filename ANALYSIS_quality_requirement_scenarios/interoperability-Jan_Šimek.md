# Interoperability analysis of the Exam Module

## Scenario:

- **Source of stimulus:** External SIS module
- **Stimulus:** Request for students data
- **Environment:** Student list component 
- **Response:** Students data send
- **Measure:** 100% of data provided

## Analysis of existing design:

- As-is Exam module stores data about students, which will be needed by most other modules, so they must be accessible. That is not the case right now.

## Possible solutions:

1. **Add access to data**:
    - Add a way for the other modules to access the data:
        - One way is to add direct connection to Student list component which provides this data inside the module. This approach might lead to tight coupling between modules.
        - Another approach is to add connection from other modules directly to the database, which may lead to even more problems.
        - Better solution might be to provide this information via API using some defined comunication protocol.
    - All the solutions approaches must take in account security.

2. **Separate data to new module**:
    - Extract the data from Exam module and define separete "People" module which will handle all the data by itself.
    - This is the solution chosen by our team in our work on Schedule module.


## Aditional notes:

- As-is Exam module also stores data about room reservations for exams. Scheduling module will certainly need to access this data on a regular basis so it can use them together with data about room reservations for lectures. This should be resolved by merging these two reservation systems into one.

- As-is Exam module also stores data about grades and courses, which must be accessible for all other modules as well.

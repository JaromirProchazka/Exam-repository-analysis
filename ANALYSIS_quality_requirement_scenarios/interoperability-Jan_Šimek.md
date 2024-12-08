# Interoperability analysis of the Exam Module

Exam-repository: https://github.com/Metalystn/Exam-repository/tree/main

### Scenario:

- an external module needs to get data from Exam module
    - as-is module stores data about room reservations for exams only, Scheduling module will certainly need to access this data on a regular basis so it can use them together with data about room reservations for lectures  
    - as-is module stores data about students and courses, which will be needed by most other modules, so they must be accessible
    - as-is module stores data about grades, which must be accessible for future modules
    - requirement: **100% requests for data are processed**

- an external module needs to use logic for statistical reports from exams
    - as Statistical Reporting service is a part of the system, the module should offer and resolve requests on these reports
    - requirements: **100% requests for reports are processed**

### Providing data to the larger system:

- Exam module stores all the data it needs for its functioning. This data will be used in other modules as well. As of now, no means of providing data to the other modules is documented. The same applies to logic.

- For some of the data it might be impractical to store them in this module. Frequent calls from other modules might be too demanding. This needs to be addressed in performance analysis and consulted with other teams working on the other modules.

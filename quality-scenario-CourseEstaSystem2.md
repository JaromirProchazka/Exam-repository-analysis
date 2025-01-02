### Design-time Dimensions

#### Quality Scenario: Modifiability

- **Stimulus:** The system needs to allow bulk course deletions, as requested by administrators.

- **Source of Stimulus:** Feature request from stakeholders.

- **Environment:** Development and testing environments.

- **Artifact:**
  - `CourseChanger Interface`
  - `CourseController`
- **Response:**
  - The feature is implemented using batch processing.
  - The system is tested to ensure that bulk deletions do not affect other course data.
  - The feature is deployed without downtime.

- **Response Measure:**
  - Feature implemented and tested within 3 weeks.
  - Test coverage for the new functionality exceeds 90%.

##### The architecture requires:

- **Batch Processing:** Design the CourseController to handle batch delete requests efficiently.
- **Data Integrity Checks:** Validate that only the intended courses are deleted.
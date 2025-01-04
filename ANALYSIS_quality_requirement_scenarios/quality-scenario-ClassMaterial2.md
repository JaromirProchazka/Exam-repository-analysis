# Quality Scenario: Modifiability

## **Stimulus**
A new feature request requires tracking submission timestamps for assignments and saving a version history for homework updates. This requires modifying the system logic for **submission** and **update** functionalities.

## **Source of Stimulus**
Students and teachers request the feature.

## **Environment**
During active semester usage, with ongoing homework submissions and updates.

## **Artifact**
- `Homework submission/creation interface`
- `Homework Controller`
- `Class Material Database Communicator`

## **Response**
1. Create new separate controllers:
   - **Homework Update Controller**: Tracks and stores version history of homework updates.
   - **Homework Deletion Controller**: Manages secure deletion of homework.
   - **Homework Submission Controller**: Records submission timestamps and validates submitted files.
2. Extend the `ClassMaterial Database` schema to include:
   - A `timestamp` field for submission tracking.
   - A `version history` table for homework updates.
3. Adjust the `Homework submission/creation interface` to route requests to the appropriate controllers.

## **Response Measure**
- The changes are implemented without disrupting existing functionalities.
- New features (submission tracking and version history) are completed within.

## **Architectural Extension**
The architecture needs the extensions:
1. **Separate Controllers**:
     - `Homework Update Controller`
     - `Homework Deletion Controller`
     - `Homework Submission Controller`
2. **Database Schema Update**:
   - `submission_timestamp` column for tracking submission times.
   - `version_history` table to store previous versions of homework.


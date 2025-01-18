# Security Scenario for Grade Modification Nonrepudiation

## Scenario

- **Source of Stimulus**: An evil teacher.
- **Stimulus**: Makes unauthorized changes to student grades.
- **Artifact**: Examination system.
- **Environment**: Normal operation.
- **Response**: The system audits the change.
- **Measure**: The teacher must not be able to plausibly deny
    making the change.

## Solution

1. **Recovering from Attacks**:
    - Add a Grade modifications audit trail component to Awarding grade service. The responsibility of this module would be to keep the complete history of awarded grades (together with the teacher who awarded them).

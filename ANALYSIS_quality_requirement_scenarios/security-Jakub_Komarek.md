# Security Scenario -- Grade Modification Nonrepudiation

A teacher (inside attacker) makes unauthorized changes to student grades
in the Examination system. It must not be possible for the attacker to plausibly
deny making the changes (nonrepudiation).

## Solution

Add a Grade modifications audit trail component to Awarding grade service.
The responsibility of this module would be to keep the complete history
of awarded grades (together with the teacher who awarded them).

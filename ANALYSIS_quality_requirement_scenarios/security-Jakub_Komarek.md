# Security Scenario -- Grade modification nonrepudiation

A teacher (inside attacker) makes unauthorized changes to student grades
in the Examination system. It must not be possible for the attacker to plausibly
deny making the changes (nonrepudiation).

## Solution

Add a Grade modifications history component to Awarding grade service.
The responsibility of this module would be to keep the complete history
of awarded grades (together with the teacher who awarded them).
The Review grades controller should then use this history component
to find the most recently awarded grade.
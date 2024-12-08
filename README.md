# Exam System Analysis

This forks purpose is to analyse the Exam module for given scenarios and quality requirements. It is done by the Schedule team.

# Exam System

## Core features and responsibilities

### Awarding Credits
As a teacher I need to award credits to student so that they can register for the final exam.

#### Feature breakdown
1. The teacher opens the exams interface in the student information system (SIS).
2. The system retrieves and displays the list of courses taught by the teacher from the database.
3. The teacher selects the relevant course to manage.
4. The system fetches and displays the list of students enrolled in the selected course.
5. The teacher chooses the student they want to review for credit assignment.
6. If the course uses midterms or quizzes:
    1. The system retrieves and displays the student's midterm and quiz results from the database.
    2. The teacher reviews the grades and determines if the student has earned sufficient points.
    3. The teacher selects the "Award Credit" button for the student.
    4. The system validates whether all conditions for awarding credit (like quiz/midterm performance) have been met.
    5. The system prompts the teacher with a confirmation dialog: _"Are you sure you want to award credit to this student?"_
        1. If the teacher selects "Yes" the system performs the following:
            1. Updates the student's record in the SIS, assigning the credit as "C".
            2. Saves the action (credit award, timestamp, teacher ID, etc.).
            3. Displays a success confirmation to the teacher: _"Credit successfully awarded."_
            4. Sends a notification to the student (via email, SMS, or the SIS notification system) informing them they have been awarded credit.
        2. If the teacher selects "No" the system aborts the action and returns to the previous page. 
7. If the course doesn’t rely on midterms/quizzes for credit awarding:
    1. The teacher manually assesses the student’s eligibility for getting the credit.
    2. The teacher repeats steps 6.iii - 6.v without reviewing midterm/quiz results.

#### Responsibilities

####  Data Collection Responsibilities:
Database Integration:
- Fetch the list of courses the teacher is teaching using a query from the SIS database.
- Retrieve the list of enrolled students for the selected course.
- If applicable, retrieve midterm/quiz results for each student.

Condition Checks:
- Verify if the student has met the conditions (grades, attendance, etc.) for receiving the credit.

#### Data Display Responsibilities:
- Display the list of courses and students in the teacher’s dashboard.
- Display student grades (if applicable) and provide a clear action button ("Award Credit").

#### Error Handling and Validation Responsibilities:
- Ensure that the system checks if the student meets the credit conditions before allowing the teacher to proceed.
- Handle the teacher's input on the confirmation dialog and proceed accordingly (yes/no).

#### System Communication Responsibilities:
- Integrate with email/SMS APIs or internal notification services to send automated messages to students once credit is awarded.
- Ensure that notification status (sent, delivered, failed) is logged and visible to the teacher if needed.
- Use transactional operations in the database to ensure that awarding credit and sending student notifications are atomic actions (either both succeed, or neither does).

---
---

### Awarding Grades
As a teacher I need to award grades to students so that I can evaluate their work and provide them with feedback on their performance.

#### Feature breakdown
1. The teacher opens the grading interface.
2. The system retrieves and displays a list of students who completed the exam.
3. The teacher selects a student to grade or chooses to grade all students.
4. The teacher can either:
    1. Input grades manually, or
    2. Review automatically generated grades for objective questions.
5. If inputting manually:
   1. The teacher enters the score for each section of the exam.
   2.  The teacher adds feedback or comments if needed.
6. If using automated grading:
   1. The system calculates grades for objective questions (e.g., multiple-choice).
   2. The teacher reviews and adjusts the grades if necessary.
7. Determine Bonus Criteria:
   1. The teacher decides the reason for awarding bonus grades, such as:
      - Extra credit work
      - Outstanding performance
      - Participation
      - Bonus questions on the exam
8. Enter the Bonus Grades:
   1. In the grade entry section, the teacher manually adds bonus points to the student's total score.
   2. The system may offer a separate field to input bonus grades or allow the teacher to adjust the final score directly.
9. Review the Grades:
   1. The teacher reviews all inputted grades and feedback to ensure accuracy.
   2. Adjustments can be made at this stage if necessary.
10. The teacher submits the final grades.
11. The system publishes the grades, and students are notified via their exam dashboard.

#### Responsibilities

#### Data Handling:
- Secure and Accurate Grade Input:
Ensure that grades are entered accurately and stored securely in the centralized database.

#### Automated Calculations:
- For objective questions, the system should ensure that calculations are correct and in line with grading rubrics.

#### User Interface:
- Grade Entry and Feedback Interface:
Provide a simple, intuitive interface for teachers to enter grades and feedback, with clear navigation and support for both manual and automated grading processes.

#### Notifications and Communication:
- Student Notification:
Once grades are published, the system should notify students immediately, and they should be able to view their grades, feedback, and performance insights in their personal dashboards.

#### Analytics and Reporting:
- Grade Analysis:
Offer teachers insights into class-wide performance, helping them make informed decisions about future teaching strategies or exam difficulty.

---
---

### Exam Registration
As a student I need to register to an exam so that I can pass the course.

#### Feature breakdown
1. The student opens the registration interface.
2. The student selects a list of the subjects they are registered for.
3. Optionally, the student can choose the teacher that handles the terms for those subjects.
4. The system shows a list of exam terms that match the selected subject and teacher.
5. The student chooses one exam term to register for.
6. The system checks if the student is allowed to register for the selected exam (e.g., prerequisites, registration deadlines).
7. If the student is allowed:
   1. the system registers the student for the exam and confirms the registration.
   2. The system updates the student’s exam registration status.
   3. The student receives a confirmation of the registration.
8. If the student is not allowed:
   1. the system prevents them from registering for the exam.
   2. The student receives a clear notification explaining why they are not allowed (e.g. prerequisites, registration deadlines).
9. Optionally, the student can deregister from the term.
10. The system tracks the deadline for deregistration and prevents deregistration after the specified deadline.
11. The exam registration status is visible to both students and instructors.

#### Responsibilities

#### Registration data collection responsibilities
- Display a list of subjects the student is registered for.
- Optionally, allow students to filter exam terms by teacher.
- Show a list of available exam terms based on subject and teacher selection.
- Validate that the student meets the prerequisites and is allowed for the exam.
- Ensure data related to exam dates, times, and registration slots is up-to-date.
- Allow students to select their exam term from the list.

#### Exam registration process responsibilities
- Verify that student meets the requirements to take the exam.
- Record the students registration for the selected exam.
- Verify that exam capacity is not exceeded.
- Allow students to deregister from exams before the deadline.

#### Confirmation and notification responsibilities
- Provide immediate feedback to the student about the success or failure of their registration.
- Send an email or notification to the student confirming the registration.
- Display registered exams in the students exam dates dashboard.

#### Deregistration responsibilities
- Enable the student to deregister from an exam before the deadline.
- Ensure that deregistered slots are made available for other students.

---
---

### Registration of rooms
As a manager I need to be able to register rooms available for exams so that the teachers can exam students.

#### Feature Breakdown
1. The manager opens the rooms interface.
2. The system collects the list of rooms in which currently exam can be taken.
3. The system displays the list to the manager.
4. The manager either: selects a room, or add a new room.
5. If the manager adds a new room:
   1. The system displays necessary information on the room to be filled. (address/building, name/number of room, capacity, availablity)
   2. The teacher fills the necessary information of the new room.
   3. The system check for conflicts with other rooms. (if the primary key of a room is the same as the new room)
   4. If there is not conflict:
      The system adds the new room to the centralized database.
   6. If there is a conflict:
      1. The systems informs the manager that there is a conflict, showing the conflicted information.
      2. The teacher either: resolve the conflict or cancel the new room.
      3. If the teacher resolve the conflice return to step 5 ii.
      4. If the teacher cancel the new room return to step 1.
6. If the managers selects a room:
   1. The system collects the information of the selected room.
   2. The system displays the information of the selected room.
   3. The manager either: removes the selected room or edit information of the selected room.
   4. If the manager removes the selected room:
      1. The system checks if there are any exams in the selected room.
      2. If there are no exams: the system removes the room from the centralized database.
      3. If there are exams: the systems disallow the removal of the room.
   5. If the manager edit information of the selected room:
      1. The system check for conflicts with other rooms. (if the primary key of a room is the same as the selected room after the changes)
      2. If there is not conflict:
         The system adds the changes to the selected room to the centralized database.
      3. If there is a conflict:
         1. The systems informs the manager that there is a conflict, showing the conflicted information.
         2. The teacher either: resolve the conflict or cancel the edit of information of the selected room.
         3. If the teacher resolve the conflice return to step 5 v a.
         4. If the teacher cancel the new room return to step 6 i.

#### Responsibilities

#### Data collection responsibility
- Integrate with a centralized database.
- Ensure transmission from the centralized database to the machine.
- Ensure that the transmitted data is syntactically correct.

#### Data writing resposibility
- Integrate with the Centralized database.
- Ensure that the user has the access to edit the information.
- Ensure transmission from the machine to the centralized database.
- Ensure that the transmitted data is syntantically correct.

#### Data display responsibility
- Display on the teacher's monitor.

#### Data conflict responsibility
- Ensure that the primary key of the data is not duplicated.

---
---

### Viewering Results

#### Feature breakdown
1. The student opens the exam results interface.
2. The system collects the list of exams across all the courses the student has taken.
3. The system displays a list of exam results, grouped by course, so the student can see all their results at once.
4. Each exam result shows the course name, and whether the student passed or failed.
5. Optionally, the student can expand any exam result to view a detailed breakdown of their score.

#### Responsibilities

#### Security and Privacy Responsibility
- Ensure that the student's exam results are only accessible to the authorized student.
- Implement authentication and authorization mechanisms to prevent unauthorized access to sensitive information.

#### Data display responsibility  
- Display on the student’s screen.
- Clearly indicate whether the student has passed or failed, with additional feedback if available.

---
---

### Statistical Report
As a manager, I need to create a report of results so that people registering for a particular class can see metrics like pass rate, fail rate, and more.

#### Feature Breakdown

1. The manager opens the results reporting interface.   
2. The system retrieves historical result data for the selected class.
3. The system calculates relevant metrics:
   - Pass rate
   - Fail rate
   - Average score
   - Distribution of grades or other relevant statistics
4. The system displays these metrics in a report format to the manager:
   - Summary metrics (pass/fail rates, average scores, etc.)
   - Visuals or charts for quick insights (e.g., bar charts, pie charts)
5. The manager can perform the following actions:
   - **Save the report**: Store the generated report in the centralized database for future reference.
   - **Edit specific metrics or add notes**: If needed, add commentary or clarify specific details for future viewers.
   - **Share the report**: Make the report viewable to users registering for the class, either by making it public or granting access permissions.
6. If the manager saves the report:
   1. The system checks for existing reports on the same class and term to avoid duplicates.
   2. **If a duplicate exists**: The system prompts the manager to confirm updating the existing report or creating a new one.
   3. **If no duplicate exists**: The system saves the report in the centralized database.
7. If the manager shares the report:
   1. The system verifies the permissions for the intended viewers (registrants or other roles).
   2. The system updates access rights and links the report to the registration interface for the relevant class.
  
#### Responsibilities

#### Data Collection Responsibility
  - Integrate with the centralized database to retrieve past results.
  - Ensure that data is retrieved accurately and includes necessary fields like grades, dates, and student IDs.

#### Data Processing Responsibility
  - Calculate pass rates, fail rates, and other metrics.
  - Ensure that metrics are calculated accurately and represent the data clearly.

#### Data Writing Responsibility
  - Store the generated report in the centralized database.
  - Allow updates or edits to existing reports.
  - Ensure data is transmitted correctly and maintains integrity.

#### Data Display Responsibility
  - Present results metrics in a user-friendly, visually appealing format.
  - Ensure the report is accessible to designated viewers when shared.

#### Data Conflict Responsibility
  - Avoid duplicate reports by checking existing records for the same class and term.
  - Ensure report updates are conflict-free with existing data in the database.

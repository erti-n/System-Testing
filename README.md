# System-Testing


1. Introduction to Testing

Software testing is the process of evaluating software components to identify bugs, defects, and unexpected behavior. Testing ensures that the system functions correctly under both normal and abnormal conditions.

Testing is an important part of software development because it improves:

Reliability
Security
Correctness
Maintainability
User experience

In the Epoka Student Event Platform, testing is necessary to ensure that students can register, log in, browse events, and register for events without problems.

2. Purpose of Testing

The purpose of testing is to detect problems early before the software is deployed.

Testing helps verify that:

Users can successfully interact with the system
Invalid input is handled correctly
Data is stored properly
Unauthorized access is prevented
Critical functionalities behave as expected

For this project, testing ensures that the event registration system works correctly and prevents issues such as duplicate registrations or invalid login attempts.

3. Focus on Testing a Single Component
Selected Component: Event Registration Function

The selected component for testing is the Event Registration Function.

This component is important because it allows students to register for university events. If this functionality does not work correctly:

Students may not be able to participate in events
Duplicate registrations may occur
Invalid event IDs may be accepted
The database may store incorrect information

The event registration process is critical because it directly affects the core functionality of the platform and user experience.

5. Writing Test Code

def register_event(student_id, event_id, registered_events):

    if student_id == "" or event_id == "":
        return "Student ID and Event ID are required"

    if not isinstance(student_id, int) or not isinstance(event_id, int):
        return "Invalid input type"

    if event_id not in [1, 2, 3, 4, 5]:
        return "Event does not exist"

    if (student_id, event_id) in registered_events:
        return "Student already registered"

    registered_events.append((student_id, event_id))
    return "Registration successful"


    def test_valid_registration():
    registered_events = []
    result = register_event(101, 1, registered_events)
    assert result == "Registration successful"


    def test_duplicate_registration():
    registered_events = [(101, 1)]
    result = register_event(101, 1, registered_events)
    assert result == "Student already registered"


    def test_invalid_event():
    registered_events = []
    result = register_event(101, 99, registered_events)
    assert result == "Event does not exist"


    def test_empty_student_id():
    registered_events = []
    result = register_event("", 1, registered_events)
    assert result == "Student ID and Event ID are required"


    def test_empty_event_id():
    registered_events = []
    result = register_event(101, "", registered_events)
    assert result == "Student ID and Event ID are required"


    def test_both_fields_empty():
    registered_events = []
    result = register_event("", "", registered_events)
    assert result == "Student ID and Event ID are required"


    def test_invalid_data_type():
    registered_events = []
    result = register_event("student", 1, registered_events)
    assert result == "Invalid input type"


6. Running Tests

The tests were executed using Python in Visual Studio Code. A separate test file named TESTING.py was created containing all test cases related to the Event Registration component.

The tests were run using the following command in the terminal:

TETSING.py

The system executed each test case and verified whether the returned result matched the expected output using Python assertions.

Interpreting Test Results

Passing Tests:
If all assertions are correct, the program executes successfully without displaying errors. A success message is shown in the terminal:
===================================
All test cases executed successfully
7/7 tests passed
===================================
Failing Tests:

If the actual output does not match the expected output, Python displays an AssertionError. This indicates that the tested functionality is not behaving correctly.

Errors:
Errors occur when the program encounters issues such as syntax mistakes, missing variables, or invalid code structure. These errors prevent the tests from running completely.


Test Execution Summary

Test Case	                 Status
Valid registration	         Passed
Duplicate registration	     Passed
Invalid event ID	         Passed
Empty student ID	         Passed
Empty event ID	             Passed
Both fields empty	         Passed
Invalid data type	         Passed


7. Test Coverage

Test coverage is important because it measures how much of the software functionality is tested. High test coverage helps ensure that the application behaves correctly under different conditions and reduces the possibility of undetected bugs.

For the Epoka Student Event Platform, the implemented tests cover the most important scenarios of the Event Registration component, including:
-Successful event registration
-Duplicate registration attempts
-Invalid event IDs
-Empty input fields
-Invalid data types
-Validation handling

These tests cover:

-Normal user behavior
-Invalid user input
-Boundary and failure conditions

The testing process ensures that the registration functionality behaves correctly in both expected and unexpected situations.

Although the current tests cover the main logic of the component, future improvements may include:

-Database integration testing
-Frontend/UI testing
-Security testing
-Performance and load testing

Overall, the implemented tests provide good coverage for the critical paths and failure scenarios of the Event Registration component.


SUGGESTED REPORT STRUCTURE


INTRODUCTION  - - Software testing is the process of evaluating software to identify bugs, defects, and unexpected behavior. Testing is important because it improves software reliability, correctness, security, and maintainability.

CHOSEN COMPONENT - - The selected component is the Event Registration Function. This component allows students to register for events and prevents duplicate or invalid registrations. It was selected because it is one of the core functionalities of the Epoka Student Event Platform.

TEST CASES - - The test cases include valid registration, duplicate registration, invalid event ID, empty fields, and invalid data types. Each test case contains expected outputs to verify correct system behavior.

TESTING TOOLS - - Python assertions were used to perform testing. Visual Studio Code was used as the development environment and terminal execution tool.

TEST CODE - - Separate Python test functions were implemented inside the TESTING.py file. Assertions were used to compare expected and actual outputs for each test scenario.

EXECUTION RESULTS - - All implemented tests executed successfully. The results showed that valid registrations passed correctly while invalid scenarios returned appropriate validation messages and errors.

COVERAGE AND REFLECTION - - The tests covered the most important paths of the Event Registration component, including normal usage, invalid inputs, and failure conditions. Future improvements may include database testing, UI testing, security testing, and performance testing.

---
title: Validation
has_children: false
nav_order: 6
---

# Validation

## Testing approach
The testing activity was carried out with the goal of validating both the business logic and the presentation layer of the application, while keeping a clear separation of concerns between components.

A bottom-up testing strategy was adopted:
1. unit tests were first implemented for the Model layer,
2. then extended to DAO and Controller components,
3. finally, basic automated tests were added for the View layer.

Although a strict Test-Driven Development (TDD) approach was not followed from the very beginning, testing was performed incrementally, with tests written alongside or immediately after the implementation of each component.

### Testing framework selection

Different testing frameworks were adopted depending on the nature of the components under test.

The **Model**, **DAO**, and **Controller** layers were tested exclusively using the `unittest` framework.  
These components implement pure business logic and data access logic, are deterministic, and do not depend on external runtime environments or graphical subsystems. For this reason, the standard Python testing framework was considered sufficient and appropriate.

However, the **View layer**, implemented using Kivy/KivyMD, required a different approach. GUI components depend on an event-driven architecture, a graphical event loop, and platform-specific initialization. While the test cases themselves are still structured as `unittest.TestCase` classes, the `pytest` framework was introduced as a test runner for the View tests.

The use of `pytest` was motivated by:
- improved compatibility with Continuous Integration environments,
- better control over environment variables and headless execution,
- support for test markers to distinguish UI tests,
- reliable execution of GUI-related tests across different operating systems.

In summary, for the View layer `pytest` provided better support for fixtures, markers and CI execution, which helped address issues related to GUI testing in a headless environment.

This hybrid approach allows the project to:
- keep unit tests simple and standard where possible,
- use a more flexible and robust testing infrastructure only where required by the GUI framework.

## Testing (automated)
Each group of tests is directly related to the functional requirements associated with task or note management, data persistence, and user interaction.

### Unit testing

Unit tests were developed for the following components:
- Model classes: tests validate object creation, attribute initialization, and domain-level constraints. These tests ensure that domain objects behave correctly in isolation.
- DAO classes: DAO unit tests verify correct interaction with the persistence layer, including:
  - saving entities,
  - retrieving stored data,
  - handling empty or invalid queries.
- Controller classes: controller unit tests focus on:
  - correct orchestration of model and DAO components
  - invocation of the appropriate persistence operations,
  - validation of input before executing business logic.

All unit tests execute successfully.
Test coverage is focused on core business logic, which represents the most critical and error-prone part of the system.

### Integration testing
Integration testing was performed by testing the interaction between multiple components within the application.

As already mentioned, for the View layer both unittest and pytest were used, and the View tests initialize the application, simulate events, and verify UI behavior. Because these tests involve multiple components working together, they also cover integration testing and lightweight system testing.
Although full end-to-end tests were not implemented, this approach allowed me to validate the overall behavior of the application in an automated and reproducible way.

In particular, several tests in the View layer verify the integration between:
- View components and Controllers
- Controllers and Model objects
- internal View logic and event handling

These tests ensure that components correctly collaborate and exchange data, even though they are not placed in dedicated integration test files.

In these tests, real components were used instead of mocks, since the interactions are simple and deterministic.
This choice increases confidence that components work correctly when combined.

All integration tests pass successfully.

### System testing
System-level tests were conducted through automated GUI tests on the View layer.

These tests initialize the application in a controlled environment, simulate user interactions, and verify the overall behavior of the system across multiple layers (View, Controller, and Model).

While full end-to-end testing with real user input and persistent storage was outside the scope of this project, the adopted approach provides a reasonable level of confidence in the correct behavior of the system as a whole.

## Acceptance tests (manual)
Manual acceptance tests were conducted to validate user-facing functionality, including:
- creating and managing tasks (scheduling them, marking them as completed/not completed, deleting them)
- creating and managing notes (editing the content of notes, deleting them)
- creating and assigning topics
- navigating between screens
- verifying correct persistence of data across application runs

Each acceptance test followed a simple and repeatable plan:
1. launch the application
2. perform the user interaction defined by the requirement
3. verify that the expected result is obtained

All manual acceptance tests were completed successfully and confirm that the application meets its functional requirements from an end-user perspective.

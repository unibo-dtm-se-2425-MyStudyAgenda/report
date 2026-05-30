---
title: Future work
has_children: false
nav_order: 13
---

# Known issues and future work

## Known Issues
The main known limitation of the current project concerns the CI/CD pipeline in the Windows environment. While all tests completed successfully on Ubuntu and macOS runners in under one minute, the Windows workflow consistently exceeded GitHub Actions' execution time limit and was terminated after 30 minutes. Since no test failures were reported before the timeout, the issue appears to be related to platform-specific behavior, such as differences in process management, file handling, dependency execution, or operating-system-specific performance characteristics.

Although the issue does not affect the functionality of the application itself, it prevents full validation of the test suite across all supported operating systems. Due to time constraints, the root cause could not be conclusively identified and remains an area for future investigation.

## Future Developments and Web Migration
A major direction for future development would be the migration of the application from a desktop-based architecture to a web-based platform. By adopting a web-compatible technology stack, the application could be accessed seamlessly across multiple devices while maintaining a synchronized user experience. Such a transition would require the introduction of a centralized backend, secure user authentication, and cloud-based data storage.

The user interface could also benefit from migration to a more modern GUI framework. While Kivy enabled rapid cross-platform development and fulfilled the project's requirements, alternative frameworks could provide a more contemporary visual design and a richer set of user-interface components.

Additional features that could further enhance the application include automated notifications for upcoming deadlines, study-progress analytics, and integration with external calendar services such as Google Calendar and Outlook. These additions would transform MyStudyAgenda from a standalone planning tool into a more comprehensive academic productivity platform.

Other potential improvements include:

* filtering tasks and notes by topic or category;
* supporting all-day tasks without requiring explicit start and end times;
* warning users about unsaved changes when leaving a note-editing screen;
* providing advanced search functionality across notes and tasks.

These enhancements would improve both usability and functionality while preserving the modular architecture established during the current development cycle.


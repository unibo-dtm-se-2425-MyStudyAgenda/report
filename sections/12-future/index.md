---
title: Future work
has_children: false
nav_order: 13
---

# Known issues and future work

## Known Issues
The most significant technical hurdle currently facing the project is the instability of the Automated GUI Testing suite within the CI/CD pipeline. Although logic-based unit tests pass consistently across all operating systems, the graphical tests frequently fail in headless environments due to complexities with rendering. Addressing this would require a more sophisticated mock environment to simulate user interactions without relying on hardware acceleration.

## Future Developments and Web Migration
To increase the utility of the software, the primary goal for future iterations is to migrate the application to a Web-based architecture. By transitioning from a standalone desktop framework to a web-compatible stack (such as using Kivy’s web support or a dedicated web framework), the application could be accessed on multiple devices for a single user. This shift would necessitate the implementation of a centralized backend and a secure user authentication system to manage synchronized cloud storage.
Furthermore, the user experience could be greatly enhanced by integrating automated notifications for upcoming deadlines and an analytics dashboard to track study progress over time. Expanding the current modular structure to support third-party calendar integrations (such as Google Calendar or Outlook) would also transform MyStudyAgenda from a standalone tool into a central hub for academic productivity.

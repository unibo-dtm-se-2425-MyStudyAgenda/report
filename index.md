---
title: Home
layout: home
has_children: false
nav_order: 1
---


# MyStudyAgenda

### Author
- [Anna Campagna](mailto:anna.campagna3@studio.unibo.it)

## Abstract

MyStudyAgenda is a desktop application developed to address the organizational challenges faced by students in higher education. In an academic environment characterized by fragmented deadlines and complex schedules, this project provides a centralized, offline-first solution for task management and academic planning. Developed using the Python programming language and the Kivy/KivyMD framework, the application delivers a responsive user interface that remains consistent across Windows, macOS, and Linux operating systems.

From a technical perspective, the project was designed following a modular architectural pattern, separating the concerns of data persistence, business logic, and graphical representation. Data integrity is maintained through a local SQLite database, ensuring that user information remains private and accessible without the need for an active internet connection. This architectural choice prioritizes reliability and low-latency interaction, which are critical for a daily productivity tool.

A significant portion of the project’s development was dedicated to establishing a professional-like DevOps lifecycle. Despite being a solo-contributor project, a robust CI/CD pipeline was implemented using GitHub Actions. The Continuous Integration (CI) suite automatically validates the codebase across a matrix of three operating systems and three Python versions (3.10, 3.11, and 3.12), utilizing Poetry for deterministic dependency management. Furthermore, the project features an automated Continuous Deployment (CD) workflow that packages the application and publishes versioned releases to TestPyPI upon the creation of Git tags.

The development process also involved navigating the complexities of automated GUI testing in headless environments. While logic-based unit testing achieved high stability, the integration of Kivy-based graphical tests through Xvfb provided significant insights into the challenges of hardware-accelerated rendering within cloud-based runners. Ultimately, MyStudyAgenda stands as a demonstration of modern software engineering practices, bridging the gap between functional application design and automated infrastructure management. It serves as a stable, extensible foundation for future developments, including cloud synchronization and web-based portability.

## Disclaimer

During the preparation of this work, the author used ChatGPT for code generation. 

The tool was used mainly for GUI design, since it was the author's first experience with Kivy/KivyMD framework. Also some UI's functions were implemented with the use of artificial intelligence.

Moreover, ChatGPT was consulted when the author encountered the first issues with CI, after developing the view part of the project's architecture. However, no suggestion provided by the tool proved to be 100% effective.

All the suggestions provided by AI were reviewd, adapted and validated by the author, who takes full responsibility for the final implementation and for the accuracy and completeness of this report.


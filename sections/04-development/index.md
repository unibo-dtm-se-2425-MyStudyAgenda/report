---
title: Development
has_children: false
nav_order: 5
---

# Development

## DVCS

The project was entirely developed using Git and hosted on GitHub in a single branch (`main`).  
Since the author worked alone, there was no need for pull requests, merges, or branch management conventions.  

However, commit messages were written following the [Conventional Commits](https://www.conventionalcommits.org/) specification, ensuring clarity and consistency.  
This makes the development history easier to read and maintain, even for future developers.

## Implementation details

- **Network protocols**: The application runs locally on the user’s machine and does not rely on any network communication. Therefore, no protocols such as HTTP or WebSockets were required.  

- **In-transit data representation**: Not applicable, since no network communication is involved.  

- **Database queries**: The application uses SQLite as its persistence layer, accessed through SQL queries. This choice was made because SQLite is lightweight, embedded, and does not require a separate server, making it suitable for a desktop application.  

- **Authentication & Authorization**: Not applicable, since the application does not involve user accounts or remote access. All data is stored locally on the user’s machine.

## Technological details

- **Programming language**: The software was developed in **Python**, due to its readability, wide adoption in education, and strong ecosystem for GUI development and testing.

- **Frameworks and libraries**:  
  - **Kivy** and **KivyMD**: for building the cross-platform desktop GUI with a modern look and feel.  
  - **SQLite**: for local data persistence.  
  - **unittest / pytest**: for testing the application components.

- **Tools**:  
  - **Visual Studio Code**: as the main development environment.  
  - **GitHub**: for version control and hosting the repository.  

- **External dependencies**: None. The application is entirely self-contained and does not rely on external APIs or third-party services.

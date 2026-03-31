---
title: Concept
has_children: false
nav_order: 2
---

# Concept

**MyStudyAgenda** is a desktop application designed to support students in organizing their academic activities and improving their weekly study routine.  
The software provides a graphical user interface (GUI) that allows users to plan tasks, manage notes, and use a built-in Pomodoro timer to structure study sessions.

### Product Type
- Type: Desktop application with GUI  
- Target users: University students and, in general, individuals who want to keep track of daily activities improving their time management 
- Environment: Runs locally on the user’s machine, without requiring network connectivity or authentication  

### Use Case Collection
- **Where are the users?**  
  Typically at home, in the library, or any environment where a computer is available (possibly theirs if they have already used the software before or plan on using it again in the future).  

- **When and how frequently do they interact with the system?**  
  Users may interact with the application daily or several times a week, especially when planning their tasks, revising notes, or managing study sessions.  

- **How do they interact with the system?**  
  Through a desktop GUI, using mouse and keyboard. No mobile or web interface is currently supported.  

- **Does the system need to store user data? Which data? Where?**  
  Yes. The application stores:    
  - Tasks (description, priority, associated topic, completion status, scheduled date and time) 
  - Notes (titles, content, associated topic) 
  - Topics (labels to categorize tasks and notes)  
  
  All data is stored locally in a SQLite database bundled with the application. No external storage or synchronization is performed.  

- **Roles**  
  The system supports a *single user role*: the student. There is no distinction between different types of users, nor any multi-user functionality.  Thus, the user doesn't need to authenticate to the application to use it.

---
title: Self-evaluation
has_children: false
nav_order: 12
---

# Self-evaluation

## Anna Campagna

As the sole contributor to *MyStudyAgenda*, I was responsible for the entire software development lifecycle, including requirements analysis, system design, implementation, testing, and documentation. The project required managing all aspects of development, from designing the graphical user interface with Kivy to implementing data persistence through SQLite and automating CI/CD workflows using GitHub Actions. Working independently ensured a consistent vision throughout the project, although it also required careful planning and self-review to compensate for the absence of peer feedback.

One of the main strengths of the project is its focus on maintainability and portability. The adoption of Poetry for dependency management and the configuration of automated testing across multiple operating systems and Python versions contributed to a more robust and reproducible development process.

A significant technical challenge emerged during the implementation of the CI pipeline. While all tests completed successfully on Ubuntu and macOS runners in under one minute, the Windows workflow consistently exceeded GitHub Actions' execution time limit and was terminated after 30 minutes. Another challenge was encountered during the deployment phase. Some solutions that worked correctly in the local development environment initially failed after packaging and installation. Resolving these issues required additional debugging and adjustments to ensure that the application functioned correctly when distributed to end users.

Looking back, one aspect that could have been improved is the Git workflow. Although version control was used throughout the project, a more structured branching strategy—such as developing new features and fixes in dedicated branches before merging them into the main branch—would have resulted in a cleaner and more maintainable project history.

Overall, this project represented a valuable learning experience. It strengthened both my technical skills and my understanding of software engineering practices, particularly in testing, deployment, dependency management, and project organization. While there are still opportunities for further refinement and additional features, I am satisfied with the final outcome and the objectives achieved.

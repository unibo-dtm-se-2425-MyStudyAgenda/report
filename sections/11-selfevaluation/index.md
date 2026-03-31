---
title: Self-evaluation
has_children: false
nav_order: 12
---

# Self-evaluation

## Anna Campagna
As the sole contributor to MyStudyAgenda, my role encompassed the entire software development lifecycle, serving as the lead architect, developer, and QA engineer. This required managing everything from the initial requirements and UI design in Kivy to the implementation of a local SQLite persistence layer and the automation of CI/CD pipelines using GitHub Actions. Being responsible for both the codebase and the comprehensive technical report allowed for a unified vision, but it also necessitated a high degree of self-discipline to ensure every detail was addressed without the benefit of peer review.
 
The primary strength of the final product lies in its robust dependency management and cross-platform architecture. By using Poetry and targeting multiple Python versions, I ensured the application remains stable across different environments. However, a significant technical challenge arose during the implementation of the CI/CD pipeline: the integration of automated GUI tests. While the logic-based unit tests perform as expected across all platforms, the GUI tests (which require a virtual display environment via Xvfb9) encountered persistent execution errors in the GitHub Actions runner. Despite multiple attempts to reconfigure the environment variables and display drivers, the GUI workflow remains inconsistent. I have chosen to document this as a known limitation, prioritizing the stability of the core application over an unreliable test suite.

This experience proved to be an invaluable learning process that highlighted the importance of "double-looking" at every detail. Navigating the complexities of headless GUI testing and managing versioned releases solo taught me to never take configuration for granted. While there is always room for further development—such as resolving the virtual display conflicts or enhancing the user interface—I am satisfied with the current result.
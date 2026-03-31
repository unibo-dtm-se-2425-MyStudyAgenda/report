# MyStudyAgenda Final Report

[This repository](https://github.com/unibo-dtm-se-2425-MyStudyAgenda/report) contains the project documentation related to MyStudyAgenda, a software made by students (as part of a Software Engineering coursework assignment) for students, to assist them with time management and deadlines organization.

You can visualize the project work documentation [here](https://unibo-dtm-se-2425-mystudyagenda.github.io/report/).

To access the project's artifact, click [here](https://github.com/unibo-dtm-se-2425-MyStudyAgenda/artifact).

To access the template used for this report, click [here](https://github.com/unibo-dtm-se/template-project-work).

## How to visualise a preview of the report, locally

You need to install __Ruby__ on your machine (instructions below).

1. Assuming that Ruby is correctly installed, you need to clone your report repository on your machine:
    
    ```bash
    git clone https://github.com/unibo-dtm-se-2425-MyStudyAgenda/report
    ```

2. Then, you need to restore Jeckyll's dependencies.
From within the root of your repository, run the following command:

    ```bash
    bundler install
    ```


3. Finally, you may run the following command from the root of your repository:

    ```bash
    bundler exec jekyll serve
    ```

    The output of that command should tell you the local URL where the preview of your site is available.
    Most commonly, it will be <http://127.0.0.1:4000>.

4. Open your browser, and navigate to the URL provided by the previous command
    + from now on, until you stop the `bundler exec jekyll serve` command, any change you make to the `.md` files will be automatically reflected in the preview
    + you may stop the preview by pressing `Ctrl+C` in the terminal

## How to install Ruby and Jekyll

Follow instructions from here: <https://jekyllrb.com/docs/installation/>

<!-- References -->

[template-repo]: https://github.com/unibo-dtm-se/template-project-work
[template-site]: https://unibo-dtm-se.github.io/template-project-work
[course-site]: https://www.unibo.it/en/study/phd-professional-masters-specialisation-schools-and-other-programmes/course-unit-catalogue/course-unit/2024/466765
[general-forum]: https://virtuale.unibo.it/mod/forum/view.php?id=1885625
[project-forum]: https://virtuale.unibo.it/mod/forum/view.php?id=1885626
[markdown-cheatsheet]: https://www.markdownguide.org/cheat-sheet
[jeckyll-home]: https://jekyllrb.com/

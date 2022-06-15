# Non-Hierarchical Forms

There are some use case where there is the need to have multiple forms on the same project but the hierarchy structure does not fit. Maybe the forms are not related or it just does not make sense for the project.

There are a couple of way to tackle this.

1. Separate the project in multiple ones
2. Use a single form with either BRANCH(es) or GROUP(s)

## 1 - Multiple projects

The simplest way would be having multiple projects, one with a single form each. Usually, a "_base_" project gets created first then it gets [cloned](../web-application/clone-project.md) or [shared](../web-application/import-and-export-projects.md) multiple times.

The name for each project might reflect what the projects are different on, which could be the period of the data collection (like year or month), the groups of users it targets, the area or the country of the data collection and so on.

Each data set is downloaded separately as multiple `csv` files which be merged in the post-processing of data using your favorite third party tool.

This is the approach we would recommend.

## 2 - Single project with BRANCH or GROUP sub-forms

If having multiple projects is not an option, there are ways to implement it with either BRANCH(es) or GROUP(s).

We built a couple of examples for anyone to view and play around with:

* [EC5 Multiple non hierarchical forms GROUP](https://five.epicollect.net/project/ec5-multiple-non-hierarchical-forms-group)
* [EC5 Multiple non hierarchical forms BRANCH](https://five.epicollect.net/project/ec5-multiple-non-hierarchical-forms-branch)

The project definition files (to import each project and see how it is done) are available here:

* [EC5 Multiple non hierarchical forms GROUP project definition](https://drive.google.com/file/d/1nSZmoIuJIotILvxNFF25SW0wmnc8-Mz8/view)
* [EC5 Multiple non hierarchical forms BRANCH project definition](https://drive.google.com/file/d/1eoTOWonDe0\_Bxz722QoPPY-sF8fxhdrc/view)

The projects are very similar. There is a single hierarchy form called "_Citizen_" which has a pivot question at the beginning to pick which one of the sub-forms (BRANCH or GROUP) the user will want to fill. [JUMPS](../formbuilder/jumps.md) are used to build the logic flow so the users will never see questions they are not supposed to answer.

The choice of using BRANCH or GROUP depends on the project requirements and preferences. The main differences are as follows.

* BRANCH allows JUMP(s) between question, GROUP(s) do not
* BRANCH(es) data gets downloaded as separate files, one per each BRANCH. GROUP(s) data is a single file.

Feel free to give it a try using the example above. If you have any questions about these approaches do not hesitate to post it on our [**community**](https://spectrum.chat/epicollect5)!

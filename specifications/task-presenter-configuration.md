# Task Presenter Configuration

## I. Introduction

Creating a [task presenter](http://docs.pybossa.com/en/latest/overview.html#task-presenter) for your PyBossa project requires prior knowledge of the Hypertext Markup Language (HTML), JavaScript, and/or Cascading Style Sheets (CSS). These programming languages are relatively simple to learn however the creation process can be very time-consuming depending on the size and scope of a project. To mitigate this issue, the PyBossa platform provides a set of pre-built templates that can be used as foundations for new project task presenters.


However, there are a few drawbacks to using the template approach:

- Templates provide a basis comprised of HTML, JavaScript and possibly CSS code, which still needs to be tweaked to a task presenter's specific needs. This can be a very problematic and error-prone step for project creators with little to no knowledge of these programming languages.

- Any improvements or fixes made to a template will have to be made to all task presenters based on that template, which can quickly become a maintenance nightmare.

- A template should strive to be as simple as possible so as not to overwhelm project creators, however the scope of a specific type of project may warrant a complex task presenter.


As an alternative to the task presenter template, this document will introduce the *task presenter configuration*, a well-defined format that aims to resolve the aforementioned shortcomings by describing how a task presenter should behave under certain conditions rather than focusing on its implementation.

Ultimately, it is our hope that by providing tools to manage task presenter configurations as well as generate HTML, JavaScript and CSS code from them, the creation process becomes simpler and much quicker since project creators can focus more on the content of their projects without having to worry about technical details.



## II. Data Format

For the purpose of this specification, the task presenter configuration will adhere to the JavaScript Object Notation (JSON) format.



## III. General Layout



## IV. Task Presenter Language
### IV.1. Default Language
### IV.2. Available Languages

## V. Task Presenter Subject
### V.1. Subject Reminder
### V.2. Subject Type

## VI. Task Presenter Questionnaire
### VI.1. Questionnaire Index
### VI.2. Questions



#### VI.2.a. Keys

A key is a unique non-empty string that identifies a question composed strictly of alphanumeric characters (a-Z, A-Z, 0-9), hyphens (-) or underscores (_).

Keys that begin with an underscore, e.g. `_end`, `__next`, or even `_`, are reserved for internal use and are therefore invalid question keys.



#### VI.2.b. Titles
#### VI.2.c. Help
#### VI.2.d. Input
#### VI.2.e. Control Flow

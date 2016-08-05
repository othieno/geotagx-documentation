# CONFIGURATION SPECIFICATIONS

## I. Introduction

Creating a GeoTag-X project requires prior knowledge of the HTML (Hypertext Markup Language), JavaScript, and/or CSS (Cascading Style Sheets) programming languages. Depending on the size and scope of a project, the creation process can be very time-consuming, error-prone, even nigh impossible for anyone with little to no knowledge of the aforementioned languages.

To help project creators, the PyBossa platform provides pre-built templates for different use-cases that can be used as a foundation for new projects.

So why not create a template for geotagx projects? This is not an absured idea as geotag-x projects have an identical look and feel, distinct only in their questions and their subjects (photos, videos, audio).

however, with a template, a project creator would still have to edit the html to suit their project

if a template is modified (bug fixes, improvements, etc.), every single project would need to make the same modifications in their projects



while this approach makes sense for general-purpose crowdsourcing projects, it doesn't really bode well in the case of geotag-x as most projects are only distinct in their questions, all the while retaining an identical look-and-feel.




however geotagx projects are very identical, safe the questions
and while we can copy a template of an already working project, editing it can be somewhat tedious.






As an alternative to the HTML, JavaScript and CSS trio, this document will introduce a set of simpler, well-defined specifications, namely
- the **project configuration** specification,
- the **task presenter configuration** specification, and
- the **tutorial configuration** specification.

By providing tools that can generate HTML, JavaScript and CSS code from these specifications, the creation process becomes simpler and much quicker since project creators no longer need to worry about technical details, and can focus more on the content of their projects.



## II. Project Configuration

The project configuration--based on the classic PyBossa project configuration--has been extended to include a new `repository` property in addition to the required `name`, `short_name`, and `description` properties.


### II.1. Project Repository

This is an optional property that provides a URL to a project's version control repository.

```json
{
    "name": "Demo project",
    "short_name": "demo",
    "description": "A demo project.",
    "repository": "https://github.com/geotagx/geotagx-project-demo.git"
}
```


Add a description_lc since we can't modify the description



## III. Task Presenter Configuration

### III.2. Questionnaire
A questionnaire is a list of entries (questions) where each is comprised of
* a **unique key** to identify the question
* the question's **title**
* a short **hint** that may dispel any ambiguities about the question
* a more detailed explanation to **help** clarify the question
* a set of **input parameters** that determine the type of input expected by the question as well as any constraints that may be placed on said input
* **branch parameters** to determine the next question


### III.2.b. Question Titles
A question title is the actual question that will be presented to a user. It must be a non-empty string, or [normalized][normalized_string] in the case of a multilingual questionnaire.

A simple question title may look like:
```json
"title": "What is the color of the sky today?"
```

When normalized, the previous example may look like
```json
"title": {
    "en": "What is the color of the sky today?",
    "fr": "Quelle est la couleur du ciel aujourd'hui?"
}
```


### III.2.c. Question Hints
[OPTIONAL]

For questions that may be open to interpretation, a hint is usually a concise way to quickly dispel any ambiguity. Just like a question title, a hint may be a non-empty string or normalized.


### III.2.d. Question Help
[OPTIONAL]

### III.2.e. Input parameters

**[TODO] Introduce question input parameters**


#### III.2.e.1. Polar

A polar (yes–no) question is a question with an answer that is expected to be either *Yes* or *No*. A polar input has no configurable properties.

```json
"input": {
    "type": "polar"
}
```


#### III.2.e.2. Dropdown List

A dropdown list allows you to pick a single value from a set of available choices. The following properties can be configured:

- ***prompt*** (`String | Object`): This is an optional message that invites a user to interact with the dropdown list, e.g. "Please select an option". It must be a non-empty or normalized string. The prompt, if set, will always be the dropdown list's first option, albeit unselectable.
- **options** (`Array`): A list of one or more available options, or groups of options, that a user can select from.

**[TODO] Document options and grouped options**

Here's an example of how to set up a dropdown list:
```json
"input": {
    "type": "dropdown-list",
    "prompt": "Please select a color",
    "options": [
        {
            "label": "Primary Colors",
            "options": [
                {
                    "label": "Red",
                    "value": "RED"
                },
                {
                    "label": "Yellow",
                    "value": "YELLOW"
                },
                {
                    "label": "Blue",
                    "value": "BLUE"
                }
            ]
        },
        {
            "label": "Secondary Colors",
            "options": [
                {
                    "label": "Green",
                    "value": "GREEN"
                },
                {
                    "label": "Purple",
                    "value": "PURPLE"
                },
                {
                    "label": "Orange",
                    "value": "ORANGE"
                }
            ]
        },
        {
            "label": "Cyan",
            "value": "CYAN"
        },
        {
            "label": "Magenta",
            "value": "MAGENTA"
        },
        {
            "label": "Black",
            "value": "BLACK"
        }
    ]
}
```

The example above is equivalent to writing the following HTML code:
```html
<select>
    <option role="prompt" selected disabled>Please select a color</option>
    <optgroup label="Primary Colors">
        <option value="RED">Red</option>
        <option value="YELLOW">Yellow</option>
        <option value="BLUE">Blue</option>
    </optgroup>
    <optgroup label="Secondary Colors">
        <option value="GREEN">Green</option>
        <option value="PURPLE">Purple</option>
        <option value="ORANGE">Orange</option>
    </optgroup>
    <option value="CYAN">Cyan</option>
    <option value="MAGENTA">Magenta</option>
    <option value="BLACK">Black</option>
</select>
```


#### III.2.e.3. Multiple Choice

```json
"input": {
    "type": "multiple-choice",
    "allow-multiple-answers": true,
    "allow-other-option": true,
    "illustrative": false,
    "options": [


    ]
}
```


#### III.2.e.4. Text
```json
"input": {
    "type": "text",
    "placeholder": String | Object,
    "longtext": Boolean,
    "min-length": Number,
    "max-length": Number
}
```


#### III.2.e.5. Number
```json
"input": {
    "type": "number",
    "placeholder": String | Object,
    "min": Number,
    "max": Number
}
```


#### III.2.e.6. Date and Time
```json
"input": {
    "type": "datetime",
    "format": String,
    "from": String,
    "to": String,
    "date-only": Boolean,
    "time-only": Boolean
}
```


#### III.2.e.7. URL
```json
"input": {
    "type": "url",
    "placeholder": String | Object,
    "domain": String,
    "max-length": Number
}
```


#### III.2.e.8. Geotagging
```json
"input": {
    "type": "geotagging",
    "location": String
}
```


### III.2.f. Question branches
[OPTIONAL]




## IV. Tutorial Configuration

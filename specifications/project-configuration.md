# Project Configuration

## I. Introduction

The project configuration--based on the classic PyBossa project
configuration--has been extended to include a few properties in
addition to the required `name`, `short_name`, and `description`
properties. For a more thorough description of the project
configuration, please refer to the [PyBossa](http://docs.pybossa.com/en/latest/user/overview.html) documentation.

A minimal project configuration may look like the following

```json
{
    "name": "Demo project",
    "short_name": "demo",
    "description": "A simple demo project."
}
```



## II. Data Format

PyBossa's project configuration files adhere to the JavaScript
Object Notation (JSON) format. This remains unchanged.



## III. Additional Properties

The following optional properties have been added to the project configuration:
- a **repository** URL to the project's version control repository
- a **track** flag that toggles project-specific analytics tracking


### III.1. Project Repository

With this property, a project creator may specify a URL to their project's
version control repository. Such a URL may be useful in cases where the creator
would consider contributions to the project from a larger community.

```json
{
    "name": "Demo project",
    "short_name": "demo",
    "description": "A simple demo project.",
    "repository": "https://github.com/geotagx/geotagx-project-demo.git"
}
```

If unspecified, this property is assumed to be `null`.


### III.2. Analytics Tracking

To improve user experience, GeoTag-X tracks the way users interact with
the platform in order to find areas likely to cause confusion. While
useful, tracking projects that are still under heavy development may not
provide any actionable data.

To disable tracking for a specific project, set the `track`
property to `false`

```json
{
    "name": "Demo project",
    "short_name": "demo",
    "description": "A simple demo project.",
    "repository": "https://github.com/geotagx/geotagx-project-demo.git",
    "track": false
}
```

If unspecified, this property is assumed to be `true`.

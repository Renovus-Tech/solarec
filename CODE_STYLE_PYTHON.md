# Code Style Guidelines for Python

This document outlines the React code style and best practices to be followed in the [Renovus Solarec Python]((https://github.com/Renovus-Tech/solarec-python)) repository. The repository might have its own code styles, but it follow these guid as base.

## Table of Contents

1. [Indentation and Whitespace](#identation-and-whitespace) 
2. [Imports](#imports) 
3. [Naming Conventions](#naming-conventions) 
4. [Comments and Docstrings](#comments-and-docstrings) 
5. [Spacing in Expressions and Statements](#spacing-in-expressions-and-statements) 
6. [Limitation on Assignments](#limitation-on-assigments) 
7. [Testing](#-testing) 
8. [Error Handling](#error-handling) 
9. [Virtual Environment](#virtual-environment) 

## Indentation and Whitespace

Use 4 spaces for indentation.
Avoid tabs; use spaces consistently.
Limit lines to 79 characters for code and 72 for docstrings.

## Imports

Use explicit imports and avoid wildcard imports (from module import *).
Group imports in the following order: standard library imports, third-party imports, and then local imports.

```
import os
import sys

from external_library import foo
from local_module import bar
```

## Naming Conventions

Use snake_case for function and variable names.
Use CamelCase for class names.
Avoid single-letter variable names except in cases like iterators (i, j, k).

## Comments and Docstrings

Write docstrings for modules, classes, and functions.
Use comments sparingly and focus on explaining complex parts of the code.

```
def add_numbers(a, b):
    """Add two numbers."""
    return a + b
```

## Spacing in Expressions and Statements

Use a space after commas in lists, tuples, and function arguments.
Avoid extraneous whitespace in the following situations:

```
# Good
spam(ham[1], {eggs: 2})
# Bad
spam( ham[ 1 ], { eggs: 2 } )
```

## String Quotes

Use single quotes for string literals unless the string contains a single quote.

```
name = 'John Doe'
```

## Limitation on Assignments

Avoid multiple assignments in a single line.

```
# Good
a = 1
b = 2
# Bad
a, b = 1, 2
```

## Testing

Write unit tests for functions and classes using a testing framework (e.g., pytest).
Follow the naming convention for test files (e.g., test_module.py).

```
def test_add_numbers():
    assert add_numbers(1, 2) == 3
```

## Error Handling

Use explicit exception handling rather than a generic except clause.
Handle specific exceptions whenever possible.

```
try:
    # some code that might raise an exception
except ValueError as ve:
    # handle ValueError
except Exception as e:
    # handle other exceptions
```

## Virtual Environment

Use virtual environments (e.g., venv, virtualenv) to manage project dependencies.

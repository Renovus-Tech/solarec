# Code Style Guidelines for Python

## Indentation and Whitespace:

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

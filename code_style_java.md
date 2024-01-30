## Java Coding Standards

This document outlines the React code style and best practices to be followed in the [Renovus Solarec Java]((https://github.com/Renovus-Tech/solarec-java)) repository. The repository might have its own code styles, but it follow these guid as base.

Use meaningful variable and method names.
Follow Java naming conventions for classes, methods, and variables.
Avoid redundant comments; write self-explanatory code.
Use static imports sparingly; prefer the class name for readability.

## Spring Boot Guidelines
Leverage Spring Boot's annotations for configuration, such as @Configuration, @Component, etc.
Utilize dependency injection with @Autowired and constructor injection.
Follow the principles of the Spring framework, such as inversion of control (IoC) and aspect-oriented programming (AOP).
Minimize the use of field injection; prefer constructor injection.

## Naming Conventions

### Packages
Use lowercase letters.
Use a reversed domain name as the prefix, e.g., com.example.project.

### Classes and Interfaces
Use CamelCase.
Choose clear, descriptive names that reflect the class or interface's purpose.

### Methods
Use camelCase.
Start with a verb that describes the action, e.g., getUserInfo().

### Variables
Use camelCase.
Choose descriptive names that convey the variable's purpose.

## Formatting
Use an indentation of four spaces.
Limit lines to 80 characters.
Maintain consistent and clear indentation.

## Documentation
Include Javadoc comments for all classes and public/protected methods.
Write clear and concise comments for complex sections of code.

## Testing
Write unit tests for all service and repository classes.
Use meaningful test method names.
Follow the Arrange-Act-Assert pattern in test methods.

## Conclusion
Consistent coding standards are crucial for the success of the project. All contributors are expected to follow these guidelines to ensure a unified and maintainable codebase.

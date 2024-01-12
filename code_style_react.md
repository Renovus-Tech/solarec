# Code Style Guidelines for React

## Component Structure

Organize components into a well-defined directory structure (e.g., src/components).
Follow the Single Responsibility Principle: Each component should have a single responsibility.
Use functional components by default and only use class components when necessary.
Naming Conventions:

## Use meaningful names for components.
Component names should be written in PascalCase.
File names should match the component name.

```
// Good
function UserProfile() { ... }
// File: UserProfile.js
```

## JSX Formatting
Use double quotes for JSX attributes.
Always self-close tags for components without children.
Use parentheses for multiline JSX.

```
// Good
<MyComponent prop="value" />
<AnotherComponent />
<MultiLineComponent
  prop1="value1"
  prop2="value2"
/>
```

## State and Props:
Destructure props when used in functional components.
Avoid modifying state directly; use setState for state changes.
Use prop-types to document and enforce prop types.

```
// Good
function MyComponent({ prop1, prop2 }) {
  // ...
}
```

## CSS Styling:
Use a consistent CSS naming convention (e.g., BEM).
Consider using CSS-in-JS libraries or styled-components for component styling.

## Documentation:
Include a brief description and usage example for each component.
Clearly document props and their types.
Include any necessary setup or configuration details in the documentation.

```
/**
 * `UserProfile` component displays user information.
 *
 * @component
 * @example
 * <UserProfile username="john_doe" />
 *
 * @param {string} username - The username of the user.
 */
function UserProfile({ username }) {
  // ...
}
```

## State Management:
Prefer using state management libraries like Redux for global state.
Keep local component state for simple, local interactions.

## Testing:
Write unit tests for components using testing libraries like Jest and React Testing Library.
Follow naming conventions for test files (e.g., MyComponent.test.js).

## React Hooks:
Use hooks like useState, useEffect, and useContext as appropriate.
Avoid using hooks conditionally; they should be called at the top level of a functional component.

// Good
function MyComponent() {
  const [value, setValue] = useState('');
  // ...
}


Version Control:

Use meaningful commit messages.
Follow a consistent branching strategy (e.g., feature/feature-name).

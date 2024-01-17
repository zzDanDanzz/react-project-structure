# react-project-structure

react project structure with no meta-framework (e.g. next.js)

### Rules

- avoid useEffect unless trying to synchronize react state with an EXTERNAL system.
- use existing tools and libraries instead of reinventing every wheel.
  - choose a component library AND STICK TO IT. (e.g. mantine)
  - choose an icons library AND STICK TO IT. (e.g. tabler icons for react)
    - avoid adding SVGs to your source code (unless you REALLY HAVE to use a custom svg)

### Tips

- get to a stable version of your component, and ONLY THEN consider animations and fancy stuff IF you have the time.
- when your state is an object with nested objects, use use-immer instead of useState.

---

### Naming Conventions

- all files and folders: kebab-case
- constants: ALL_CAPS
- components and classes: PascalCase

### Files and Folder

["React also uses tree structures to manage and model the relationship between components in a React app. These trees are useful tools to understand how data flows through a React app"](https://react.dev/learn/understanding-your-ui-as-a-tree) - so with the project structure below I'm trying to make it easier to understand how data flows.

#### Pages Folder

> Group related code together in dedicated folders for each page, keeping all components, hooks, and utilities nearby

- pages/
  - {{page-name}}/
    - components/
      - {{component-name}}/
        - {{component-name}}.tsx
        - hooks/
          - use-{{hook-name}}.ts
        - context/
          - {{context-name}}.provider.ts
          - use-{{context-name}}.provider.ts
        - utils/
          - {{utility-name}}.ts
        - etc…
    - hooks/
      - use-{{hook-name}}.ts
    - {{page-name}}.page.tsx

#### Shared Folder

> For code that is shared across multiple pages, we have the 'shared' folder.

- shared/
  - components/
    - {{component-name}}/
      - …repeat above component structure
  - hooks/
    - use-{{hook-name}}.ts
  - constants/
    - e.g. shared urls, config, etc.
  - utils/
    - {{utility-name}}.ts

> the project entry file

- main.ts

> routes declaration (can only import the .page.tsx export from pages folder)

- routes.ts

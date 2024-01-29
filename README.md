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

---

### Files and Folder

- ["React also uses tree structures to manage and model the relationship between components in a React app. These trees are useful tools to understand how data flows through a React app"](https://react.dev/learn/understanding-your-ui-as-a-tree) - so on the one hand, 'nesting' your files to follow the actual react tree structure makes sense ...
- HOWEVER, too much nesting is also visually complex so let's keep the nesting 3 levels deep by making major separations of concern through the pages, features, and shared folder.
- and we will keep our directories flat where possible. e.g. keep all the code of a component in one file where possible.

#### Repeatable Structure

think of this as a variable that can be reused.

```
{{REPEATABLE_STRUCTURE}}
├─ hooks/
│  └─ use-{{hook-name}}.ts
├─ context/
│  ├─ {{context-name}}.provider.ts
│  └─ use-{{context-name}}.provider.ts
└─ utils/
   └─ {{utility-name}}.ts
```

#### Pages Folder

1. create a separate folder for each page, with a main export called `{{page-name}}.page.tsx`
2. the `components` folder will contain the components used ONLY in that page.
3. the `{{REPEATABLE_STRUCTURE}}` will contain hooks, context, utils, etc, ONLY __shared__ by components in that page

```
pages/
└─ {{page-name}}/
   ├─ components/
   │  └─ {{component-name}}.tsx
   ├─ {{REPEATABLE_STRUCTURE}}
   └─ {{page-name}}.page.tsx
```

#### Features Folder

- here, we keep `features` that are part of a page but have grown so complex that can have their own `page` structure (but they're not conceptually a page)

- the `features` folder follows the same structure as the `pages` folder except that everywhere you see _page_ or _pages_ you replace it with _feature_ or _features_.

```
features/
└─ {{feature-name}}/
   ├─ components/
   │  └─ {{component-name}}.tsx
   ├─ {{REPEATABLE_STRUCTURE}}
   └─ {{feature-name}}.feature.tsx
```

#### Shared Folder

- the `shared` folder is for code that is _shared_ across *multiple* `pages` and/or `features`

```
shared/
├─ components/
│  └─ {{component-name}}.tsx
└─ {{REPEATABLE_STRUCTURE}}
```

#### Misc

the project entry file:

`main.ts`

routes declaration (can only import the .page.tsx export from pages folder):

`routes.ts`

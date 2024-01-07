# react-project-structure

### Rules
* avoid early optimization (value code readability over millisecond performance benefits)
* it's ok to repeat code TWICE. don't follow D.R.Y. too early.
* avoid useEffect unless trying to synchronize react state with an EXTERNAL system. 
* use existing tools and libraries instead of reinventing every wheel.
* let prettier / eslint plugins do your formatting and don't override the project's prettier / eslint config. (bonus: enable format-on-save in your editor)


________________




### Files and Folder


> For each page we create a folder and sub-folder containing the main export, components, and hooks that belong to that page.


* pages/
   * example-page/
      * components/
         * example.component/
            * example.component.tsx
            * example.hooks.tsx
            * example.utils.tsx
            * example.constants.tsx
            * example.context.tsx
            * etc…
      * hooks/
         * use-example-hook.ts
      * example.page.tsx


Some components / hooks need to be shared between multiple pages, we place those in the shared folder. 


* shared/
   * components/
      * example.component/
         * …repeat component structure
   * hooks
      * use-example-hook.ts
   * layouts
      * home-layout/
         * …repeat component structure


the project entry file
* main.ts


routes declaration (can only import the .page.tsx export from pages folder)
* routes.ts

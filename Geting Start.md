# Developer Documentation for Nuxt 3 Project

<img src="./files/Nuxt Stucture.png" width="500px" />

## Introduction
This document provides comprehensive guidance for developers working on a Nuxt 3 project. Nuxt 3 is a modern framework built on Vue.js, leveraging Vite for development and Nitro for server-side capabilities. This documentation covers project setup, structure, naming conventions, and usage of helpers, cookies, and API integrations to ensure a smooth development experience.

## Prerequisites
- **Node.js**: Version 20.x or newer (active LTS recommended).
- **Text Editor**: Visual Studio Code with extension:
  - Code Spell Checker
  - Vue (Official)
  - Nuxtr
  - Tailwind Snippets
  - GitHub Copilot
  - ESLint
  - Auto Rename Tag
- **Git**: For version control.
- **Knowledge**: Familiarity with HTML, CSS, SCSS, JavaScript, Vue.js, and Node.js.

## Project Setup
Follow these steps to set up the project locally:
1. **Install Dependencies**:
   ```bash
   npm install
   ```
2. **Run the Project**:
   - Development: `npm run dev`.
   - Production build: `npm run generate`.
   - Production build for HCS: `npm run generateHcs`.
   - Production deploy `bash deploy.sh`
3. **Note**: On Windows, use WSL for faster HMR if performance is slow.

## Project Structure
The project follows a modular structure for scalability and maintainability:
Example directory structure:
```plaintext
project-root/
├── assets/
│   ├── lang/
│   │   └── km.json
│   │   └── en.json
│   ├── json/
│   │   └── studentType.json
│   │   └── item.json
├── components/
│   ├── mainModule/
│   │   ├── subModule/
│   │   │   └── HeaderComponent.vue
├── composables/
│   ├── mainComposable/
│   │   ├── subComposable/
│   │   │   └── useAuth.ts
├── pages/
│   ├── main_page/
│   │   └── sub_page.vue
├── stores/
│   ├── mainStore/
│   │   └── subStore.ts
├── helpers/
│   │── apis.js
│   └── str.js
├── public/
│   ├── _kedtec/
│   │   │── img
│   │   │   └── file.png
├── utils/
└── nuxt.config.ts
```

## Naming Conventions
Adhere to the following naming conventions for consistency:

- **Page Names**: Use snake_case (e.g., `home_page.vue`, `user_profile_page.vue`).
- **Component Names**: Use PascalCase (e.g., `HeaderComponent.vue`, `UserCardComponent.vue`).
- **Composable Names**: Use camelCase with `use` prefix (e.g., `useAuth.ts`, `useFetchData.ts`).
- **Utility Names**: Use camelCase (e.g., `formatDate.js`, `parseJson.js`).
- **Store Names**: Use camelCase (e.g., `userStore.ts`, `cartStore.ts`).
- **Folder Names**: Use camelCase, excluding `page` (e.g., `productDetail`, not `productDetailPage`).
- **Other Files**: Use camelCase (e.g., `configSettings.ts`, `apiClient.ts`).
- **Variable Names**: Use camelCase (e.g., `variableName`).

## Key Features and Workflows

### Routing
Nuxt 3 uses file-based routing. Pages are defined in the `pages/` directory:
- `pages/home_page.vue` → `/home`
- `pages/product_detail/[id].vue` → `/product_detail/:id` (dynamic route)

### State Management
Corrected Prompt: "Use Pinia for state management. Name the file the same as the function name, e.g., `useCount.js`. Note: Do not create a single file in a single folder."
- File name: `useCount.js`
- Function name: `useCountStore`
- Key name: `CountStore`
```text
stores/
│     └── useCount.js
```
```javascript
// stores/mainStore/countStore.ts
export const useCountStore = defineStore('CountStore', {
    state: () => ({
        data: 0
    }),
    getters: {
        getData: (state) => state.data,
    },
    actions: {
        setData() {
            this.data++
        }
    }
})

if (import.meta.hot) {
    import.meta.hot.accept(acceptHMRUpdate(useCountStore, import.meta.hot));
}
```

### Middlewares
```javascript
definePageMeta({
  middleware: ["auth", "permission"],
  ...
});
```

### Layouts
This note explains how to implement layouts in a Nuxt.js application, focusing on the default and navbar layouts. Layouts define the structure of pages, allowing consistent rendering of components like navigation bars across multiple pages.
- `default` - No navbar
- `navbar` - With list of menu
```javascript
definePageMeta({
  ...
  layout: 'navbar'
});
```

### Breadcrumb
A list of links that indicate the current page's location within a navigational hierarchy.

### Calling API
Use with useHttp

- **Url**: Specifies the endpoint for the API request.
  - Relative path: `/api/somepath` (e.g., for local or same-origin requests).
  - Absolute URL: `https://domain.com/api/somepath` (e.g., for external APIs).
- **Options**: 
  - `method`: Specifies the HTTP method for the request.
    - `GET` or `POST` (case-insensitive).
  - `data`: The payload to send with the request.
  - `headers`: Custom headers to include in the request.
  - `isGlobal`:
    - Set to true for requests that do not require authentication and can be shared across the application (e.g., public API endpoints).
    - Set to false for requests that require authentication and are specific to a user login.
  - `isWeb`: Indicates if the request is made to a web-based URL.
  - `alertError`: Controls whether to display an error alert on request failure.
  - `alertSuccess`: Controls whether to display a success alert on request completion.
  - `signal`: An AbortSignal to cancel the request if needed.
```javascript
const { data, error } = await useHttp(apis.studyClass, {
  method: "POST",
  data: filter,
  ...
});
```
Cancel the request
```javascript
// At the top
const controller;

// Calling api
controller = new AbortController();
const { data, error } = await useHttp(apis.studyClass, {
  method: "POST",
  data: filter,
  signal: controller.signal,
  ...
});

// to cancel the request
controller.abort();
```

## Using Data Across Pages
This guide explains how to share and use data across pages in a web application, focusing on two primary methods: dynamic pages and query strings. These approaches are useful for passing data between pages, ensuring seamless user experiences while maintaining authentication and permission checks as described in the API Usage Guide.
- **create dynamic routes**(pages/user/:id)
- **queryParams**:  key (string) and value (object) `queryParams(key, data)`
  - Pass only small, essential data (e.g., IDs, simple filters) via query strings.
  - Not to carry large payloads.
```javascript
// Create queryString
const queryString = queryParams('data', {});

// Geting data
const queryData = queryParams();

console.log(queryData.data)
```

## Using Data Across Components
This guide explains how to share and use data across components in a Nuxt web application, The guide uses Pinia, a state management library for Vue.js, to manage shared data across components.

## Development Guidelines
- **Code Style**: Use ESLint and Prettier for consistent formatting. Configure in `.eslintrc` or `package.json`.
- **Clean Code**: Write modular, commented code. Avoid large files; break logic into composables and components.

## Troubleshooting
- **HMR Slow**: Use WSL on Windows or optimize Vite in `nuxt.config.ts`.
- **Dependency Issues**: Delete `node_modules` and `package-lock.json`, then run `npm install`.

## Contributing
- Follow setup instructions above.
- Create feature branches and submit pull requests.
- Refer to `CONTRIBUTING.md` for detailed guidelines.
- Join the Nuxt community at <a href="https://nuxt.com/docs/community/getting-help" target="_blank">nuxt.com/community</a>.

## Additional Resources
- [Nuxt 3 Documentation](https://nuxt.com)
- [Nuxt Modules](https://modules.nuxtjs.org)
- [Vue.js Documentation](https://vuejs.org)
- [NuxtUI Documentation](https://ui2.nuxt.com)
- [Flowbite Documentation](https://flowbite-vue.com)

## Conclusion
This documentation provides a clear and structured guide for developing with the Nuxt 3 project. By adhering to the naming conventions, project structure, and usage patterns for helpers, cookies, and APIs, developers can efficiently contribute to and maintain the codebase. Regularly update this documentation to reflect changes in the project.

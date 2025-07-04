# Developer Documentation for Nuxt 3 Project

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

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <project-name>
   ```
2. **Install Dependencies**:
   ```bash
   npm install
   ```
3. **Environment Configuration**:
   - Copy `.env.example` to `.env`.
   - Configure environment variables (e.g., API endpoints, keys).
4. **Run the Project**:
   - Development: `npm run dev` (Vite-powered HMR).
   - Production Build: `npm run build && npm run start`.
   - Static Site: `npm run generate` (for SSG).
5. **Note**: On Windows, use WSL for faster HMR if performance is slow.

## Project Structure
The project follows a modular structure for scalability and maintainability:

- **components/**: Reusable Vue components.
  - Example: `components/mainModule/subModule/HeaderComponent.vue`
- **composables/**: Custom composables for reusable logic.
  - Example: `composables/mainComposable/subComposable/useAuth.ts`
- **pages/**: File-based routing for pages.
  - Example: `pages/main_page/sub_page.vue`
- **stores/**: State management with Pinia.
  - Example: `stores/mainStore/subStore.ts`
- **public/**: Static assets (e.g., images, fonts).
- **nuxt.config.ts**: Nuxt configuration file.

Example directory structure:
```plaintext
project-root/
├── assets/
│   ├── lang/
│   │   └── km.json
│   │   └── en.json
├── components/
│   ├── mainModule/
│   │   └── subModule/
│   │       └── HeaderComponent.vue
├── composables/
│   ├── mainComposable/
│   │   └── subComposable/
│   │       └── useAuth.ts
├── pages/
│   ├── main_page/
│   │   └── sub_page.vue
├── stores/
│   ├── mainStore/
│   │   └── subStore.ts
├── public/
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
Use Pinia for state management:
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
- Join the Nuxt community at [nuxt.com/community](https://nuxt.com/community).

## Additional Resources
- [Nuxt 3 Documentation](https://nuxt.com)
- [Nuxt Modules](https://modules.nuxtjs.org)
- [Vue.js Documentation](https://vuejs.org)

## Conclusion
This documentation provides a clear and structured guide for developing with the Nuxt 3 project. By adhering to the naming conventions, project structure, and usage patterns for helpers, cookies, and APIs, developers can efficiently contribute to and maintain the codebase. Regularly update this documentation to reflect changes in the project.

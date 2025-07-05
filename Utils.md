# Utils

### Utility Functions
The following utility functions are available to streamline development in the Nuxt 3 project. These functions are designed to be reusable, type-safe, and compatible with client-side.

- **`copyWith`**: Creates an immutable copy of an object with specified property updates, preserving Vue’s reactivity. Use this to avoid mutating props or state directly.
```javascript
const data1 = {name: "foo"}
const data2 = copyWith(data1);
```
- **`getCurrencyIcon`**: Retrieves the emoji or image representation of a currency (e.g., USD → 🇺🇸). Returns a fallback for unsupported currencies.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`getDeviceId`**: Generates or retrieves a unique device identifier for tracking or analytics. Ensures privacy compliance (e.g., GDPR) and works in both client and server contexts.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`buildUrl`**: Constructs a URL for API endpoints, Nuxt routes, or external links. Leverages Nuxt’s `useRequestURL` or `$fetch` for robust URL handling.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`isEmpty`**: Checks if a value (e.g., object, array, string) is empty, null, or undefined. Handles edge cases for various data types.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`isNotEmpty`**: Checks if a value is non-empty. Consider using `!isEmpty` for simplicity, as this function is a convenience wrapper.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`checkGlobalContext`**: Verifies global application settings or context (e.g., environment variables or Nuxt app state). Safe for use in both SSR and CSR.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`getLuminance`**: Calculates the luminance of a color for accessibility or theming purposes, following W3C standards.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`translateBy`**: Translates a key using Nuxt’s i18n module (`$t`). Supports dynamic key-based translations with fallback handling.
```javascript
const icon = getCurrencyIcon(data1);
```
- **`onMountedUtil`**: Executes logic when a Vue component is mounted. Wraps `onMounted` composable for specific use cases (e.g., delayed execution).
```javascript
const icon = getCurrencyIcon(data1);
```
- **`formatDate`**: Formats a date for display, compatible with SSR. Uses a library like `date-fns` or `day.js` for consistent date handling.
```javascript
const icon = getCurrencyIcon(data1);
```

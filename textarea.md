###### [Home](/_doc)

## \# **OCTextarea** :

Display a textarea field.

- ### **Usage**

  \- Use a **v-model** to make the Textarea reactive.

```vue
<template>
  <OCTextarea v-model="value" />
</template>

<script setup>
const value = ref("");
</script>
```

- ### **Size**

  \- Use the **size** prop to change the size of the Textarea.

```vue
<template>
  <OCTextarea size="sm" />
</template>
```

- ### **Placeholder**

  \- Use the **placeholder** prop to set a placeholder text.

```vue
<template>
  <OCTextarea placeholder="Description..." />
</template>
```

- ### **Rows**

  \- Use the **rows** prop to set the number of rows of the Textarea.

```vue
<template>
  <OCTextarea :row="1" placeholder="Description..." />
</template>
```

- ### **Disabled**

  \- Use the **disabled** prop to disable the Textarea.

```vue
<template>
  <OCTextarea disabled placeholder="Description..." />
</template>
```

- ### **Autoresize**

  \- Use the **autoresize** prop to enable the autoresize. Writing more lines than the rows prop will make the Textarea grow up.

```vue
<template>
  <OCTextarea v-model="value" autoresize placeholder="Description..." />
</template>

<script setup>
const value = ref();
</script>
```

- ### **Maxrows**
  \- Use the **maxrows** prop to set a maximum number of rows when autoresizing. If set to 0, the Textarea will infinitely grow up.

```vue
<template>
  <OCTextarea
    v-model="value"
    autoresize
    :maxrows="5"
    placeholder="Description..."
  />
</template>

<script setup>
const value = ref();
</script>
```

- ### **Resize**

  \- Use the **resize** prop to enable the resize control.

```vue
<template>
  <OCTextarea resize placeholder="Description..." />
</template>
```

- ### **UI**

  \- Use the **ui** prop to customize style textarea field.

```vue
<template>
  <OCTextarea
    placeholder="Description..."
    :ui="{ base: 'color-bg-wrapper !shadow-none focus:!ring-1' }"
  />
</template>
```

- ### **Props**

  \- **size** : TextareaSize ( **"2xs"**, **"xs"**, **"sm"**, **"md"**, **"lg"**, **"xl"** ). The default prop set **md**.

  \- **name** : string. The default prop set **"null"**.

  \- **placeholder** : string. The default prop set **"null"**.

  \- **rows** : number. The default prop set **4**.

  \- **maxrows** : number. The default prop set **0**.

  \- **autofocusDelay** : number. The default prop set **100**.

  \- **autofocus** : boolean. The default prop set **false**.

  \- **resize** : boolean. The default prop set **false**.

  \- **autoresize** : boolean. The default prop set **false**.

  \- **required** : boolean. The default prop set **false**.

  \- **disabled** : boolean. The default prop set **false**.

  \- **ui** : object. The default prop set **\{ \}**.

- ### **Config UI**

```js
const ui = {
  wrapper: "relative",
  base: "color-bg-wrapper !shadow-none focus:!ring-1",
  form: "form-textarea",
  rounded: "rounded-[10px]",
  placeholder: "placeholder-gray-400 dark:placeholder-gray-500",
  file: {
    base: "file:mr-1.5 file:font-medium file:text-gray-500 dark:file:text-gray-400 file:bg-transparent file:border-0 file:p-0 file:outline-none color-text",
  },
  size: {},
  gap: {},
  padding: {},
};
```

---

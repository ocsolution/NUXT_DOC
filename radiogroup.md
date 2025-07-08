###### [Home](/_doc)

## \# **OCRadioGroup** :

Display a set of radio buttons.

- ### **Usage**

  \- Use a **v-model** to make the RadioGroup reactive.

```vue
<template>
  <OCRadios v-model="selected" :options="options" />
</template>

<script setup>
const options = [
  { value: "female", label: "Female" },
  { value: "male", label: "Male" },
];

const selected = ref();
</script>
```

- ### **Disabled**

  \- Use the **disabled** prop to disable the RadioGroup.

```vue
<template>
  <OCRadios :options="options" disabled />
</template>

<script setup>
const options = [
  { value: "female", label: "Female" },
  { value: "male", label: "Male" },
];
</script>
```

- ### **Slots**

  \- **label** : Use the **#label** slot to override the label of each option.

```vue
<template>
  <OCRadios :options="options">
    <template #label="{ option }">
      <span class="italic">{{ option.label }}</span>
    </template>
  </OCRadios>
</template>

<script setup>
const options = [
  { value: "female", label: "Female" },
  { value: "male", label: "Male" },
];
</script>
```

- ### **UI**

  \- Use the **ui** prop to customize style Container RadioGroup.

```vue
<template>
  <OCRadios
    :options="options"
    :ui="{
      wrapper:
        'flex-wrap py-2 px-3 ring-1 ring-inset ring-gray-300 dark:ring-gray-700 ocs-rounded color-bg-wrapper',
    }"
  />
</template>

<script setup>
const options = [
  { value: "female", label: "Female" },
  { value: "male", label: "Male" },
];
</script>
```

- ### **UI Radio**

  \- Use the **ui** prop to customize style Radio.

```vue
<template>
  <OCRadios
    :options="options"
    :ui="{
      base: 'h-4 w-4',
    }"
  />
</template>

<script setup>
const options = [
  { value: "female", label: "Female" },
  { value: "male", label: "Male" },
];
</script>
```

- ### **Props**

  \- **name** : string. The default prop set **null**.

  \- **options** : array. properties in options ( **label** and **value** is required, **disabled**).

  \- **disabled** : boolean. The default prop set **false**.

  \- **optionAttribute** : string. The default prop set **"label"**.

  \- **valueAttribute** : string. The default prop set **"value"**.

  \- **ui** : object. The default prop set **\{ \}**.

  \- **uiRadio** : object. The default prop set **\{ \}**.

- ### **Config UI & UI Radio**

```js
const ui = {
  wrapper:
    "relative flex items-start flex-wrap py-2 px-3 ring-1 ring-inset ring-gray-300 dark:ring-gray-700 ocs-rounded color-bg-wrapper",
  fieldset: "flex flex-wrap items-center gap-x-5 gap-y-3",
};
const uiRadio = {
  wrapper: "relative flex items-start",
  container: "flex items-center h-5",
  base: "h-4 w-4",
  form: "form-radio",
  background: "bg-transparent dark:bg-transparent",
  border: "border border-gray-300 dark:border-gray-700",
  ring: "",
  inner: "",
  label: "text-sm font-normal color-w-b-1 line-clamp-1",
  required: "",
  help: "",
};
```

---

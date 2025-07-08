###### [Home](/_doc)

## \# **OCCheckboxGroup** :

Display a group of checkbox field.

- ### **Usage**

  \- Use a **v-model** to make the CheckboxGroup reactive.

```vue
<template>
  <OCCheckboxes v-model="selected" :options="options" />
</template>

<script setup>
const options = [
  { value: "email", label: "Email" },
  { value: "sms", label: "Phone (SMS)" },
];

const selected = ref([]);
</script>
```

- ### **Disabled**

  \- Use the **disabled** prop to disable the Checkbox.

```vue
<template>
  <OCCheckboxes v-model="selected" :options="options" disabled />
</template>

<script setup>
const options = [
  { value: "email", label: "Email" },
  { value: "sms", label: "Phone (SMS)" },
];

const selected = ref([]);
</script>
```

- ### **Slots**

  \- **label** : Use the **#label** slot slot to customize the label.

```vue
<template>
  <OCCheckboxes v-model="selected" :options="options">
    <template #label="item">
      <span class="italic">{{ item.label }} </span>
    </template>
  </OCCheckboxes>
</template>

<script setup>
const options = [
  { value: "email", label: "Email" },
  { value: "sms", label: "Phone (SMS)" },
];

const selected = ref([]);
</script>
```

- ### **Props**

  \- **name** : string. The default prop set **null**.

  \- **ui** : string. The default prop set **null**.

  \- **options** : array. properties in options ( **label** and **value** is required, **disabled**).

  \- **disabled** : boolean. The default prop set **false**.

---

###### [Home](/_doc)

## \# **OCCheckbox** :

Display a checkbox field

- ### **Usage**

  \- Use a **v-model** to make the Checkbox reactive.

```vue
<template>
  <OCCheckbox v-model="selected" label="Checkbox" name="Checkbox" />
</template>

<script setup>
const selected = ref(true);
</script>
```

- ### **Label**

  \- Use the **label** prop to display a label on the right.

```vue
<template>
  <OCCheckbox label="Checkbox" />
</template>
```

- ### **Required**

  \- Use the **required** prop to display a red star next to the label of the Checkbox.

```vue
<template>
  <OCCheckbox label="Checkbox" required />
</template>
```

- ### **Help**

  \- Use the **help** prop to display some text under the Checkbox.

```vue
<template>
  <OCCheckbox label="Checkbox" help="Please check this box" />
</template>
```

- ### **Disabled**

  \- Use the **disabled** prop to disable the Checkbox.

```vue
<template>
  <OCCheckbox label="Checkbox" disabled />
</template>
```

- ### **Slots**

  \- **label** : Use the **#label** slot to override the content of the label.

```vue
<template>
  <OCCheckbox>
    <template #label>
      <span class="italic">Checkbox</span>
    </template>
  </OCCheckbox>
</template>
```

- ### **Props**

  \- **label** : string. The default prop set **null**.

  \- **help** : string. The default prop set **null**.

  \- **name** : string. The default prop set **null**.

  \- **ui** : object. The default prop set **\{ \}**.

  \- **required** : boolean. The default prop set **false**.

  \- **disabled** : boolean. The default prop set **false**.

---

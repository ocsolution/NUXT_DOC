###### [Home](/_doc)

## \# **OCRadio** :

Display a set of radio button.

- ### **Usage**

  \- Use a **v-model** to make the Radio reactive.

```vue
<template>
  <OCRadio v-model="radio" :value="true" label="Radio" />
</template>

<script setup>
const radio = ref();
</script>
```

- ### **Required**

\-Use the **required** prop to display a red star next to the label of the Radio.

```vue
<template>
  <OCRadio label="Radio" required />
</template>
```

- ### **Help**

  \- Use the **help** prop to display some text under the Radio.

```vue
<template>
  <OCRadio label="Radio" help="Please choose one" />
</template>
```

- ### **Disabled**

  \- Use the **disabled** prop to disable the Radio.

```vue
<template>
  <OCRadio label="Radio" disabled />
</template>
```

- ### **Slots**

  \- **label** : Use the **#label** slot to override the content of the label.

```vue
<template>
  <OCRadio>
    <template #label>
      <span class="italic">Radio</span>
    </template>
  </OCRadio>
</template>
```

- ### **Props**

  \- **value** : can set ( string | number | boolean). The default prop set **null**.

  \- **label** : string. The default prop set **null**.

  \- **help** : string. The default prop set **null**.

  \- **name** : string. The default prop set **null**.

  \- **ui** : object. The default prop set **\{ \}**.

  \- **required** : boolean. The default prop set **false**.

  \- **disabled** : boolean. The default prop set **false**.

---

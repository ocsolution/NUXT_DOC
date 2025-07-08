###### [Home](/_doc)

## \# **OCInput** :

Display an input

- ### **Usage**

  \- Use a **v-model** to make the Input reactive.

```vue
<template>
  <OCInput v-model="value" />
</template>

<script setup>
const value = ref("");
</script>
```

- ### **Size**
  \- Use the **size** prop to change the size of the Input.

```vue
<template>
  <OCInput size="md" />
</template>
```

- ### **Type**

  \- Use the **type** prop to change the input **type**, the default **type** is set to text.

  \- Some types have been implemented in their own components, such as **Checkbox**, **Radio**, etc. and others have been styled like **file** for example.

```vue
<template>
  <OCInput type="file" v-model="" icon="i-heroicons-folder" />
</template>
```

- ### **Placeholder**

  \- Use the **placeholder** prop to set a placeholder text.

```vue
<template>
  <OCInput placeholder="please enter input" />
</template>
```

- ### **Icon**

  \- Use the **leading** and **trailing** props to set the icon position or the **leading-icon** and **trailing-icon** props to set a different icon for each position.

```vue
<template>
  <OCInput
    icon="ri-keyboard-line"
    :trailing="false"
    placeholder="please enter input"
  />
</template>
```

- ### **Disabled**

  \- Use the **disabled** prop to disable the Input.

```vue
<template>
  <OCInput disabled placeholder="please enter input" />
</template>
```

- ### **Loading**

  \- Use the **loading** prop to show a loading icon and disable the Input.

  \- Use the **loading-icon** prop to set a different icon. Defaults to **i-heroicons-arrow-path-20-solid**.

```vue
<template>
  <OCInput loading placeholder="please enter input" />
</template>
```

- ### **Slots**

  \- **leading** : Use the **#leading** slot to set the content of the leading icon.

  \- **trailing** : Use the **#trailing** slot to set the content of the trailing icon.

```vue
<template>
  <OCInput placeholder="please enter input">
    <template #leading>
      <i class="ri-community-line"></i>
    </template>

    <template #trailing>
      <i class="ri-arrow-down-s-line"></i>
    </template>
  </OCInput>
</template>
```

\* You can for example create a clearable Input by injecting a Button in the trailing slot that displays when some text is entered. The **ui** prop `:ui="{ icon: { trailing: { pointer: '' } } }"` is required.

```vue
<template>
  <OCInput
    v-model="input"
    placeholder="please enter input"
    :ui="{ icon: { trailing: { pointer: '' } } }"
  >
    <template #trailing>
      <UButton
        v-show="input ? true : false"
        color="gray"
        variant="link"
        icon="i-heroicons-x-mark-20-solid"
        @click="input = ''"
      />>
    </template>
  </OCInput>
</template>

<script setup>
const input = ref();
</script>
```

- ### **Props**

  \- **size** : InputSize ( **"2xs"**, **"xs"**, **"sm"**, **"md"**, **"lg"**, **"xl"** ). The default prop set **md**.

  \- **name** : string. The default prop set **null**.

  \- **type** : string. The default prop set **"text"**.

  \- **ui** : object. The default prop set **{}**.

  \- **icon** : string. The default prop set **null**.

  \- **placeholder** : string. The default prop set **null**.

  \- **loadingIcon** : string. The default prop set **"i-heroicons-arrow-path-20-solid"**.

  \- **leadingIcon** : string. The default prop set **null**.

  \- **trailingIcon** : string. The default prop set **null**.

  \- **disabled** : boolean. The default prop set **false**.

  \- **trailing** : boolean. The default prop set **false**.

  \- **loading** : boolean. The default prop set **false**.

  \- **autofocus** : boolean. The default prop set **false**.

  \- **autofocusDelay** : number. The default prop set **100**.

  \- **autocomplete** : string. The default prop set **"on"**.

---

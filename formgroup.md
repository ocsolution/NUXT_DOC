- ###### [Home](/_doc)

## \# **OCFormGroup**

\- Display a label and additional informations around a form element.

- ### **Usage**
  \- Use the OCFormGroup component around an **OCInput**, **OCTextarea**, **OCSelect**, **OCRadio**, **OCRadioGroup**, **OCCheckbox** or an **OCCheckboxGroup**, **etc...** with a label. The **label** will automatically be associated with the form element so it gets focused on click.

```vue
<template>
  <OCFormGroup label="Email">
    <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
  </OCFormGroup>
</template>
```

- ### **Required**

  \- Use the required prop to indicate that the form element is required.

```vue
<template>
  <OCFormGroup label="Email" required>
    <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
  </OCFormGroup>
</template>
```

- ### Description

  \- Use the description prop to display a description below the label.

```vue
<template>
  <OCFormGroup label="Email" description="We'll only use this for spam.">
    <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
  </OCFormGroup>
</template>
```

- ### Hint

  \- Use the hint prop to display a hint above the form element.

```vue
<template>
  <OCFormGroup label="Email" hint="Option">
    <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
  </OCFormGroup>
</template>
```

- ### Help

  \- Use the help prop to display an help message below the form element.

```vue
<template>
  <OCFormGroup
    label="Email"
    help="We will never share your email with anyone else."
  >
    <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
  </OCFormGroup>
</template>
```

- ### Slots

\- **slot label** : Use the **#label** slot to set the custom content for label.

```vue
<template>
  <OCFormGroup>
    <template #label>
      <div class="inline-flex items-center justify-center h-4 w-4">
        <img
          src="https://avatars.githubusercontent.com/u/739984?v=4"
          class="rounded-full object-cover text-[8px]"
        />
      </div>
    </template>
    <template #default>
      <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
    </template>
  </OCFormGroup>
</template>
```

\- **slot description** : Use the #description slot to set the custom content for description.

```vue
<template>
  <OCFormGroup label="Email">
    <template #description>
      <div class="flex items-center space-x-[2px]">
        <span>Write only valid email address</span>
        <i class="i-heroicons-information-circle" />
      </div>
    </template>
    <template #default>
      <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
    </template>
  </OCFormGroup>
</template>
```

\- **slot hint** : Use the #hint slot to set the custom content for hint.

```vue
<template>
  <OCFormGroup label="Email">
    <template #hint>
      <i class="i-heroicons-information-circle" />
    </template>
    <template #default>
      <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
    </template>
  </OCFormGroup>
</template>
```

\- **slot help** : Use the #help slot to set the custom content for help.

```vue
<template>
  <OCFormGroup label="Email">
    <template #help>
      <div class="flex items-center space-x-[2px]">
        <span>Here are some examples</span>
        <i class="i-heroicons-information-circle" />
      </div>
    </template>
    <template #default>
      <OCInput placeholder="you@example.com" icon="i-heroicons-envelope" />
    </template>
  </OCFormGroup>
</template>
```

\- **slot error** : Use the #error slot to set the custom content for error.

```vue
<template>
  <OCFormGroup
    label="Email"
    :error="!email && 'You must enter an email'"
    help="This is a nice email!"
  >
    <template #default="{ error }">
      <OCInput
        v-model="email"
        type="email"
        placeholder="Enter email"
        :trailing-icon="
          error ? 'i-heroicons-exclamation-triangle-20-solid' : undefined
        "
      />
    </template>

    <template #error="{ error }">
      <span
        :class="[
          error
            ? 'text-red-500 dark:text-red-400'
            : 'text-primary-500 dark:text-primary-400',
        ]"
      >
        {{ error ? error : "Your email is valid" }}
      </span>
    </template>
  </OCFormGroup>
</template>

<script setup>
const email = ref("");
</script>
```

- ### **Props**

  \- **size** : FormGroupSize ( **"2xs"**, **"xs"**, **"sm"**, **"md"**, **"lg"**, **"xl"** ). The default prop set **md**.

  \- **name** : string. The default prop set **null**.

  \- **label** : string. The default prop set **null**.

  \- **help** : string. The default prop set **null**.

  \- **description** : string. The default prop set **null**.

  \- **hint** : string. The default prop set **null**.

  \- **error** : string | boolean. The default prop set **null**.

  \- **ui** : object. The default prop set **\{ \}**.

  \- **required** : boolean. The default prop set **false**.

  \- **disabled** : boolean. The default prop set **false**.

---

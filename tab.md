###### [Home](/_doc)

## \# **OCTab**

\- A set of tab panels that are displayed one at a time.

- ### **Usage**

  Pass an array to the **items** prop of the Tabs component. Each item can have the following properties:

  \+ label - The label of the item.

  \+ slot - A key to customize the item with a slot.

  \+ content - The content to display in the panel by default.

  \+ disabled - Determines whether the item is disabled or not.

```vue
<template>
  <OCTab :items="items" />
</template>

<script setup>
const items = [
  {
    label: "Tab1",
    content: "This is the content shown for Tab1",
  },
  {
    label: "Tab2",
    disabled: true,
    content: "And, this is the content for Tab2",
  },
  {
    label: "Tab3",
    content: "Finally, this is the content for Tab3",
  },
];
</script>
```

- ### **Vertical**

  \- You can change the orientation of the tabs by setting the **orientation** prop to **vertical**.

  But you can use ui prop to customize width **\: ui="{ list: { width: '' } }"**.

```vue
<template>
  <OCTab :items="items" :ui="{ list: { width: 'w-48' } }" />
</template>

<script setup>
const items = [
  {
    label: "Tab1",
    content: "This is the content shown for Tab1",
  },
  {
    label: "Tab2",
    content: "And, this is the content for Tab2",
  },
  {
    label: "Tab3",
    content: "Finally, this is the content for Tab3",
  },
];
</script>
```

- ### **Default index**

  \- You can set the default index of the tabs by setting the **default-index** prop.

```vue
<template>
  <OCTab :items="items" :default-index="2" />
</template>

<script setup>
const items = [
  {
    label: "Tab1",
    content: "This is the content shown for Tab1",
  },
  {
    label: "Tab2",
    content: "And, this is the content for Tab2",
  },
  {
    label: "Tab3",
    content: "Finally, this is the content for Tab3",
  },
];
</script>
```

- ### **Listen to changes**

  \- You can listen to changes by using the **@change** event. The event will emit the index of the selected item.

```vue
<template>
  <OCTab :items="items" @change="onChange" />
</template>

<script setup>
const items = [
  {
    label: "Tab1",
    content: "This is the content shown for Tab1",
  },
  {
    label: "Tab2",
    content: "And, this is the content for Tab2",
  },
  {
    label: "Tab3",
    content: "Finally, this is the content for Tab3",
  },
];

function onChange(index) {
  const item = items[index];

  alert(`${item.label} was clicked!`);
}
</script>
```

- ### **Slots**

  \- You can use slots to customize the buttons and items content of the Accordion.

##### \+ **slot default**

\- Use the **#default** slot to customize the content of the trigger buttons. You will have access to the **item**, **index**, **selected** and \*\* \*\* in the slot scope.

```vue
<template>
  <OCTab :items="items">
    <template #default="{ item, index, selected }">
      <div class="flex items-center gap-2 relative truncate">
        <i :class="`w-4 h-4 ${item.icon}`" />
        <span class="truncate">{{ index + 1 }}. {{ item.label }}</span>
      </div>
    </template>
  </OCTab>
</template>

<script setup>
const items = [
  {
    label: "Getting Started",
    icon: "i-heroicons-information-circle",
    content: "This is the content shown for Tab1",
  },
  {
    label: "Installation",
    icon: "i-heroicons-arrow-down-tray",
    content: "And, this is the content for Tab2",
  },
  {
    label: "Theming",
    icon: "i-heroicons-eye-dropper",
    content: "Finally, this is the content for Tab3",
  },
];
</script>
```

##### \+ **slot item**

\- Use the **#item** slot to customize the items content. You will have access to the **item**, **index** and **selected** properties in the slot scope.

```vue
<template>
  <OCTab :items="items">
    <template #tab1="{ item, index, selected }">
      <OCCard class="max-w-sm">
        <template #header>
          <div class="p-4">
            <p class="text-lg font-medium">{{ item.label }}</p>
            <p class="color-sub-text">{{ item.description }}</p>
          </div>
        </template>
        <div class="grid justify-center items-center">
          <h3>Hello Tab1</h3>
        </div>
      </OCCard>
    </template>

    <template #tab2="{ item, index, selected }">
      <OCCard class="max-w-sm">
        <template #header>
          <div class="p-4">
            <p class="text-lg font-medium">{{ item.label }}</p>
            <p class="color-sub-text">{{ item.description }}</p>
          </div>
        </template>
        <div class="grid justify-center items-center">
          <h3>Hello Tab2</h3>
        </div>
      </OCCard>
    </template>
  </OCTab>
</template>

<script setup>
const items = [
  {
    label: "Tab 1",
    slot: "tab1",
    description: "This is the content shown for Tab1",
  },
  {
    label: "Tab 2",
    slot: "tab2",
    description: "And, this is the content for Tab2",
  },
];
</script>
```

##### \+ **use slot in items prop**

\- You can also pass a slot property to customize a specific item.

```vue
<template>
  <OCTab :items="items">
    <template #item="{ item, index, selected }">
      <OCCard class="max-w-sm">
        <template #header>
          <div class="p-4">
            <p class="text-lg font-medium">{{ item.label }}</p>
            <p class="color-sub-text">{{ item.description }}</p>
          </div>
        </template>
        <div v-if="item.key == 'tab1'">
          <div class="flex justify-center items-center">
            <h3>Hello Tab1</h3>
          </div>
        </div>
        <div>
          <div class="flex justify-center items-center">
            <h3>Hello Tab2</h3>
          </div>
        </div>
      </OCCard>
    </template>
  </OCTab>
</template>

<script setup>
const items = [
  {
    label: "Tab 1",
    slot: "tab1",
  },
  {
    label: "Tab 2",
    slot: "tab2",
  },
];
</script>
```

- ### **Props**

  \- **items** : array. properties in items ( **label** is required, **disabled**, **content**, **slot** ) and can create any properties.

  \- **orientation** : string ("horizontal" | "vertical"). The default prop set **"vertical"**.

  \- **defaultIndex** : number. The default prop set **0**.

  \- **ui** : object. The default prop set **\{ \}**.

---

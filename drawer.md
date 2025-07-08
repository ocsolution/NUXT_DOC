###### [Home](/_doc)

## \# OCDrawer

\- Display a dialog that slides in from the edge of the screen.

- ### **Usage**

  \- Use a v-model to control the **OCDrawer** state.

```vue
<template>
  <div>
    <UButton label="Open" @click="isOpen = true" />

    <OCDrawer v-model="isOpen">
      <div class="p-4 flex-1">
        <UButton
          color="gray"
          variant="ghost"
          size="sm"
          icon="i-heroicons-x-mark-20-solid"
          class="flex sm:hidden absolute end-5 top-5 z-10"
          square
          padded
          @click="isOpen = false"
        />>
      </div>
    </OCDrawer>
  </div>
</template>

<script setup>
const isOpen = ref(false);
</script>
```

- ### **Disable overlay**

  \- Set the **overlay** prop to **false** to disable it.

```vue
<template>
  <div>
    <UButton label="Open" @click="isOpen = true" />

    <OCDrawer v-model="isOpen" :overlay="false">
      <div class="p-4 flex-1">
        <UButton
          color="gray"
          variant="ghost"
          size="sm"
          icon="i-heroicons-x-mark-20-solid"
          class="flex sm:hidden absolute end-5 top-5 z-10"
          square
          padded
          @click="isOpen = false"
        />>
      </div>
    </OCDrawer>
  </div>
</template>

<script setup>
const isOpen = ref(false);
</script>
```

- ### **Disable transition**

  \- Set the transition prop to false to disable it.

```vue
<template>
  <div>
    <UButton label="Open" @click="isOpen = true" />

    <OCDrawer v-model="isOpen" :transition="false">
      <div class="p-4 flex-1">
        <UButton
          color="gray"
          variant="ghost"
          size="sm"
          icon="i-heroicons-x-mark-20-solid"
          class="flex sm:hidden absolute end-5 top-5 z-10"
          square
          padded
          @click="isOpen = false"
        />>
      </div>
    </OCDrawer>
  </div>
</template>

<script setup>
const isOpen = ref(false);
</script>
```

- ### **Prevent close**

  \- Use the **prevent-close** prop to disable the outside click

```vue
<template>
  <div>
    <UButton label="Open" @click="isOpen = true" />

    <OCDrawer v-model="isOpen" :prevent-close="false">
      <div class="p-4 flex-1">
        <UButton
          color="gray"
          variant="ghost"
          size="sm"
          icon="i-heroicons-x-mark-20-solid"
          class="flex sm:hidden absolute end-5 top-5 z-10"
          square
          padded
          @click="isOpen = false"
        />>
      </div>
    </OCDrawer>
  </div>
</template>

<script setup>
const isOpen = ref(false);
</script>
```

- ### Slots

\- **slot header** : use to slot to fill the header.

```vue
<template>
  <div>
    <UButton label="Open" @click="isOpen = true" />

    <OCDrawer v-model="isOpen">
      <template #header>
        <h3
          class="text-base font-semibold leading-6 text-gray-900 dark:text-white flex items-center space-x-1"
        >
          <span>{{ $t("home") }} Drawer</span>
        </h3>
      </template>
    </OCDrawer>
  </div>
</template>

<script setup>
const isOpen = ref(false);
</script>
```

\- **slot footer** : use to slot to fill the footer.

```vue
<template>
  <div>
    <UButton label="Open" @click="isOpen = true" />

    <OCDrawer v-model="isOpen">
      <template #footer>
        <h3
          class="text-base font-semibold leading-6 text-gray-900 dark:text-white flex items-center space-x-1"
        >
          <span>Drawer Footer</span>
        </h3>
      </template>
    </OCDrawer>
  </div>
</template>

<script setup>
const isOpen = ref(false);
</script>
```

- ### Props

  \- **side** : string **"right"** | **"left"**. The default prop set **"left"**.

  \- **transition** : boolean. The default prop set **true**.

  \- **overlay** : boolean. The default prop set **true**.

  \- **preventClose** : boolean. The default prop set **false**.

  \- **appear** : boolean. The default prop set **false**.

  \- **ui** : object. The default prop set **\{ \}**.

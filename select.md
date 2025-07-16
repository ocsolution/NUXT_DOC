# OCSelect

## Props

### + required
Used to enforce a required selection. If `true`, prevents selection from being cleared. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :required="true" />
```

### + localData
Used Local source for select options. Expected to have a `.data` array and optionally `.keySearch`.

```vue
<OCSelect v-model="selectedUser" :localData="{ data: users }" />
```

### + api
Used to enables remote fetching for select options. API config object (e.g., `{ url, method, filter, where, fixObjectValue }`).

```vue
<OCSelect v-model="selectedUser" :api="{ url: '/api/users', method: 'POST', where: 'data', filter: { active: true } }"/>
```

### + isNotAllowClear
Used to prevents adding a ---Clear Selected--- option, if `true`. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :isNotAllowClear="true" />
```

### + defaultSelect
Used to auto-selects the first option, if `true`. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :defaultSelect="true" />
```

### + multiple
Used to enables multi-selection mode, if `true`. Default: `false`.

```vue
<OCSelect v-model="selectedUsers" :multiple="true" />
```

### + selectIfOne
If `true` and only one item exists, auto-selects it. Default: `false`.

```vue
<OCSelect v-model="selectedRole" :localData="{ data: roles }" :selectIfOne="true" />
```

### + searchable
If `true`, enables search. If a function, it’s used as custom search handler. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :searchable="false" />
```

Or use a custom search function:

```vue
<OCSelect v-model="selectedUser" :searchable="customSearchFn" />
```

### + disabled
If `true`, disables the component entirely. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :disabled="true" />
```

### + specificProp
Property name used to auto-select value during initialization.

```vue
<OCSelect v-model="selectedUser" :localData="{ data: users }" specificProp="IsDefault"/>
```

### + variant
Style variant: `"outline"`, `"solid"`, `"solidBackGround"`, `"none"` — determines visual style.

```vue
<OCSelect v-model="selectedUser" variant="solid" />
<OCSelect v-model="selectedUser" variant="outline" />
<OCSelect v-model="selectedUser" variant="none" />
```

### + class
Extra CSS class to apply to the root container.

```vue
<OCSelect v-model="selectedUser" class="custom-border" />
```

### + placeholder
Text to show when no selection is made. Default: `Please select`.

```vue
<OCSelect v-model="selectedUser" placeholder="Choose a user" />
```

### + selectType
Used to trigger special logic like selecting the current academic year. Default: `""`.

```vue
<OCSelect v-model="academicYear" selectType="academicYear" />
```

### + colorPlaceholder
If `true`, renders placeholder text in primary color instead of grey. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :colorPlaceholder="true" />
```

### + recordCountPropotyName
Property name to extract totalRecord from the response for pagination. Note: Typo, should be `recordCountPropertyName`. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :api="{ url: '/api/users' }" recordCountPropotyName="TotalUsers"/>
```

### + clearSelect
Used to enables the `---Clear Selected---` option. Only relevant in single-select mode. Default: `true`.

```vue
<OCSelect v-model="selectedUser" :clearSelect="false" />
```

### + pk
The primary key field used to identify options. Used for comparing selected items. Default: `null`.

```vue
<OCSelect v-model="selectedItem" :pk="'UserId'" />
```

### + templateLeading
Used to controls how options and selected items are displayed (leading/profile/info).

```vue
<OCSelect v-model="selectedUser"
  :templateLeading="{
    labelKey: 'Name',
    labelKeyEn: 'NameEnglish',
    imagePath: 'Avatar',
    gender: 'Gender'
  }"
/>
```

### + templateOption
Used to controls how dropdown options are displayed (profile/info view with sublabel).

```vue
<OCSelect v-model="selectedUser"
  :templateOption="{
    labelKey: 'Name',
    labelKeyEn: 'NameEnglish',
    subLabelKey: 'Email',
    subLabelKeyEn: 'Email',
    imagePath: 'Avatar',
    gender: 'Gender'
  }"
/>
```
### + isNotAllowRemoteSelect
If `true`, prevents calling `remoteSelect()` method programmatically. Default: `false`.

```vue
<OCSelect v-model="selectedUser" :isNotAllowRemoteSelect="true" />
```

## Emits

### + @selected
Emitted every time the selected value changes.This emits has 2 mode:
- In single mode: `an object` or `undefined`.
- In multiple mode: `an array of selected objects` or `[]`.

```vue
<template>
  <OCSelect v-model="selectedUser" @selected="handleSelection" />
</template>

<script setup>
function handleSelection(val) {
  console.log("Selected:", val);
}
</script>
```

### + @mapData=""
Emitted after data is fetched or updated.

```vue
<template>
  <OCSelect v-model="selectedUser" @mapData="handleListData" />
</template>

<script setup>
function handleListData(data) {
  console.log("data:", data);
}
</script>
```

### + @onSearch=""
Emitted when user types in the search box

```vue
<template>
  <OCSelect v-model="selectedUser" @onSearch="logSearch" />
</template>

<script setup>
function logSearch(search) {
  console.log("User is searching for:", search);
}
</script>
```

## Expose
This makes internal functions available to the parent component, so the parent can control or refresh the `<OCSelect />` programmatically.

### + remoteSelect(filter: object)
Programmatically set selected item(s) by `pk` value or filter from `API/local`. `filter` should include pk and value(s) to match in data source, can also include additional filters ({ isFilter: true }).

```vue
<template>
  <OCSelect ref="refSelectUser" :api="{ url: '/api/users', method: 'POST' }" />
</template>

<script setup>
const refSelectUser = ref()

// Select user with ID 5
refSelectUser.value.remoteSelect({ pk: 'Id', Id: 5 })

// For multiple mode: select by array of IDs
// refSelectUser.value.remoteSelect({ pk: 'Id', Id: [1, 2, 3] })
</script>
```

### + reload()
Re-fetch options list (from API or local)

```vue
<template>
  <Button @click="fnReload">Reload</Button>
  <OCSelect ref="refSelectUser" :api="{ url: '/api/users', method: 'POST' }" />
</template>

<script setup>
const refSelectUser = ref()

// Reload options manually
function fnReload(){
  refSelectUser.value.reload()
}
</script>
```


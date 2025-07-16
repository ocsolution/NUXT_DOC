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

### + pk
The primary key field used to identify options. Used for comparing selected items. Default: `null`.

### + templateLeading
Used to controls how options and selected items are displayed (leading/profile/info).

### + templateOption
Used to controls how dropdown options are displayed (profile/info view with sublabel).

### + isNotAllowRemoteSelect
If `true`, prevents calling `remoteSelect()` method programmatically.






###### [Home](/_doc)

## \# **OCSelect**

- ### **Usage**

  \- Use a **v-model** to make the OCSelect reactive.

```vue
<template>
  <OCSelect
    v-model="select"
    text="Code"
    :api="{
      url: 'https://demo1api.kottrasala.com//api/enrollment/get',
      method: 'post',
    }"
    :options="{ placeholder: 'Please select you' }"
  />
</template>

<script setup>
const select = ref();
</script>
```

- ### **Api**

  \- Use the **api** prop to get data from server.

```vue
<template>
  <OCSelect
    text="Code"
    :api="{
      url: 'https://demo1api.kottrasala.com//api/enrollment/get',
      method: 'post',
    }"
  />
</template>
```

- ### **Select Multiple data**

```vue
<template>
  <OCSelect
    text="Code"
    :api="{
      url: 'https://demo1api.kottrasala.com//api/enrollment/get',
      method: 'post',
    }"
    :options="{
      placeholder: 'Please select item',
      multiple: true,
    }"
  />
</template>

<script setup>
const select = ref();
</script>
```

- ### **Function in OCSelect**

  \- **update:template** : use this function for customize UI lists on OCSelect.

  \- **update:selection** : use this function for customize UI when selected list on OCSelect.

  \- **update:data** : use this function for set data filter to API.

  \- **update:process**: use this function for get data from API.

```vue
<template>
  <OCSelect
    text="Code"
    :api="{
      url: 'https://demo1api.kottrasala.com//api/enrollment/get',
      method: 'post',
    }"
    :options="{
      placeholder: 'Please select item',
    }"
    @update:data="updateData"
    @update:process="updateProcess"
    @update:template="updateTemplate"
    @update:selection="updateSelection"
  >
  </OCSelect>
</template>

<script setup>
const select = ref();

function updateData(e) {
  console.log("updateData", e);
}
function updateProcess(e) {
  console.log("updateProcess", e);
}
function updateSelection(e) {
  e.selection = `<div class='flex gap-1.5 items-center'>
                    <img src="/img/default.svg" class="w-5 h-5 rounded-full"/>
                    <span>${e.NameKh}</span>
                </div>`;
}

function updateTemplate(e) {
  e.template = `<div class='flex gap-1.5 items-center'>
                    <img src="/img/default.svg" class="w-7 h-7 rounded-full"/>
                    <span>${e.NameKh}</span>
                </div>`;
}
</script>
```

- ### **Props**

  \- **text** : string. The default prop set **null** and is **required**.

  \- **pk** : string. The default prop set **Id** and is **required**.

  \- **api** : use to get data from server . if type of api is `GET` **api** prop value is string `api="/api/enrollment/list"` and type of api is `POST` **api** prop value is object `:api="{ url:'/api/enrollment/list', type:'POST' }"`.

  \- **options** : object. The default prop set **\{ search: true, pagination: true, placeholder: '', multiple: false, tag: false, required:false \}**

  \- **data** : use to get data from localData and value is array **\[ \]**

---

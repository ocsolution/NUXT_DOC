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

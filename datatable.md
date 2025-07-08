###### [Home](/_doc)

## **OCDataTable**

### \# **Usage**

- **Use with Data** : you can use without **columns** prop if you don't use columns datatable auto generate from **data** prop to render **th** for show on table. But you should use **columns** prop.

- **Use with API** : **columns** prop is required.

  \+ **api** prop gets value:

  \- if **api** method of api is `GET` then **api** prop gets a string value.

  \- if **api** method of api is `POST` then **api** prop gets a object value.

\* Component use with **Data**

```vue
<template>
  <OCTable :columns="columns" :data="data"></OCTable>
</template>

<script setup>
const data = [];
const columns = [];
</script>
```

\* Component use with **API** method **POST**

```vue
<template>
  <OCTable :api="api" :columns="columns"> </OCTable>
</template>

<script setup>
const api = { url: "/api/enrollment/get", method: "POST" };
const columns = [];
</script>
```

\* Component use with **API** method **GET**

```vue
<template>
  <OCTable :api="api" :columns="columns"> </OCTable>
</template>

<script setup>
const api = "/api/enrollment/get";
const columns = [];
</script>
```

### \# **ref of Table**

- **ref** : use to call function from Table. It has function such as { **dt()**, **filter()**, **reload()** }.

```vue
<template>
  <OCTable ref="table" :columns="columns" :api="api">
    <template #headerLeft>
      <Button @click="onFilter">Filter</Button>
    </template>

    <template #headerRight>
      <Button @click="onReload">Reload</Button>
    </template>
  </OCTable>
</template>

<script setup>
const table = ref();

mounted(() => {
  console.log("table", table.value);
});

function onFilter() {
  table.value.filter();
}
function onReload() {
  table.value.reload();
}
</script>
```

### \# **Slots**

- **headerLeft** : use **#headerLeft** slot to add the custom content for headerLeft.

```vue
<template>
  <OCTable :columns="columns" :data="data">
    <template #headerLeft>
      <Button>Filter</Button>
    </template>
  </OCTable>
</template>
```

- **headerCenter** : use **#headerCenter** slot to set the custom content for headerCenter.

```vue
<template>
  <OCTable :columns="columns" :data="data">
    <template #headerCenter>
      <div>Header Center</div>
    </template>
  </OCTable>
</template>
```

- **headerRight** : use **#headerRight** slot to add the custom content for headerRight.

```vue
<template>
  <OCTable :columns="columns" :data="data">
    <template #headerRight>
      <div>Header Right</div>
    </template>
  </OCTable>
</template>
```

- **template** : use **#template** slot to hide table and custom content. If you use slot template the prop **showTemplate** is required.

```vue
<OCTable :columns="columns" :data="data" :show-template="true">
    <template #template="[data]">
        <div>{{data}}</div>
     </template>
</OCTable>
```

- **slot** : use slot name follow render in **columns** prop.

```vue
<template>
  <OCTable :columns="columns" :data="data">
    <template #title="props">
      <div class="bg-primary">
        {{ props.rowDate }}
      </div>
    </template>
    <template #name="props">
      <div>{{ props.rowData }}</div>
    </template>
  </OCTable>
</template>

<script setup>
const data = [];

const columns = [
  {
    title: "Id",
    data: "id",
    ordering: false,
    className: "min-width all",
  },
  {
    title: "Name",
    data: "name",
    className: "min-width",
  },
  {
    title: "",
    data: null,
    orderable: false,
    className: "min-width all",
    render: "#action",
  },
];
</script>
```

```vue
<template>
  <OCTable
    :columns="columns"
    :api="api"
    @update:data="updateData"
    @update:dataSrc="updateDataSrc"
  >
  </OCTable>
</template>

<script setup>
function updateData(d) {
  console.log("data", d);
}
function updateDataSrc(d) {
  console.log("dataSrc", d);
}
</script>
```

### \# **Component Button can use in table**

- **`<OCTblFilter/>`** : has **v-model** , **@on-click** and **@on-cancel**

```vue
<template>
  <OCTable ref="table" :columns="columns" :api="api">
    <template #headerLeft>
      <OCTblFilter
        v-model="isOpen"
        @on-click="onFilter"
        @on-cancel="onCancelFilter"
      >
      </OCTblFilter>
    </template>
  </OCTable>
</template>

<script setup>
const table = ref();
const isOpen = ref(false);

function onFilter() {
  table.value.filter();
}

function onCancelFilter() {
  console.log("cancel");
}
</script>
```

### \# **Props**

- **options** : use to customize on table and value is object `:options ="{}"` .

  \+ if you don't use **options** .The default set `options = { info: true, searching: true, paging: true, responsive: true, lengthMenu: [10, 25, 50, 100],}`

- **data** : use to get data from localData and value is array `:data="[]"` .

- **api** : use to get data from server . if method of api is `GET` **api** prop value is string `api="/api/enrollment/list"` and method of api is `POST` **api** prop value is object `:api="{ url:'/api/enrollment/list', method:'POST' }"`.

- **columns** : use to display th of table and value is array `:columns="[]"` .

- **selected-pk** : use to show checkbox in table and value is string `selected-pk="Id"` .

- **show-template** : use to hide table list for customize template and value is boolean `:show-template="true"` .

- **state-key** : use to save state data in table`state-key="stateKey"` .

### \# **Function Callback of Table**

- **update:data()** : use to filter data to api .

- **update:dataSrc()** : use to get data from api .

### \# **Clear State Data**

- you must to use **useOCTableDataStore()** and this store have 2 functions for clear `const ocTableStore = useOCTableDataStore()`

  \+ **clearData** use for only clear data and keep { Pages, Records, Search} .

  > ocTableStore.clearData('stateKey')

  \+ **clearAllData** use for only clear all data .

  > ocTableStore.clearAllData('stateKey')

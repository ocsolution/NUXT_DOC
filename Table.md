# OCTable

Display data in a table.

## Usage 

## Props

### + data
Use the `data` prop to set the data to display in the table. By default, the table will display all the fields of the rows.

```vue
<script setup>
const people = [{
  id: 1,
  name: 'Lindsay Walton',
  title: 'Front-end Developer',
  email: 'lindsay.walton@example.com',
  role: 'Member'
}, {
  id: 2,
  name: 'Courtney Henry',
  title: 'Designer',
  email: 'courtney.henry@example.com',
  role: 'Admin'
}, {
  id: 3,
  name: 'Tom Cook',  
  title: 'Director of Product',
  email: 'tom.cook@example.com',
  role: 'Member'
}]
</script>

<template>
  <OCTable :data="people" />
</template>
```

### + api
Use the `api` prop to get from server side to display in the table. but prop `columns` is required.
  - if **api** method of api is `GET` then **api** prop gets a string value.
  - if **api** method of api is `POST` then **api** prop gets a object value.

```vue
<template>
   <OCTable :api="api" :columns="columns"/>
</template>

<script setup>
// when api use with method GET
const api = 'api/table/list'

// when api use with method POST
const api = { url:'api/table/list', method:'POST' }

const columns = [
  { title: 'Code', data: 'Code', class: 'min-width' },
  { title: 'Name', data: 'Name', class: 'min-width' },
  { title: 'EnglishName', data: 'EnglishName', class: 'min-width' },
  { title: 'Action', data: null, class: 'min-width', render:'#action' },
]
</script>
```

### + columns
Use the `columns` prop to configure which columns to display. It's an array of objects with the following properties:
- **title**: Column header name shown in the table.
- **data**: Specifies which property of the row data this column displays. Can be dot notation ('user.name') or a function.
- **className**: Set custom class for cells in this column.
- **render**: Customize how cell content is rendered (raw HTML, formatting, etc).
- **orderable**: Allow/disallow sorting for this column. Default: true.
- **sortData**: Customize sorting more data for this column.
- **hidden**:  Allow/disallow hide this column. Default: false.
- **alignRight**: Allow/disallow text align right for this column. Default: false.

```vue
<template>
   <OCTable :data="data" :columns="columns"/>
</template>

<script setup>
const data = [
  { Id:1, Code:'Emp00001', Name:'ឡុង​ ឡងឌី', EnglishName:'Long LunDy', Age:24 },
  { Id:2, Code:'Emp00002', Name:'ផាន ឈៀងហេង', EnglishName:'Phang ChheangHeng', Age:24 },
]

const columns = [
  {
    title: "Employee",
    data: null,
    orderable: false,
    className: "all min-width",
    render: '#employee',
    sortData:[
      { title: 'Employee Code', data: 'Code' },
      { title: 'Employee Name', data: 'Name' },
      { title: 'Employee EnglishName', data: 'EnglishName' },
    ]
  },
  { title: '', data: 'Code', class: 'min-width', hidden: true,},
  { title: '', data: 'Name', class: 'min-width', hidden: true,},
  { title: '', data: 'EnglishName', class: 'min-width', hidden: true,},
  {
    title: "Age",
    data: "Age",
    alignRight: true,
    className: "min-width",
  },
  {
    title: "Actions",
    data: null,
    orderable: false,
    className: "all min-width",
    render:'#actions'
  }
]
</script>
```

### + options 
Usw the `options` allows customization of the table’s interface and available features. These `options` are set during initialization and control layout, behavior, and interactivity.
- **isScroll**: (Custom) A flag to conditionally enable scroll-related styles or logic in the component. Default: false.
- **scrollY**: Enables vertical scrolling and sets a fixed height (e.g., 400, '400px'). Automatically disables pagination if the height is large enough to show all rows. Default: 400.
- **scrollX**: Enables horizontal scrolling. Useful when the table width exceeds its container. Default: false
- **info**: Displays footer text such as "Total Records: 0". Default: true.
- **searching**: 	Enables the built-in search input for client-side filtering. Default: true.
- **paging**: Enables pagination and select record. Default: true.
- **reload**: Enables button reload. Default: true.
- **lengthMenu**: A dropdown menu allowing the user to select how many rows to show per page. Default: [10, 25, 50, 100].
- **pageLength**: Sets the default number of rows displayed per page. Default: 10.
  
You find more options in [datatable.net](https://datatables.net/reference/option/)

```vue
<script setup>
const optionDefault = {
    isScroll: true,
    scrollY: 400,
    scrollX: false,
    info: true,
    searching: true,
    paging: true,
    reload: true,
    responsive: {
      details: {
        renderer: DataTablesCore.Responsive.renderer.listHiddenNodes(),
      },
    },
    lengthMenu: [10, 25, 50, 100],
    pageLength: 10,

  };
</script>
```

### + selectedPk and v-model
The `selectedPk` defines the primary key field used to uniquely identify each row in the table (as a string). Use `v-model` to enable row selection in the table. The `v-model` will be an array containing the selected rows based on the `selectedPk` value.

```vue
<template>
   <OCTable v-model="selected" selectedPk="Code" :api="api" :columns="columns"/>
</template>

<script setup>
const api = { url:'api/table/list', method:'POST' }
const selected = ref()
const columns = [
  { title: 'Code', data: 'Code', class: 'min-width' },
  { title: 'Name', data: 'Name', class: 'min-width' },
  { title: 'EnglishName', data: 'EnglishName', class: 'min-width' },
  { title: 'Action', data: null, class: 'min-width', render:'#action' },
]
</script>
```

### + stateKey
Use the `stateKey` to enable `OCTable` to remember its state (including filters, sorting, and pagination) when navigating to a detail page and returning to the index page.
The `stateKey` must be a unique string used as the identifier for saving and restoring the table state.

```vue
<template>
   <OCTable stateKey="stateOCTable" :api="api" :columns="columns"/>
</template>

<script setup>
const api = { url:'api/table/list', method:'POST' }
const columns = [
  { title: 'Code', data: 'Code', class: 'min-width' },
  { title: 'Name', data: 'Name', class: 'min-width' },
  { title: 'EnglishName', data: 'EnglishName', class: 'min-width' },
  { title: 'Action', data: null, class: 'min-width', render:'#action' },
]
</script>
```

### + keyTable
Use the `keyTable` to identify a DOM element uniquely so Vue can efficiently re-render or re-create it when `keyTable` changes value.

```vue
<template>
  <OCWrapperPage>
    <OCBtn type="reload" color="reload" icon="reload" lable="Change Key" @click="keyTable = !keyTable"/>
    <OCTable :keyTable="" :api="api" :columns="columns"/>
  </OCWrapperPage>
</template>

<script setup>
const api = { url:'api/table/list', method:'POST' }
const keyTable = ref(false)
const columns = [
  { title: 'Code', data: 'Code', class: 'min-width' },
  { title: 'Name', data: 'Name', class: 'min-width' },
  { title: 'EnglishName', data: 'EnglishName', class: 'min-width' },
  { title: 'Action', data: null, class: 'min-width', render:'#action' },
]
</script>
```

### + showTemplate
Use the `showTemplate` to hide the default table rows and columns, and instead display a custom grid or card layout using a template. When `showTemplate` is set to `true`, you must also provide a `<template v-slot:template="[data]">` slot for rendering the custom content. Default: false.

```vue
<template>
   <OCTable stateKey="stateOCTable" :api="api" :columns="columns">
      <template #template="[data]">
        <div class="w-full grid grid-cols-[repeat(auto-fill,minmax(263px,1fr))] items-center gap-3">
          <div v-for="d in data">
            <div>{{d.Code}} • {{d.EnglishName}}</div>
          </div>
        </div>
      </template>
   </OCTable>
</template>

<script setup>
const api = { url:'api/table/list', method:'POST' }
const columns = [
  { title: 'Code', data: 'Code', class: 'min-width' },
  { title: 'Name', data: 'Name', class: 'min-width' },
  { title: 'EnglishName', data: 'EnglishName', class: 'min-width' },
  { title: 'Action', data: null, class: 'min-width', render:'#action' },
]
</script>
```

### + isTotalDetail
Use the `isTotalDetail` to hide the OCTableFooter. When `isTotalDetail` is set to `true`, the footer will be hidden. Default: false

### + haveBorder
Use the `haveBorder` to apply a border style to the `OCTable`. When `haveBorder` is set to `true`, the table will be displayed with borders. Default: false.

### + autoload
Use the `autoload` in combination with the `api` prop to control whether data is automatically loaded from the server. When `autoload` is set to `false`, data will not be fetched automatically. To manually trigger data loading, use the exposed `ref` and call the `reload` function. Default: true.

### + selectAllPk
Use the `selectAllPk` to display a "Select All" button that selects all rows in the table.The value of selectAllPk should be a string that matches the unique key property in `data` prop or data from `api` prop.

### + hideGroupBtnSelect
Use the `hideGroupBtnSelect` to hide the "Select All" button group. When set to `true`, the selection controls will not be displayed. Default: true.

## Slots
You can use `slots` to customize the header, the footer and data cells of the table.

### + headerTable
Use the `#headerTable` slot to customize top of header.

### + headerLeft

### + headerCenter

### + headerApplyFilter

### + headerRight

### + middleTable

### + template

### + loading

### + totalDetail

### + ShowDetailAfterTableOne

### + ShowDetailAfterTableTwo

### + Dynamic

## Emits

## Ref
Use to call function from Table. It has function such as { **dt()**, **filter()**, **reload()**, **responsive()** }.




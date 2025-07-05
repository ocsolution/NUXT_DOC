# Table

Display data in a table.

## Usage 

+ Use the `data` prop to set the data to display in the table. By default, the table will display all the fields of the rows.

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

+ Use the `api` prop to get from server side to display in the table. but prop `columns` is required.

### columns
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
  <div>
    <OCTable :data="data" :columns="columns"/>
  </div>
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








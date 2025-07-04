# Table

Display data in a table.

## Usage 

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

### columns
Use the `columns` prop to configure which columns to display. It's an array of objects with the following properties:
- **title**: The label to display in the table heade.
- **data**: The field to display from the row data.
- **className**: The class to apply to the column cells.
- **render**: 







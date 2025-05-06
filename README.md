# ANQ Server Data Table

A powerful server-side data table component for Vue 3 applications, built with Quasar Framework. This component provides a seamless way to handle server-side pagination, filtering, sorting, and data management in your Vue applications.

## Features

- Server-side pagination with customizable page sizes
- Advanced server-side filtering with a modal form
- Server-side sorting
- Built-in search functionality
- Row click events
- Customizable column definitions
- Responsive design
- Built with Vue 3 and Quasar Framework
- TypeScript support
- Customizable styling with Tailwind CSS
- Modal form integration
- Axios for API requests

## Installation

```bash
npm install anq-server-data-table
```

## Usage

```vue
<template>
  <anq-server-data-table
    :columns="columns"
    :link="apiEndpoint"
    :link-params="additionalParams"
    :title="'My Data Table'"
    :has-search="true"
    :has-filter="true"
    :show-page-size-select="true"
    :enable-row-click="true"
    :filter-modal-data="filterConfig"
    @row-click="handleRowClick"
    @get-data-successfuly="handleDataSuccess"
    @get-data-error="handleDataError"
  />
</template>

<script setup lang="ts">
import { AnqServerDataTable } from 'anq-server-data-table'

const columns = [
  { name: 'id', label: 'ID', field: 'id', sortable: true },
  { name: 'name', label: 'Name', field: 'name', sortable: true },
  // Add more columns as needed
]

const filterConfig = {
  fields: [
    {
      type: 'text',
      label: 'Name',
      urlParam: 'name'
    },
    {
      type: 'select',
      label: 'Status',
      urlParam: 'status',
      choices: [
        { label: 'Active', value: 'active' },
        { label: 'Inactive', value: 'inactive' }
      ]
    },
    {
      type: 'date',
      label: 'Created Date',
      urlParam: 'created_at'
    }
  ]
}

const handleRowClick = (row, index) => {
  console.log('Row clicked:', row, index)
}

const handleDataSuccess = (data) => {
  console.log('Data loaded successfully:', data)
}

const handleDataError = (error) => {
  console.error('Error loading data:', error)
}
</script>
```

## Props

| Prop | Type | Required | Description |
|------|------|----------|-------------|
| columns | QTableColumn[] | Yes | Array of column definitions |
| link | String | Yes | API endpoint URL |
| linkParams | Object | No | Additional URL parameters |
| title | String | No | Table title |
| loading | Boolean | No | Loading state of the table |
| hidePagination | Boolean | No | Hide pagination controls |
| flat | Boolean | No | Flat style for the table |
| square | Boolean | No | Square style for the table |
| hasSearch | Boolean | No | Enable search functionality |
| hasFilter | Boolean | No | Enable filter functionality |
| showPageSizeSelect | Boolean | No | Show page size selector |
| enableRowClick | Boolean | No | Enable row click events |
| filterModalData | FilterModalData | No | Configuration for filter modal |
| axiosInterceptor | AxiosInstance | No | Custom Axios instance |
| paginationResponseKeys | Object | No | Custom pagination response keys |
| orderingKey | String | No | Custom ordering parameter key |
| pageSizes | number[] | No | Available page sizes |

## Filter Modal Field Types

The component supports various field types in the filter modal:

- `text`: Text input
- `date`: Date picker
- `time`: Time picker
- `date-time`: Date and time picker
- `number`: Number input
- `boolean-checkbox`: Single checkbox
- `checkboxs`: Multiple checkboxes
- `radios`: Radio buttons
- `select`: Single select dropdown
- `select-multiple`: Multiple select dropdown

## Events

| Event | Parameters | Description |
|-------|------------|-------------|
| rowClick | (row: any, index: number) | Emitted when a row is clicked |
| getDataSuccessfuly | (data: any) | Emitted when data is successfully loaded |
| getDataError | (error: any) | Emitted when data loading fails |
| openFilter | () | Emitted when filter modal is opened |

## Slots

The component provides several slots for customization:

- `title`: Custom table title
- `search-input`: Custom search input
- `filter-btn`: Custom filter button
- `pagination`: Custom pagination controls
- `page-size`: Custom page size selector
- All Quasar QTable slots
- Filter modal slots (prefixed with `filter-modal-`)

## Dependencies

- Vue 3
- Quasar Framework
- Axios
- TypeScript
- Tailwind CSS
- anq-modal-form

## Development

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Author

- Aymane Nahji

## Repository

[GitHub Repository](https://github.com/AymaneNahji/anq-server-data-table)
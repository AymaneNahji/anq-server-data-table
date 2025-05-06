<template>
  <div class="q-pa-md">
    <AnqServerDataTable
      :columns="columns"
      :api-url="apiUrl"
      :pagination-response-keys="paginationKeys"
      :has-search="true"
      :has-filter="true"
      :filter-modal-data="filterModalData"
      title="Users List"
      link="users"
      @row-click="onRowClick"
    />
  </div>
</template>

<script setup lang="ts">
import AnqServerDataTable from './components/AnqServerDataTable.vue';
import { QTableColumn } from 'quasar';

// Define table columns
const columns: QTableColumn[] = [
  {
    name: 'id',
    label: 'ID',
    field: 'id',
    align: 'left',
    sortable: true
  },
  {
    name: 'name',
    label: 'Name',
    field: 'name',
    align: 'left',
    sortable: true
  },
  {
    name: 'email',
    label: 'Email',
    field: 'email',
    align: 'left',
    sortable: true
  },
  {
    name: 'status',
    label: 'Status',
    field: 'status',
    align: 'left',
    sortable: true
  }
];

// API configuration
const apiUrl = 'https://api.example.com/users';

// Pagination response keys mapping
const paginationKeys = {
  results: 'data',
  count: 'total',
  lastPage: 'last_page',
  next: 'next_page_url',
  previous: 'prev_page_url'
};

// Filter modal configuration
const filterModalData = {
  props: {
    title: 'Filter Users',
    okLabel: 'Apply Filters',
    cancelLabel: 'Cancel',
    formIsLoading: false
  },
  fields: [
    {
      type: 'text' as const,
      label: 'Name',
      urlParam: 'name'
    },
    {
      type: 'select' as const,
      label: 'Status',
      urlParam: 'status',
      choices: [
        { label: 'Active', value: 'active' },
        { label: 'Inactive', value: 'inactive' }
      ]
    },
    {
      type: 'date' as const,
      label: 'Created Date',
      urlParam: 'created_at'
    }
  ]
};

// Row click handler
const onRowClick = (row: any, index: number) => {
  console.log('Clicked row:', row, 'at index:', index);
};
</script>

<style>
.q-pa-md {
  padding: 16px;
}
</style>

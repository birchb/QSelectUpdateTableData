<template>
  <q-page class="flex flex-center">
    <div id="q-app" class="q-ma-lg q-pa-lg">
  <q-table
    title='Select Test'
    :data='tableData'
    :columns='columns'
    row-key="__index"
    class="table-editor">

    <template v-slot:body-cell-name="{row}">
      <td>
        <q-select
          :value='row'
          dense
          :options='options'
          option-label="name"
          option-value="id"
          map-options
          borderless
          @input="val => updateSelection(row.__index, val)"

        />
      </td>
    </template>
  </q-table>
</div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      options: [
        { name: 'Alice', id: '001' },
        { name: 'Bob', id: '002' },
        { name: 'Charlie', id: '003' },
        { name: 'David', id: '004' },
        { name: 'Elizabeth', id: '005' },
        { name: 'Frank', id: '006' },
        { name: 'George', id: '007' },
        { name: 'Hailey', id: '008' },
        { name: 'Imogene', id: '009' }
      ],
      tableData: [
        { name: 'Bob', id: '002' },
        { name: 'Alice', id: '001' },
        { name: 'Charlie', id: '003' },
        { name: 'Alice', id: '001' },
        { name: 'Charlie', id: '003' },
        { name: 'Bob', id: '002' }
      ],
      columns: [
        { name: 'id', label: 'ID', field: 'id', align: 'left' },
        { name: 'name', label: 'Name', field: 'name', align: 'left' }
        // { name: 'selected', label: 'Selected Name', field: 'name', align: 'left' }
      ]
    }
  },

  methods: {
    updateSelection (index, val) {
      console.log(val)
      this.tableData[index].name = val.name
      this.tableData[index].id = val.id
    }
  }
}
</script>

<style>
  .table-editor .q-table__middle {
    overflow: visible;
  }
</style>

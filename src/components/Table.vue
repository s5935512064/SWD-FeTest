<template>
  <div class="q-pa-md">
    <q-table
      class="my-sticky-dynamic"
      title="Assignment of Open Work Orders"
      :rows="row"
      :columns="columns"
      row-key="index"
      v-model:selected="selected"
    >
      <template class="q-pa-none" v-slot:top>
        <div class="full-width column">
          <div class="q-pa-sm row text-white" style="background-color: #21ba45">
            <p class="q-ma-sm text-subtitle2">
              <q-icon class="text-h5" name="assignment" /> Assignment of Open
              Work Orders
            </p>
            <q-space />
            <q-btn unelevated color="orange" label="Start WO" class="" />
          </div>
          <div class="text-white">
            <div class="row q-mt-sm items-center">
              <div class="q-ml-md">
                <q-chip
                  class="q-pa-md"
                  color="green-11"
                  text-color="black"
                  label="List"
                  icon="list"
                />
                <q-chip
                  class="q-pa-md"
                  color="green-11"
                  text-color="black"
                  label="Calendar"
                  icon="calendar_month"
                />
                <q-chip
                  class="q-pa-md"
                  color="green-11"
                  text-color="black"
                  label="User"
                  icon="group"
                />
              </div>
            </div>
            <div class="q-mt-sm">
              <p class="q-ml-lg text-black text-subtitle1 q-mb-none">
                List Table
              </p>
            </div>
          </div>
        </div>
      </template>
      <template v-slot:body="props">
        <q-tr :id="props.pageIndex + 1" :props="props">
          <q-td key="index" :props="props">
            {{ props.row.id }}
          </q-td>
          <q-td key="data" :props="props">
            {{ props.row.data }}
          </q-td>
          <q-td key="data2" :props="props">
            {{ props.row.data2 }}
          </q-td>
          <q-td key="timestamp" :props="props">
            {{ convetTimeStampToDate(props.row.timestamp) }}
          </q-td>
        </q-tr>
        <q-space />
      </template>
    </q-table>
  </div>
</template>

<script>
import { ref } from "vue";

import dayjs from "dayjs";

const columns = [
  {
    name: "index",
    label: "ID",
    field: "index",
    align: "center",
    sortable: true,
  },
  {
    name: "data",

    label: "Data 1",
    align: "center",
    field: "data",
    sortable: true,
  },
  {
    name: "data2",

    label: "Data 2",
    align: "center",
    field: "data2",
    sortable: true,
  },
  {
    name: "timestamp",
    align: "center",
    label: "Timestamp",
    field: "timestamp",
    sortable: true,
  },
];

export default {
  props: {
    row: Array,
  },
  setup(props) {
    const convetTimeStampToDate = (timeStamp) => {
      const date = dayjs(timeStamp).format("YYYY-MM-DD HH:MM:ss");
      return date;
    };

    return {
      columns,
      convetTimeStampToDate,
    };
  },
};
</script>

<style lang="sass">
.my-sticky-dynamic
  /* height or max-height is important */
  height: 450px

.q-table__top /* bg color is important for th; just specify one */
  padding: 0


  thead tr:first-child th /* bg color is important for th; just specify one */
    background-color: #fff
    color: #000


  thead tr th
    position: sticky
    z-index: 1
  /* this will be the loading indicator */
  thead tr:last-child th
    /* height of all previous header rows */
    top: 48px
  thead tr:first-child th
    top: 0
</style>

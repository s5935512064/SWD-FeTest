<template>
  <div class="maincontainer">
    <q-page class="column q-pa-md">
      <div class="q-pa-md">
        <div class="row q-gutter-md">
          <Card />
        </div>
      </div>
      <div class="col">
        <Table :row="rows" />
      </div>
    </q-page>
  </div>
</template>

<script>
import { ref, onMounted, defineComponent } from "vue";
import Card from "../components/Card.vue";
import Table from "../components/Table.vue";

import { getData } from "../data/service";

export default {
  components: {
    Card,
    Table,
  },
  setup() {
    const rows = ref([]);

    onMounted(async () => {
      rows.value = await getData();
    });

    return {
      rows,
    };
  },
};
</script>

<style lang="scss" scoped>
.maincontainer {
  width: 80vw;
  height: 100vh;
}
</style>

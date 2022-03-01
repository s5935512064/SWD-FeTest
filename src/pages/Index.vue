<template>
  <div class="maincontainer">
    <q-page class="column q-pa-md">
      <div class="q-pa-md">
        <div class="row justify-between">
          <Card />
        </div>
      </div>
      <div class="col">
        <Table />
      </div>
    </q-page>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import Card from "../components/Card.vue";
import Table from "../components/Table.vue";

export default {
  components: {
    Card,
    Table,
  },
};
</script>

<style lang="scss" scoped>
.maincontainer {
  width: 80vw;
  height: 100vh;
}
</style>

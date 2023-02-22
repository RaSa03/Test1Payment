<template lang="">
  <table class="table">
    <thead class="thead-dark"></thead>
    <thead class="thead-dark">
      <tr>
        <th @click="emitSortParams('id')" scope="col" class="col">
          Id
          <SortButtons
            :select="paramsOrder.id.select"
            :upDown="paramsOrder.id.upDown"
          />
        </th>
        <th @click="emitSortParams('brand')" scope="col" class="col">
          Brand
          <SortButtons
            :select="paramsOrder.brand.select"
            :upDown="paramsOrder.brand.upDown"
          />
        </th>
        <th @click="emitSortParams('age')" scope="col" class="col">
          Age
          <SortButtons
            :select="paramsOrder.age.select"
            :upDown="paramsOrder.age.upDown"
          />
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(car, id) in carsList" :key="car.id">
        <th scope="row">{{ car.id }}</th>
        <td>{{ car.brand }}</td>
        <td>{{ car.age }}</td>
      </tr>
    </tbody>
  </table>
</template>
<script setup>
import SortButtons from "./SortButtons.vue";
import { defineEmits } from "vue";
const emit = defineEmits(["sort"]);
const paramsOrder = {
  id: { select: false, upDown: false },
  brand: { select: false, upDown: false },
  age: { select: false, upDown: false },
};
const emitSortParams = (param) => {
  paramsOrder[param].upDown = !paramsOrder[param].upDown;
  for (const key in paramsOrder) {
    if (key !== param) paramsOrder[key].select = false;
    else paramsOrder[key].select = true;
  }
  const params = {
    sortBy: param,
    order: paramsOrder[param].upDown,
  };
  emit("sort", params);
};
defineProps({
  carsList: {
    type: Array,
    required: true,
  },
});
</script>
<style scoped>
.col {
  cursor: pointer;
  border: 2px solid #000;
  background: #f8f7f7;
}
</style>

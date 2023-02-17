<script setup>
import SearchModal from "@/components/SearchModal.vue";
import CarTable from "@/components/CarTable.vue";
import SortModal from "@/components/SortModal.vue";
import { onMounted, ref, computed } from "vue";

const URL = "https://my-json-server.typicode.com/RaSa03/FakeServer/cars?";
const cars = ref([]);

const getCarsList = async (sortParams = { sortBy: "id", order: false }) => {
  const response = await fetch(
    URL +
      new URLSearchParams({
        _sort: sortParams.sortBy,
        _order: sortParams.order ? "desc" : "asc",
      })
  ).catch((error) => {
    console.log(error.message);
  });
  cars.value = await response.json();
};

const searchWithParams = (params) => {
  if (params.id) {
    console.log("id");
    cars.value = cars.value.filter((car) => car.id == params.id);
  }
  if (params.brand) {
    console.log(params.brand);
    cars.value = cars.value.filter((car) => car.brand.includes(params.brand));
  }
  cars.value = cars.value.filter(
    (car) => car.age <= params.age.to && car.age >= params.age.from
  );
};

onMounted(() => getCarsList());
</script>

<template>
  <div class="container mt-5">
    <div class="row">
      <button @click="getCarsList" type="button" class="btn btn-light col">
        Весь список
      </button>
      <button
        type="button"
        class="btn btn-secondary col"
        data-bs-toggle="modal"
        data-bs-target="#sortModal"
      >
        Сортировка
      </button>
      <button
        type="button"
        class="btn btn-primary col"
        data-bs-toggle="modal"
        data-bs-target="#searchModal"
      >
        Поиск...
      </button>
    </div>
    <CarTable :carsList="cars" />
    <SortModal @sort="getCarsList" />
    <SearchModal @search="searchWithParams" />
  </div>
</template>

<style scoped></style>

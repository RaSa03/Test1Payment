<template lang="">
  <table class="table">
    <thead class="thead-dark"></thead>
    <thead class="thead-dark">
      <tr>
        <th scope="col">#</th>
        <th scope="col">Brand</th>
        <th scope="col">Age</th>
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
defineProps({
  carsList: {
    type: Array,
    required: true,
  },
});
</script>
<style lang=""></style>

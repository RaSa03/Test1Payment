<template>
  <div
    class="modal fade"
    id="sortModal"
    tabindex="0"
    aria-labelledby="sortModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="exampleModalLabel">
            Сортировка по:
          </h1>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="form-check">
            <input
              v-model="sortParams.sortBy"
              class="form-check-input"
              type="radio"
              name="exampleRadios"
              id="exampleRadios1"
              value="id"
              checked
            />
            <label class="form-check-label" for="exampleRadios1"> Id </label>
          </div>
          <div class="form-check">
            <input
              v-model="sortParams.sortBy"
              class="form-check-input"
              type="radio"
              name="exampleRadios"
              id="exampleRadios2"
              value="brand"
            />
            <label class="form-check-label" for="exampleRadios2"> Brand </label>
          </div>
          <div class="form-check">
            <input
              v-model="sortParams.sortBy"
              class="form-check-input"
              type="radio"
              name="exampleRadios"
              id="exampleRadios3"
              value="age"
            />
            <label class="form-check-label" for="exampleRadios3"> Age </label>
          </div>

          <div class="form-check">
            <input
              v-model="sortParams.order"
              class="form-check-input"
              type="checkbox"
              value=""
              id="flexCheckDefault"
            />
            <label class="form-check-label" for="flexCheckDefault">
              сортировка по убыванию
            </label>
          </div>
        </div>

        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Закрыть
          </button>
          <button
            @click="$emit('sort', sortParams)"
            type="button"
            class="btn btn-primary"
            data-bs-dismiss="modal"
          >
            Отсортировать
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";

const sortParams = ref({
  sortBy: "id",
  order: false,
});
</script>
<style lang=""></style>

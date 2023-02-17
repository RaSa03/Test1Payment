<template>
  <div
    class="modal fade"
    id="searchModal"
    tabindex="-1"
    aria-labelledby="searchModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="exampleModalLabel">Детали поиска</h1>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <div class="input-group mb-3">
            <span class="input-group-text" id="basic-addon1">ID</span>
            <input
              v-model="searchParams.id"
              type="text"
              class="form-control"
              aria-describedby="basic-addon1"
            />
          </div>

          <div class="input-group mb-3">
            <span class="input-group-text" id="basic-addon2">Brand</span>

            <input
              v-model="searchParams.brand"
              type="text"
              class="form-control"
              aria-describedby="basic-addon2"
            />
          </div>

          <div class="mb-3">
            <label for="basic-url" class="form-label">Age</label>
            <div class="input-group">
              <input
                v-model="searchParams.age.from"
                type="number"
                class="form-control"
                id="basic-url"
                placeholder="From"
                aria-describedby="basic-addon3"
              />
              <input
                v-model="searchParams.age.to"
                type="number"
                class="form-control"
                id="basic-url"
                placeholder="To"
                aria-describedby="basic-addon3"
              />
            </div>
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
            @click="$emit('search', searchParams)"
            type="button"
            class="btn btn-primary"
            data-bs-dismiss="modal"
          >
            Поиск
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";

const searchParams = ref({
  id: "",
  brand: "",
  age: {
    from: 0,
    to: 2023,
  },
});
</script>
<style lang=""></style>

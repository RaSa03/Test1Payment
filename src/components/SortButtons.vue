<template>
  <div class="btn-group">
    <div :class="{ selectup: !upDown && select }" class="up"></div>
    <div :class="{ selectdown: upDown && select }" class="down"></div>
  </div>
</template>
<script setup>
defineProps({
  upDown: {
    type: Boolean,
    required: true,
  },
  select: {
    type: Boolean,
    required: true,
  },
});
</script>
<style scoped>
.btn-group {
  display: inline-flex;
  flex-direction: column;
  margin-left: 10px;
}
.up {
  width: 0;
  height: 0;
  border-left: 7px solid transparent;
  border-right: 7px solid transparent;
  border-bottom: 14px solid #7b7b7b;
}
.down {
  width: 0;
  margin-top: 2px;
  height: 0;
  border-left: 7px solid transparent;
  border-right: 7px solid transparent;
  border-top: 14px solid #7b7b7b;
}

.selectup {
  border-bottom: 14px solid #4079ff;
}
.selectdown {
  border-top: 14px solid #4079ff;
}
</style>

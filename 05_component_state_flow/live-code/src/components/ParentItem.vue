<template>
  <div>
    <h4>Parent Item</h4>
    <div>{{ item.id }} : {{ item.name }}</div>
  </div>
</template>

<script setup>
defineProps({
  item: Object,
})

</script>

<style scoped>

</style>

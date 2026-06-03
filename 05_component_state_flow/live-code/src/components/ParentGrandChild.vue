<template>
  <div>
    <h3>Grand Child</h3>
    <p>My Parent Say : {{ myMsg }}</p>
    <p>Dynamic Props : {{ dynamicProps }}</p>
    <button @click="updateName"> 이름 변경해주세요 </button>
  </div>
</template>

<script setup>
defineProps({
  myMsg: String,
  dynamicProps: String
})

const emit = defineEmits(['updateName'])

const updateName = function () {
  emit('updateName')  // parentchild로 이벤트 발생
}

</script>

<style scoped>

</style>

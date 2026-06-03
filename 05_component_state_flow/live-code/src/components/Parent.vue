<template>
  <div>
    <h1>Parent Component</h1>
    <ParentChild my-msg="Hello Child~!" 
    @some-event="someCallback"
    @some-event2="someCallback"
    @emit-args="getNumbers"
    @update-name="updateName"
    />
    <div>이름 : {{ name }}</div>
    <hr>
    <ParentItem v-for="item in items" :key="item.id" 
      :item="item"
    />
    
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ParentChild from '@/components/ParentChild.vue'
import ParentItem from '@/components/ParentItem.vue'

const items = ref([
  { id: 1, name: '사과' },
  { id: 2, name: '바나나' },
  { id: 3, name: '딸기' }
])

const someCallback = function () {
  console.log('자식 컴포넌트로 부터 Some Event가 발생했습니다. ')
}

const getNumbers = function (...args) {
  console.log('자식으로 부터 받은 데이터 : ', args)
}


const name = ref('Alice')

const updateName = function () {
  name.value = 'Bella'
}

</script>

<style scoped>

</style>

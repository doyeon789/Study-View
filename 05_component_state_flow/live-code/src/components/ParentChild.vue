<template>
  <div>
    <h2>Parent Child Component</h2>
    <button @click="$emit('some-event')">클릭</button>
    <button @click="buttonClick">JS에서 emit 발생 클릭</button>
    <button @click="sendData">부모 컴포넌트로 데이터 전달</button>
    <h3>Parent's Say: {{ myMsg }}</h3>
    <hr>
    <ParentGrandChild :my-msg="myMsg" :dynamic-props="url"
      @update-name="updateName"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ParentGrandChild from '@/components/ParentGrandChild.vue'


const url = ref('https://google.com')

// defineProps(['myMsg'])  // 사용할 수 있지만 object를 권장
const props = defineProps({
                myMsg: String
              })

console.log(props.myMsg)  // 내부에서 prop 값에 접근하려면 defineProps를 변수로 할당할 필요가 있음

const emit = defineEmits(['someEvent2', 'emitArgs', 'updateName']) // 발생시킬 이벤트명 등록

const buttonClick = function () {
  console.log('커스텀 이벤트 발생!!')
  emit('someEvent2')  // JS 니까 카멜케이스!
}

const sendData = function () {
  emit('emitArgs', 1, 2, 3)
}

const updateName = function () {
  emit('updateName')  // parent로 이벤트 발생
}

</script>

<style scoped>

</style>

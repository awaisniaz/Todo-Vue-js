<script setup>
import { defineProps, ref } from 'vue'

let props = defineProps(['addTodo'])

const inputdata = ref('')

const updateInput = (e) => {
  console.log(e?.target?.value)
  inputdata.value = e?.target?.value
}
const addTodoList = () => {
  console.log(inputdata.value)
  props.addTodo(inputdata.value)
  inputdata.value = ''
}
</script>
<template>
  <div class="form">
    <input
      type="text"
      placeholder="New Task"
      :value="inputdata.value"
      @change="updateInput"
    /><button @click="addTodoList">
      <i class="fas fa-plus"></i>
    </button>
  </div>
</template>
<style scoped>
.form {
  position: relative;
  margin: 0 0 30px;
}
input[type='text'] {
  width: 100%;
  height: 50px;
  font: 15px/1.4 'Poppins', sans-serif;
  padding: 15px;
  background: #f3f3f3;
  color: #333;
  border: 1px solid transparent;
  border-radius: 10px;
  transition: border 0.3s linear;
}
.form button {
  background: none;
  border: none;
  color: #4ec5c1;
  font-size: 18px;
  position: absolute;
  top: 50%;
  right: 20px;
  transform: translateY(-50%);
}
</style>

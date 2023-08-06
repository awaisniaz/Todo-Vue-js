<script setup>
import AddTask from './AddTask.vue'
import listofTask from './listofTask.vue'
import { ref } from 'vue'

const tasklist = ref([
  {
    name: 'Watching Netflix',
    complete: true,
    id: 0,
    date: '06-08-2023'
  },
  { name: 'Learn Vue Js', complete: false, id: 1, date: '06-08-2023' }
])

const addTodo = (item) => {
  console.log(item)
  let add = [
    ...tasklist.value,
    { name: item?.text, date: item.date, complete: false, id: tasklist.value.length }
  ]
  tasklist.value = add
  numberOfCompelet.value = tasklist.value.filter((item) => item.complete == false).length
}
const deleteItem = (id) => {
  let itemdeleted = tasklist.value.filter((item) => item.id != id)
  tasklist.value = itemdeleted
}

const clearAll = () => {
  tasklist.value = []
}
const markAllCompleted = () => {
  tasklist.value = tasklist.value.map((item) => {
    return { ...item, complete: true }
  })
}
const numberOfCompelet = ref(tasklist.value.filter((item) => item.complete == false).length)
</script>
<template>
  <div class="container">
    <div class="task">
      <div class="title"><h1>To Do List</h1></div>
      <AddTask :addTodo="addTodo" />
      <listofTask
        v-bind:tasklist="tasklist"
        v-bind:numberOfCompelet="numberOfCompelet"
        :deleteItem="deleteItem"
        :markAllCompleted="markAllCompleted"
        :clearAll="clearAll"
      />
    </div>
  </div>
</template>
<style scoped>
.container {
  max-width: 480px;
  margin: 0 auto;
  padding: 0 15px;
}
.task {
  background: #fff;
  border-radius: 25px;
  padding: 30px;
  box-shadow: 0px 0px 40px 0px rgba(0, 0, 0, 0.1);
}

.title {
  text-align: center;
  margin: 0 0 20px;
}
</style>

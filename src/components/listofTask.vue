<script setup>
import { defineProps } from 'vue'
const props = defineProps([
  'tasklist',
  'numberOfCompelet',
  'deleteItem',
  'markAllCompleted',
  'clearAll'
])
</script>
<template>
  <!-- task lists -->
  <div class="taskItems">
    <ul>
      <li v-for="item in props.tasklist" v-bind:key="item.name">
        <button :class="{ complete: item.complete }">{{ item.name }} {{ item.id }}</button>
        <button @click="deleteItem(item.id)"><i class="far fa-trash-alt"></i></button>
      </li>
    </ul>
  </div>
  <!-- buttons -->
  <div class="clearBtns">
    <button @click="markAllCompleted">Clear completed</button>
    <button @click="clearAll">Clear all</button>
  </div>
  <!-- pending task -->
  <div class="pendingTasks">
    <span>Pending Tasks: {{ props.numberOfCompelet }} </span>
  </div>
</template>
<style scoped>
.complete {
  text-decoration: line-through;
}
</style>

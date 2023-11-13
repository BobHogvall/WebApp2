<script setup>
import CloudButton from './CloudButton.vue';
const props = defineProps(['toDo']);
//const check true or false
</script>

<template>
  <li>
    <h4 class="label">To Do:</h4>
    <h1>{{ props.toDo.name }}</h1>
    <h4 class="label">Time Estimate:</h4>
    <h1>{{ props.toDo.time }}</h1>
    <CloudButton @cloud-click="$emit('itemDelete')" buttonText="remove" />
  </li>
</template>

<style scoped>
li {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  padding-left: 40px;
  gap: 20px;
  width: 100%;
  text-transform: uppercase;
  align-items: center;
  border: 2px solid #a9cadc;
  background-color: rgb(255 255 255 / 50%);
  margin-bottom: 10px;
 
}


</style>

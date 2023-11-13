<script setup>
import CloudButton from './CloudButton.vue';
import { ref } from 'vue';
import ToDoItem from './ToDoItem.vue';

const List = ref([]);
const name = ref('');
const time = ref('');
const priority = ref('');
const errorMessage = ref('');
let itemId = 0;

//generate id
const addItem = () => {
  if (name.value === '' || time.value === '' || priority.value === '') {
    errorMessage.value = 'Please fill out all fields';
    name.value = '';
    time.value = '';
    priority.value = '';
    return;
  } else {
    const myObject = {
      id: itemId++,
      name: name.value,
      time: time.value,
      priority: priority.value
    };

    List.value.push(myObject);

    name.value = '';
    time.value = '';
    priority.value = '';
  }
};

const removeItem = (item) => {
  List.value = List.value.filter((remove) => remove !== item);
};
</script>

<template>
  <div class="main-container">
    <div class="forms">
      <div class="form-1">
        <h3>To Do:</h3>
        <input v-model="name" type="text" placeholder="what:" class="input-1" />
      </div>
      <div class="form-2">
        <h3>Time Estimate:</h3>
        <input v-model="time" type="text" placeholder="how long:" class="input-2"/>
      </div>
      <div class="form-3">
        <h3>Priority:</h3>
        <select v-model="priority" placeholder="importance" class="input-3">
          <option value="low">Low</option>
          <option value="high">High</option>
        </select>
      </div>
      <CloudButton @cloud-click="addItem" buttonText="Add" />
    </div>
    <p class="error-message">{{ errorMessage }}</p>
    <div class="lists">
      <ul class="list">
        <h2>High Priority:</h2>
        <ToDoItem
          v-for="item in List.filter((item) => item.priority === 'high')"
          :key="item"
          :toDo="item"
          @itemDelete="removeItem(item)"
        />
      </ul>
      <ul class="list">
        <h2>Low Priority:</h2>
        <ToDoItem
          v-for="item in List.filter((item) => item.priority === 'low')"
          :key="item"
          :toDo="item"
          @itemDelete="removeItem(item)"
        />
      </ul>
    </div>
  </div>
</template>

<style scoped>
*,
*:before,
*:after {
  box-sizing: border-box;
}
.main-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.labels {
  display: flex;
  justify-content: space-around;
  text-align: center;
  width: 60%;
}

.forms {
  display: flex;
  justify-content: center;
  text-align: center;
  align-items: end;
  z-index: 10000;
  position: relative;
  gap: 15px;
  width: 60%;
}

input,
select {
  width: 15rem;
  padding: 1em 1em;
  border: none;
  border-radius: 17px;
}

.input-1 {
  box-shadow: 0px 0px 15px 8px rgb(152 191 211 / 60%);
}

.input-2 {
  box-shadow: 0px 0px 15px 8px rgba(138, 185, 209, 0.6);
}

.input-3 {
  box-shadow: 0px 0px 15px 8px rgba(123, 171, 195, 0.6);
}

input:hover {
  background-color: #f0efef;
}

select {
  padding: 1em 1em;
}

p {
  z-index: 1000;
}

.label {
  margin-top: 0;
  margin-bottom: 10px;
}

.lists {
  display: flex;
  justify-content: space-between;
  gap: 20px;
  width: 80%;
}

ul {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  padding-left: 0;
  width: 80%;
  list-style: none;
  text-align: center;
  z-index: 9999;
}

.error-message {
  text-align: center;
}
</style>

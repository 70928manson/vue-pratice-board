<script setup>
  // composition api
  import { ref, onMounted } from 'vue';

  const message = ref("yoyo");
  const status = ref("active");
  const tasks = ref(["Task One", "Task Two", "Task Three"]);
  const newTask = ref("default");

  const changeStatus = () => {
    if (status.value === 'active') {
      status.value = 'pending';
    } else if (status.value === 'pending') {
      status.value = 'inactive';
    } else {
      status.value = 'active';
    }
  };

  const addTask = () => {
    if (newTask.value.trim() !== "") {
      tasks.value.push(newTask.value);
      newTask.value = "";
    }
  };

  const deleteTask = (index) => {
    tasks.value.splice(index, 1) // start, delete count
  };

  onMounted(async () => {
    try {
      const response = await fetch("https://jsonplaceholder.typicode.com/todos");
      const data = await response.json();
      tasks.value = data.map((task) => task.title);
    } catch (err) {
      console.log("error", err);
    }
  })
</script>

<template>
  <h1>Vue Tasks Board</h1>
  <p>{{ message }}</p>
  <p v-if="status === 'active'">status is active</p>
  <p v-else-if="status === 'pending'">status is pending</p>
  <p v-else>status is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" >
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>

  <br />
  <button @click="changeStatus">Change Status</button>
</template>

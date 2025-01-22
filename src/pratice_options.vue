<script>
// options api
export default {
  data() {
    return {
      message: "yoyo",
      status: "active",
      tasks: ["Task One", "Task Two", "Task Three"],
      link: "https://google.com"
    }
  },
  methods: {
    changeStatus() {
      if (this.status === 'active') {
        this.status = 'pending';
      } else if (this.status === 'pending') {
        this.status = 'inactive';
      } else {
        this.status = 'active';
      };
    }
  }
}
</script>

<template>
  <h1>Vue Jobs</h1>
  <p>{{ message }}</p>
  <p v-if="status === 'active'">status is active</p>
  <p v-else-if="status === 'pending'">status is pending</p>
  <p v-else>哈哈使用者不在線上</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a :href="link">Click for Google</a>
  <br />
  <button @click="changeStatus">Change Status</button>
</template>

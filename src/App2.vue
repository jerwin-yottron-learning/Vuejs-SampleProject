<script>
export default {
  data() {
    return {
      name: " jerwin",
      status: 'active',
      tasks: ['Task One', 'Task Two', 'Task Three','Task four'],
      link: "https://google.com",
    };
  },
  methods: {
    toggleStatus() {
      if (this.status === 'active') {
        this.status = 'pending'
      } else if (this.status === 'pending') {
        this.status = 'inactive';
      } else {
        this.status ="";
      }
    },
  },
};

</script>


<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }} </li>
    <!-- <a v-bind:href="link">Click for google</a> -->
    <a :href="link">click for google</a>
  </ul>
  <br>
  <!-- <button v-on:click="toggleStatus">changestatus</button> -->
  <button @click="toggleStatus()">changestatus</button>

</template>

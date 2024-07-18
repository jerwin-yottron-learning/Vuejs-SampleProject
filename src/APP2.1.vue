<script setup>
/*
To make this reactive in composition api we need to import the ref and make this reactive and 
also remove "this" keyword and add "value"  
2.for composition api we dont need to return anything just in script mention setup
*/
import { ref,onMounted } from 'vue';
// export default { //noo need this to setup 
  // setup(){ //this we will mention in the top of the script
    const name = ref('Varun Prasand');
    const status = ref('active');
    const tasks = ref(['TasK one', 'Task Two','Task Three']);
  const toggleStatus = ()=>{
    if (status.value === 'active') {
        status.value = 'pending'
      } else if (status.value === 'pending') {
        status.value = 'inactive';
      } else {
        status.value ="";
      }
  };
  const newTask =ref("dssddddddddd");
 
// Function to add a new task
const addTask = () => {
  if (newTask.value.trim() !=='') {
    tasks.value.push(newTask.value);
    newTask.value = ""; // Clear the input after adding the task
  }
};


const deleteTask =(index)=>{
  tasks.value.splice(index,1);
}
//no need to return anything
  // return{
  //   name,
  //   status,
  //   tasks,
  //   toggleStatus
  // }

onMounted (async()=>{
  try{
    const response = await fetch('https://jsonplaceholder.typicode.com/todos');
    console.log(response);
    const data =await response.json();
    console.log(data);
    tasks.value = data.map((task)=> task.title);
  }catch(error){
    console.log("error fetching tasks")
  }
})
</script>


<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add task</label>
    <input type="text" id="newTask " name="newTask" v-model="newTask"/>
 <button type="submit">submit</button>
  
  </form>

  <h3>Tasks:</h3>
  <ul>
    <!-- <li v-for="task in tasks" :key="task">{{ task }}  -->
      <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)" >X</button>
    </li>
  
  </ul>
  
  <br>
  <!-- <button v-on:click="toggleStatus">changestatus</button> -->
  <button @click="toggleStatus()">changestatus</button>

</template>

<script>
  export default{
    data(){
      return {
        name: 'John Doe',
        status: true,
        newstatus: 'active',
        tasks: ['Task One', 'Task Two', 'Task Three'],
        link: 'https://google.com',
      }
    },
    methods:{

      toggleStatus(){
        if(this.newstatus === 'active'){
          this.newstatus = 'pending';
        }else if(this.newstatus === 'pending'){
          this.newstatus = 'inactive';
        }else{
          this.newstatus = 'active';
        }
      }

    }
  }

</script>

<template>
  <h1>{{ name }}</h1>

  <!-- Using Boolean -->
  <p v-if="status">User is Active (Online)</p>
  <p v-else>User is Inactive (Offline)</p>

  <!-- Using String -->
  <p v-if="newstatus === 'active'">User is Active</p>
  <p v-else-if="newstatus === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>

  <!-- Loop Through Arrays -->
  <h3>Tasks:</h3>
    <ul>
      <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
  
  <a v-bind:href="link">Click for Google</a>
  <a :href="link">Click for Google</a>
  
  <br />

  <button v-on:click="toggleStatus">Change Status</button>
  <button @click="toggleStatus">Change Status</button>

</template>
<template>
    <div>
<table class="table">
  <thead>
    <tr>
      <th scope="col">id</th>
      <th scope="col">Name</th>
      <th scope="col">Description</th>
      <th scope="col">Priority</th>
      <th scope="col">Status</th>
    </tr>
  </thead>
  <tbody>
      
    <tr v-for="item in tasks.tasks" :key="item.id">
      <th scope="row">{{item.id}}</th>
      <td>{{item.name}}</td>
      <td>{{item.description}}</td>
      <td>{{item.priority}}</td>
      <td>{{item.status}}</td>
    </tr>
  </tbody>
</table>

    </div>
</template>

<script>
export default {
    name: 'Tasklist',
    data() {
        return{
            tasks:[],
        }
    },

mounted() {
    this.getTask()     
},
methods: {
    getTask: async function() {
    try {
        const data = await fetch('http://127.0.0.1:8000/api/tasks/')
        this.tasks = await data.json()
        console.log(this.tasks)
        }catch (error) {
        console.error(error)
        }
    }
}   
}
</script>
<template>
  <div class="container">
    <h1 class="mt-5 items-center">my to do list </h1>
    <div class="d-flex">
        <input v-model="task" type="text" class="form-control" placeholder="enter the text" />
        <button @click="submitTask()" class="btn btn-warning">Submit</button>

    </div>

    <!-- Table -->
    <table class="table table-bordered mt-4">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col">#</th>
      <th scope="col">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task, index) in tasks" :key="index">
      <th scope="row">{{task.name}}</th>
      <td>{{task.status}}</td>
      <td>
        <div class="items-center" @click="editTask(index)">
          <svg xmlns="http://www.w3.org/2000/svg"  width="20" height="30" viewBox="0 0 600 300"><!--!Font Awesome Free 6.6.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M453.3 19.3l39.4 39.4c25 25 25 65.5 0 90.5l-52.1 52.1s0 0 0 0l-1-1s0 0 0 0l-16-16-96-96-17-17 52.1-52.1c25-25 65.5-25 90.5 0zM241 114.9c-9.4-9.4-24.6-9.4-33.9 0L105 217c-9.4 9.4-24.6 9.4-33.9 0s-9.4-24.6 0-33.9L173.1 81c28.1-28.1 73.7-28.1 101.8 0L288 94.1l17 17 96 96 16 16 1 1-17 17L229.5 412.5c-48 48-109.2 80.8-175.8 94.1l-25 5c-7.9 1.6-16-.9-21.7-6.6s-8.1-13.8-6.6-21.7l5-25c13.3-66.6 46.1-127.8 94.1-175.8L254.1 128 241 114.9z"/></svg>


      </div> 
    </td>
      <td>  

        <div class="items-center"> 
                    <svg xmlns="http://www.w3.org/2000/svg" @click="deleteTask(index)" width="20" height="30" viewBox="0 0 600 300"><!--!Font Awesome Free 6.6.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.--><path d="M135.2 17.7L128 32 32 32C14.3 32 0 46.3 0 64S14.3 96 32 96l384 0c17.7 0 32-14.3 32-32s-14.3-32-32-32l-96 0-7.2-14.3C307.4 6.8 296.3 0 284.2 0L163.8 0c-12.1 0-23.2 6.8-28.6 17.7zM416 128L32 128 53.2 467c1.6 25.3 22.6 45 47.9 45l245.8 0c25.3 0 46.3-19.7 47.9-45L416 128z"/></svg>

        </div>


      </td>
    </tr>

  </tbody>
</table>


  </div>
</template>

<script>
export default {

    data() {
        return {
            editedTask: null,
            task: "",
            tasks: [
                {
                    name: 'weak up ',
                    status: 'to do'

            },
            {
                    name: 'eat beakfast',
                    status: 'to do'

            }
        ]
        }
    },
    methods: {

        submitTask() { 
            if(this.task.length === 0) return;

          
            if(this.editedTask === null) {
           
            
            this.tasks.push({
                name: this.task,
                status: 'todo'
                
            });
             }  else {
             this.task = this.tasks[this.editedTask].name
             this.editedTask = null
             
             }
        
            this.task= '';
        },
        deleteTask(index) {
        this.tasks.splice(index, 1)
        },
        editTask(index) {
        this.task = this.tasks[index].name;
        this.editedTask = null
        }
      
    }

}
</script>

<style>

</style>
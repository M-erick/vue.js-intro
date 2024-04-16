<template>
  <div  class="container">

    <h2 class="text-center mt-5">My Vue Todo App</h2>   
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter task" class="form-control">
      <button  @click="submitTask" class="btn btn-warning rounded-0">SUBMIT</button>

    </div>

    <!-- Tables for task -->
    <table class="table table-bordered">
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">#</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task,index) in tasks" :key="index">
      <td >{{task.name}}</td>
      <td>{{task.status}}</td>
      <td>
      <div class="text-center" @click="editTask(index)">
      <span class="fa fa-pen"></span>
      </div>
      </td>
      <td> <div class="text-center" @click="deleteTask(index)">
      <span class="fa fa-trash"></span>
      </div></td>
    </tr>
    
   
  </tbody>
</table>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    msg: String
  },
  data(){
    return {
      task:'Hello World',

      tasks:[
        {name:'study vue.js',
        status:'to-do'},
         {name:'study React',
        status:'to-do'},
      ]
    }
  },
  methods:{
  submitTask(){
  if(this.task.length===0) return ;
  this.task.push({
  name:this.task,
  status:'to-do'
  });
  this.task ='';
  },
  deleteTask(index){
  this.task.splice(index,1);
  },
  editTask(index){
  this.task = this.task[index].name},

  }
}
</script>


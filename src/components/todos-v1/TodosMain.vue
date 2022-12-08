<script>
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap-icons/font/bootstrap-icons.css';
import './page_styles.css';

export default {
  data() {
    return {
      task: '',
      errorMsg: '',
      editedTask: null,
      isDisabledAdd: false,
      isDisabledX: false,
      stat: 1,
      tasks: [
        {
          name: 'Stay sane',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
        {
          name: 'Get your shit together',
          status: 'To-do',
        },
      ],
    };
  },
  methods: {

    

    submitTask() {
      if(this.task.length === 0) return;

      if(this.editedTask === null){
      this.tasks.push({
        name: this.task,
        status: 'to-do',
        
      });
      }else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
      this.task = '';
      this.isDisabledX = false;
      
    },

    deleteTask(index){
      this.tasks.splice(index, 1);

    },

    changeStat(index){
      if(this.tasks[index].status==='To-do'){
        this.tasks[index].status = 'Done';
      }else{
        this.tasks[index].status = 'To-do';
      }

    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;
      this.isDisabledX = true;

    },
    
    onInput (event) {
      const value = Number(event.target.value);
      if (isNaN(value)) {
        
        // nope
      } else {
        // v poradku
      }


      
      this.task = event.target.value;
      


      if(isNaN(this.task)){
        console.log("This is not valid input");
        this.isDisabledAdd = true;
        
      }else{
        this.isDisabledAdd = false;
        
      }
    },  
  },
};

</script>

<template>
  <div class="app">
   
   <div class="mt-3 text-center">
      <h1 class="user-select-none">Tasks for today</h1>
      <h2>{{ errorMsg }}</h2>
   </div>

    <div>
      <div class="mt-3 d-flex justify-content-center">
        <div class="add-new-form">
        <div class="d-flex">
            <input type="text" :value="task" v-on:keyup.enter="submitTask" @input="onInput" class="form-control" aria-describedby="tasklHelp" placeholder="Enter your task here..">
            <button type="button" class="btn btn-outline-success ms-2" :disabled='isDisabledAdd' @click="submitTask">Add</button>
          </div>
          <div id="taskHelp" class="form-text">Let your dreams come true...</div>
        </div>
      </div>
    </div>
   
    <div class="mt-3 d-flex flex-wrap justify-content-center ">
      <div class="card m-2" style="width: 18rem;" v-for="(task, index) of tasks" :key="index">
        <div class="card-body">
          <h5 class="list-group-item">{{ task.name }}</h5>
          <ul class="list-grup-flush">
            <li type="button" class="btn btn-outline-secondary ms-1" @click = "changeStat(index)"> {{ task.status }}  </li>
            <li type="button" class="btn btn-outline-secondary ms-1" @click = "editTask(index)">Edit</li>
            <li type="button" class="btn btn-outline-danger ms-1" :disabled="isDisabledX" @click = "deleteTask(index)">Delete </li>
          </ul>
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped>
.add-new-form {
  max-width: 500px;
}
</style> 
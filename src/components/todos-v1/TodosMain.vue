<script>
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
        /*{
          name: 'Stay sane',
          status: 'to-do'
        },
        {
          name: 'Get your shit together',
          status: 'to-do'
        },*/
      ]
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
      if(this.tasks[index].status==='to-do'){
        this.tasks[index].status = 'done';
      }else{
        this.tasks[index].status = 'to-do';
      };

    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;
      this.isDisabledX = true;

    },
    
    onInput (event) {
      this.task = event.target.value;
      
      if(isNaN(this.task)){
        console.log("This is not valid input");
        this.isDisabledAdd = true;
        
      }else{
        this.isDisabledAdd = false;
        
      }
    },  
  },
}
console.log(0+1)
</script>

<template>
  <div class="container">
    <div class="app">
      <div>
        <h1 class="app-title">Tasks for today</h1>
        <h2>{{ errorMsg }}</h2>
      </div>
      <div class="form">
        <input type="text" :value="task" v-on:keyup.enter="submitTask" @input="onInput" placeholder="Enter your task here..">
        <button :disabled='isDisabledAdd' @click="submitTask">Add</button>
      </div>
      <div class="line">
        <tr v-for="(task, index) of tasks" :key="index">
          <td>{{ task.name }}</td>
          <td><button @click = "changeStat(index)"> {{ task.status }} </button> </td>
           <td><button :disabled="isDisabledX" @click = "deleteTask(index)">X</button></td>
           <td><button @click = "editTask(index)">Edit</button></td>
          </tr>
        <tr> </tr>
        </div>
    </div>
  </div>
  
</template>

<style scoped>
.container {
  height: 100%;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.form {
  display: flex;
}
.line {
  padding: 4px;
}
.h1 {
  position: center;
}
</style> 
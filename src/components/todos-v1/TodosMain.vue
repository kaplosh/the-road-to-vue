<script>
import './page_styles.css';

export default {
  data() {
    return {
      task: '',
      editedTask: null,
      lines: [],
      tasks: [
        {
          name: 'Stay sane',
          status: 'to-do'
        },
        {
          name: 'Get your shit together',
          status: 'to-do'
        },
      ]
    };
  },
  methods: {
    submitTask() {
      if(this.task.length === 0) return;

      if(this.editedTask === null){
      this.tasks.push({
        name: this.task,
        status: 'to-do'
      });
      }else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }
      this.task = '';
      
    },

    deleteTask(index){
      this.tasks.splice(index, 1);

    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;

    },
    
    onInput (event) {
      this.task = event.target.value;
      console.log(event.target.value);
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="app">
      <div>
        <h1 class="app-title">Tasks for today</h1>
      </div>
      <div class="form">
        <input type="text" :value="task" @input="onInput">
        <button @click="submitTask">Next</button>
      </div>
      <div class="line">
        <tr v-for="(task, index) of tasks" :key="index">
          <td>{{ task.name }}</td>
          <td>{{ task.status }}</td>
           <button @click = "deleteTask(index)">X</button>
           <button @click = "editTask(index)">Edit</button>
          </tr>
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

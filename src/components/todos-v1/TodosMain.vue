<script>
import './page_styles.css';

export default {
  data() {
    return {
      text: '!',
      lines: [],
    };
  },
  methods: {
    nextLine() {
      this.lines.push(this.text);
      this.text = '';
    },
    deleteLine(index) {
      
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
        <input type="text" v-model="text">
        <button v-on:click="nextLine">Next</button>
      </div>
      <div class="line">
        <div v-for="(line, index) of lines" :key="index">
          {{ line }}
        <li v-on:click="deleteLine($index)" class="line-item" v-bind:class="{ 'line-item--deleted': item.deleted}"> {{ line }} <span class="item-delete">X</span></li>
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

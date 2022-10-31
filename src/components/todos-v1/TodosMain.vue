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
  },
};
</script>

<template>
  <div class="container">
    <div class="app">
      <div class="form">
        <input type="text" v-model="text">
        <button v-on:click="nextLine">Next</button>
      </div>
      <div class="line">
        <div v-for="(line, index) of lines" :key="index">
          {{ line }}
        </div>
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
</style>

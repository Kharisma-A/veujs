<template>
    <div>
      <h1>{{ count }}</h1>
      <button @click="increment">Tambah</button>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {  
      const count = ref(0);
  
      const increment = () => {
        count.value++;
      };
  
      return { count, increment };
    }
  };
  </script>
  
  <style>
  button {
    padding: 10px;
    background-color: green;
    color: white;
    border: none;
    cursor: pointer;
    font-size: 16px;
    margin-top: 10px;
  }
  </style>
  
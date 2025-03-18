<template>
    <div>
      <h1>Form Binding dengan v-model</h1>
      <input v-model="name" placeholder="Masukkan nama" />
      <p>Nama Anda: {{ name }}</p>
  
      <select v-model="selected">
        <option disabled value="">Pilih warna favorit</option>
        <option>Merah</option>
        <option>Biru</option>
        <option>Hijau</option>
      </select>
      <p>Warna Favorit Anda: {{ selected }}</p>
  
      <button @click="submitForm">Kirim</button>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const name = ref('');
      const selected = ref('');
  
      const submitForm = () => {
        alert(`Nama: ${name.value}\nWarna Favorit: ${selected.value}`);
      };
  
      return { name, selected, submitForm };
    }
  };
  </script>
  
  <style>
  input, select {
    display: block;
    margin: 10px 0;
    padding: 8px;
    font-size: 16px;
  }
  
  button {
    padding: 10px;
    background-color: green;
    color: white;
    border: none;
    cursor: pointer;
  }
  </style>
  
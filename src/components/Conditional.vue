<template>
    <div class="container">
      <div v-if="!isLoggedIn">
        <h2>Silakan Login</h2>
        <input type="text" v-model="username" placeholder="Masukkan username" />
        <input type="password" v-model="password" placeholder="Masukkan password" />
        <button @click="login" class="btn">Login</button>
      </div>
  
      <div v-else>
        <h2>Selamat Datang, {{ username }}!</h2>
        <p>Anda sekarang masuk ke dashboard pengguna.</p>
        <button @click="logout" class="btn-logout">Logout</button>
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const username = ref("");
      const password = ref("");
      const isLoggedIn = ref(false);
  
      const login = () => {
        if (username.value && password.value) {
          isLoggedIn.value = true;
        } else {
          alert("Silakan isi username dan password!");
        }
      };
  
      const logout = () => {
        isLoggedIn.value = false;
        username.value = "";
        password.value = "";
      };
  
      return { username, password, isLoggedIn, login, logout };
    }
  };
  </script>
  
  <style>
  /* Styling modern */
  .container {
    text-align: center;
    margin-top: 50px;
    font-family: 'Arial', sans-serif;
  }
  
  input {
    display: block;
    margin: 10px auto;
    padding: 8px;
    width: 200px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  .btn {
    background-color: #27ae60;
    color: white;
    font-size: 16px;
    padding: 8px 16px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .btn-logout {
    background-color: #e74c3c;
    color: white;
    font-size: 16px;
    padding: 8px 16px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .btn:hover {
    background-color: #219150;
  }
  
  .btn-logout:hover {
    background-color: #c0392b;
  }
  </style>
  
<template>
    <div class="container">
      <h1>Event Listener dengan Vue</h1>
      
      <!-- Button dengan efek animasi -->
      <button @click="incrementCounter" class="btn">
        <i class="fas fa-hand-pointer"></i> Klik Saya ({{ counter }})
      </button>
  
      <!-- Teks berubah dengan efek transisi -->
      <p @mouseover="changeMessage" @mouseleave="resetMessage">
        {{ message }}
      </p>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const counter = ref(0);
      const message = ref("Arahkan kursor ke sini!");
  
      const incrementCounter = () => {
        counter.value++;
      };
  
      const changeMessage = () => {
        message.value = "Kursor terdeteksi! 🎉";
      };
  
      const resetMessage = () => {
        message.value = "Arahkan kursor ke sini!";
      };
  
      return { counter, message, incrementCounter, changeMessage, resetMessage };
    }
  };
  </script>
  
  <style>
  /* Styling yang lebih modern */
  .container {
    text-align: center;
    margin-top: 50px;
    font-family: 'Arial', sans-serif;
  }
  
  h1 {
    color: #2c3e50;
    font-size: 24px;
  }
  
  /* Tombol dengan efek animasi */
  .btn {
    background: linear-gradient(135deg, #007bff, #0056b3);
    color: white;
    font-size: 18px;
    padding: 10px 20px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }
  
  .btn:hover {
    transform: scale(1.05);
    box-shadow: 0px 4px 10px rgba(0, 123, 255, 0.5);
  }
  
  /* Teks dengan efek transisi */
  p {
    font-size: 20px;
    color: #555;
    transition: color 0.3s ease, transform 0.3s ease;
    cursor: pointer;
  }
  
  p:hover {
    color: #e74c3c;
    transform: scale(1.1);
  }
  </style>
  
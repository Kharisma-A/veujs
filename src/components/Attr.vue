<template>
    <div class="container">
      <h1>Pemesanan Tiket Bioskop</h1>
  
      <!-- Menampilkan poster film -->
      <img :src="moviePoster" :alt="movieTitle" class="poster" />
  
      <!-- Pilihan kategori tiket -->
      <h3>Pilih Kategori Tiket:</h3>
      <select v-model="selectedCategory">
        <option v-for="(price, category) in ticketCategories" :key="category" :value="category">
          {{ category }} - Rp{{ price.toLocaleString() }}
        </option>
      </select>
  
      <!-- Informasi harga dan jumlah tiket -->
      <p>Harga per tiket: <strong>Rp{{ ticketCategories[selectedCategory].toLocaleString() }}</strong></p>
      <p>Tiket tersisa: <strong :class="{'low-stock': ticketStock < 5}">{{ ticketStock }}</strong></p>
  
      <!-- Tombol pemesanan -->
      <button :disabled="ticketStock === 0" @click="orderTicket" class="btn">
        {{ ticketStock === 0 ? "Tiket Habis" : "Pesan Sekarang" }}
      </button>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const movieTitle = ref("Dune: Part Two");
      const moviePoster = ref("https://source.unsplash.com/300x400/?movie");
      const ticketCategories = ref({
        "Reguler": 50000,
        "VIP": 100000,
        "VVIP": 150000
      });
      const selectedCategory = ref("Reguler");
      const ticketStock = ref(10);
  
      const orderTicket = () => {
        if (ticketStock.value > 0) {
          ticketStock.value--;
          alert(`Berhasil memesan tiket kategori ${selectedCategory.value}!`);
        }
      };
  
      return { movieTitle, moviePoster, ticketCategories, selectedCategory, ticketStock, orderTicket };
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
  
  h1 {
    color: #2c3e50;
  }
  
  .poster {
    width: 300px;
    height: 400px;
    border-radius: 8px;
    margin-bottom: 15px;
  }
  
  select {
    font-size: 16px;
    padding: 5px;
    border-radius: 5px;
    margin-bottom: 10px;
  }
  
  p {
    font-size: 18px;
  }
  
  .low-stock {
    color: red;
    font-weight: bold;
  }
  
  .btn {
    background-color: #27ae60;
    color: white;
    font-size: 18px;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background 0.3s ease;
  }
  
  .btn:disabled {
    background-color: #95a5a6;
    cursor: not-allowed;
  }
  </style>
  
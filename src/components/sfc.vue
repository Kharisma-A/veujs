<template>
  <div class="weather-app" :style="{ backgroundImage: `url(${backgroundImage})` }">
    <div class="weather-card">
      <h1>Weather Dashboard</h1>
      <h2>{{ location }}</h2>
      <img :src="weatherIcon" :alt="weatherDescription" class="weather-icon" />
      <p class="temperature">{{ temperature }}°C</p>
      <p class="description">{{ weatherDescription }}</p>
      <button @click="updateWeather" class="btn-refresh">Update</button>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const location = ref("Jakarta, ID");
    const temperature = ref(30);
    const weatherDescription = ref("Cerah Berawan");
    const weatherIcon = ref("https://source.unsplash.com/100x100/?sun");
    const backgroundImage = ref("https://source.unsplash.com/800x600/?sky");

    const updateWeather = () => {
      // Simulasi perubahan cuaca
      const weatherData = [
        { temp: 30, desc: "Cerah Berawan", icon: "https://source.unsplash.com/100x100/?sun", bg: "https://source.unsplash.com/800x600/?sky" },
        { temp: 24, desc: "Hujan Ringan", icon: "https://source.unsplash.com/100x100/?rain", bg: "https://source.unsplash.com/800x600/?rain" },
        { temp: 18, desc: "Bersalju", icon: "https://source.unsplash.com/100x100/?snow", bg: "https://source.unsplash.com/800x600/?snow" },
        { temp: 27, desc: "Berawan", icon: "https://source.unsplash.com/100x100/?cloud", bg: "https://source.unsplash.com/800x600/?cloud" }
      ];
      
      const randomWeather = weatherData[Math.floor(Math.random() * weatherData.length)];
      temperature.value = randomWeather.temp;
      weatherDescription.value = randomWeather.desc;
      weatherIcon.value = randomWeather.icon;
      backgroundImage.value = randomWeather.bg;
    };

    return { location, temperature, weatherDescription, weatherIcon, backgroundImage, updateWeather };
  }
};
</script>

<style>
/* Styling modern dan responsif */
.weather-app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-size: cover;
  background-position: center;
  transition: background 0.5s ease-in-out;
}

.weather-card {
  background: rgba(255, 255, 255, 0.8);
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

h1 {
  color: #2c3e50;
  font-size: 22px;
}

h2 {
  font-size: 18px;
  color: #555;
}

.weather-icon {
  width: 80px;
  height: 80px;
  margin: 10px 0;
}

.temperature {
  font-size: 36px;
  font-weight: bold;
  color: #e74c3c;
}

.description {
  font-size: 18px;
  font-style: italic;
  color: #555;
}

.btn-refresh {
  margin-top: 10px;
  background-color: #3498db;
  color: white;
  font-size: 16px;
  padding: 8px 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s ease;
}

.btn-refresh:hover {
  background-color: #2980b9;
}
</style>

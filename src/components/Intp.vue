<template>
  <div>
    <h1>Halo, {{ name }}!</h1>
    <p>Hari ini adalah {{ day }}.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "Pengguna Vue",
      day: new Date().toLocaleDateString("id-ID", { weekday: 'long' })
    };
  }
};
</script>

<style>
h1 {
  color: darkblue;
}

p {
  font-size: 18px;
  color: gray;
}
</style>

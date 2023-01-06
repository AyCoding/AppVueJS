<template>
  <RestaurantCard/>
 </template>

<script>
import RestaurantCard from './components/RestaurantCard.vue'

export default {
  name: 'App',
  components: {
    RestaurantCard
  }
}
</script>

<style>
@import url("https://unpkg.com/reset-css@5.0.1/reset.css");
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700;900&display=swap');

html,
body {
  font-family: 'Poppins', sans-serif;
  box-sizing: content-box;
  font-size: 16px;
}
</style>

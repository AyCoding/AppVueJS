<template>
  <RouterLink to="/" style="text-decoration: none">
    <div id="return">Retour à la home</div>
  </RouterLink>
  <div>
    <img :src="restaurant.image" alt="image du restaurant">
  </div>
  <p>{{ restaurant.name }}</p>
  <p>Note du restaurant : {{ restaurant.note }}</p>
  <p>Temps de livraison : {{ restaurant.drive_time }}</p>
</template>

<script>
import BDD from "../BDD";
import {useRoute} from "vue-router";

export default {
  name: "Restaurant",
  setup() {
    const route = useRoute()
    const restaurant = BDD.find((restaurant) => restaurant.name === route.params.name)

    return {
      restaurant
    }
  }
}
</script>

<style scoped lang="scss">
#return {
  margin: 25px 45px;
  font-weight: 400;
  cursor: pointer;
  text-decoration: none;
  color: #333;

  &:hover {
    font-weight: 900;
  }
}
</style>
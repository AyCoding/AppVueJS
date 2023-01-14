<template>
  <div class="restaurant--row">
    <h2 class="title">
      Nos restaurant !
    </h2>
    <div class="wrapper--card">
      <RouterLink class="restaurant--wrapper" v-for="(card,index) in three_restaurant" :key="index" :to="{name: 'Restaurant', params: {name:card.name}}">
        <RestaurantCard :info_restaurant="card"/>
      </RouterLink>
    </div>
  </div>
</template>

<script>
import RestaurantCard from "./RestaurantCard.vue";

export default {
  name: "RestaurantRow",
  components: {
    RestaurantCard
  },
  props: {
    three_restaurant: Array
  }
}
</script>

<style lang="scss">
.restaurant--row {
  .restaurant--wrapper {
    width: 32%;
    text-decoration: none;
    color: #000;
    &:hover {
      color: #555;
    }
  }
  .title {
    font-size: 2rem;
  }

  .wrapper--card {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
</style>
<template>
  <div class="home">
    <div class="header">
      <img src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg" alt="">
      <div class="wrapper--input">
        <input v-model="user_search_restaurant" type="text" placeholder="De quoi avez vous envie ?">
        <div class="search">
          <RouterLink v-for="(restaurant, i) in search_restaurant" :key="i" :to="{name: 'Restaurant', params: {name:restaurant.name}}">
            <div class="container--restaurant--search">
              <div class="wrapper--img">
                <img :src="restaurant.image" alt="">
              </div>
              <p>{{ restaurant.name }}</p>
            </div>
          </RouterLink>
        </div>
      </div>
    </div>
    <div class="banner"></div>
    <RestaurantRow v-for="(data, index) in data_restaurant" :three_restaurant="data"/>
  </div>
</template>

<script>
// IMPORT
import BDD from '../BDD';
import {onMounted, ref, watch} from "vue";

// COMPONENTS
import RestaurantRow from "../components/RestaurantRow.vue"

export default {
  name: "Home",
  components: {
    RestaurantRow
  },
  setup() {
    class Restaurant {
      constructor(name, note, image, drive_time) {
        this.name = name
        this.note = note
        this.image = image
        this.drive_time = drive_time
      }
    }

    let data_restaurant = ref([])
    let all_restaurant = []

    const makeDataRestaurant = () => {
      let three_restaurant = []

      for (const restaurant of BDD) {
        const new_restaurant = new Restaurant(restaurant.name, restaurant.note, restaurant.image, restaurant.drive_time)
        // make all restaurant array
        all_restaurant.push(new_restaurant)

        if (three_restaurant.length === 2) {
          three_restaurant.push(new_restaurant)
          data_restaurant.value.push(three_restaurant)
          three_restaurant = []
        } else {
          three_restaurant.push(new_restaurant)
        }
      }
    }
    // User search restaurant
    let user_search_restaurant = ref('')
    let search_restaurant = ref([])

    watch(user_search_restaurant, new_value => {

      let regex = RegExp(new_value.toLowerCase())

      let new_search_restaurant = all_restaurant.filter(restaurant => regex.test(restaurant.name.toLowerCase()))

      search_restaurant.value = new_search_restaurant

      if (new_value == 0) {
        search_restaurant.value = []
      } else {
        search_restaurant.value = new_search_restaurant
      }
    })

    onMounted(makeDataRestaurant)

    // RETURN
    return {
      data_restaurant,
      user_search_restaurant,
      search_restaurant
    }
  },
}
</script>

<style lang="scss">
.home {

  .header {
    width: 100%;
    height: 120px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    img {
      max-width: 200px;


    }

    .wrapper--input {
      position: relative;

      input {
        font-family: 'Poppins', sans-serif;
        background-color: #f6f6f6;
        border: none;
        width: 400px;
        height: 60px;
        outline: none;
        text-indent: 20px;
      }

      .search {
        position: absolute;
        top: 100%;
        width: 100%;
        background: #fff;

        .container--restaurant--search {
          display: flex;
          align-items: center;
          padding: 10px;

          .wrapper--img {
            width: 60px;
            height: 60px;
            margin-right: 25px;
            border-radius: 50%;
            overflow: hidden;

            img {
              width: auto;
              height: 100%;
            }
          }
        }
      }
    }
  }

  .banner {
    width: 100%;
    height: 200px;
    background-image: url("https://ubernewsroomapi.10upcdn.com/wp-content/uploads/sites/345/2016/03/blog_960x540.jpg");
  }
}
</style>
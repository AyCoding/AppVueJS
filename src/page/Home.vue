<template>
  <RestaurantRow/>
</template>

<script>
// IMPORT
import BDD from '../BDD';
// COMPONENTS
import RestaurantRow from "../components/RestaurantRow.vue"

export default {
  name: "Home",
  components: {
    RestaurantRow
  },
  setup() {
    console.log(BDD)

    class Restaurant {
      constructor(name, note, image, drive_time) {
        this.name = name
        this.note = note
        this.image = image
        this.drive_time = drive_time
      }
    }

    let resto = new Restaurant('Chez Nono', 4.9, 'img', '45mn')
    console.log(resto)
  }
}
</script>

<style scoped>

</style>
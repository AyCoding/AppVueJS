<template>
  <div class="restaurant--card">
    <div class="restaurant-image">

    </div>
    <div class="restaurant--information">
      <div class="top">
        <p class="name">
          Subway
        </p>
        <p class="note">
          <span>4.5</span>
        </p>
      </div>
      <p class="time">
        20-30mn
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "RestaurantCard",
}
</script>

<style lang="scss">
.restaurant--card {
  width: 32%;
  height: 30vh;

  p {
    margin: 0;
  }

  .restaurant-image {
    background-image: url("https://cn-geo1.uber.com/image-proc/resize/eats/format=webp/width=550/height=440/quality=70/srcb64=aHR0cHM6Ly9kMXJhbHNvZ25qbmczNy5jbG91ZGZyb250Lm5ldC8zNzg4MDJiMC1jNTI4LTQ4MjktYjBiNS0wY2M2NDBkZjYzY2QuanBlZw==");
    height: 70%;
    background-size: cover;
    background-position: center;
  }

  .restaurant--information {

    .top {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 10px 0;

      .note {
        display: flex;
        background-color: #eee;
        justify-content: center;
        align-items: center;
        width: 30px;
        height: 30px;
        font-size: .8rem;
        border-radius: 50%;
      }
    }

    .time {
      font-size: .9rem;
    }
  }
}
</style>
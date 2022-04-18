<template>
  <!-- Modal -->
  <div class="black-bg" v-if="isModalOpen">
    <div class="white-bg">
      <h4>{{ products[clickedRoom].title }}</h4>
      <p>{{ products[clickedRoom].content }}</p>
      <button @click="isModalOpen = false">닫기</button>
    </div>
  </div>
  <!-- navbar -->
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <!-- Discount Banner -->
  <Discount />
  <div v-for="product in products" :key="product.id">
    <img :src="product.image" class="room-img"/>
    <h4 @click="modalOpen(product.id)">{{ product.title }}</h4>
    <p>{{ product.price }}원</p>
  </div>
</template>

<script>
import products from './assets/oneroom';
import Discount from './components/DiscountBanner'

export default {
  name: 'App',
  data() {
    return {
      isModalOpen : false,
      clickedRoom: 0,
      menus : ['Home', 'Shop', 'About'],
      products : products,
    }
  },
  methods: {
    modalOpen(id) {
      this.isModalOpen = true
      this.clickedRoom = id
    }
  },
  components: {
    Discount: Discount
  },
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgb(0, 0, 0, 0.5);
  position: fixed;
  padding: 1rem;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 0.5rem;
  padding: 2rem;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background-color: darkslateblue;
  padding: 1rem;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 2rem;
}
</style>

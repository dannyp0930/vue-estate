<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <div v-for="product in products" :key="product.id">
    <img :src="product.imgUrl"/>
    <h4>{{ product.name }}</h4>
    <p>{{ product.price}} 만원</p>
    <button @click="increase(product.id)">허위매물신고</button>
    <span>신고수 : {{ product.report }}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      menus : ['Home', 'Shop', 'About'],
      products : [
          { id: 0, name: '역삼동원룸', price: 60, report: 0, imgUrl: require('./assets/room0.jpg') },
          { id: 1, name: '천호동원룸', price: 50, report: 0, imgUrl: require('./assets/room1.jpg') },
          { id: 2, name: '마포구원룸', price: 70, report: 0, imgUrl: require('./assets/room2.jpg') },
        ],
    }
  },
  methods: {
    increase(id) {
      this.products[id].report++;
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>

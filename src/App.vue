<template>
  <!-- Modal -->
  <div class="black-bg" v-if="modalOpen">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="modalOpen = false">닫기</button>
    </div>
  </div>
  <!-- Content -->
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <div v-for="product in products" :key="product.id">
    <img :src="require(`./assets/room${product.id}.jpg`)" class="room-img"/>
    <h4 @click="modalOpen = true">{{ product.name }}</h4>
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
      modalOpen : false,
      menus : ['Home', 'Shop', 'About'],
      products : [
          { id: 0, name: '역삼동원룸', price: 60, report: 0 },
          { id: 1, name: '천호동원룸', price: 50, report: 0 },
          { id: 2, name: '마포구원룸', price: 70, report: 0 },
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
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
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
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>

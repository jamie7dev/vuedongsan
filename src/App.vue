<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <button @click="modalOpen = false">X</button>
      <h4>제품 상세 페이지</h4>
      <p>제품 상세 내용</p>
    </div>
  </div>
  <div class="nav">
    <a v-for="(a, i) in navs" :key="i">{{a}}</a>
  </div>
  <!-- <div v-for="(a, i) in products" :key="i">
    <h4>{{ a }}</h4>
    <p>{{prices[i]}} 만원</p>
    <button @click="reports[i]++">허위매물신고</button><span>신고 : {{ reports[i] }}</span>
  </div> -->
  <div>
    <img class="room-img" src="./assets/room0.jpg" alt="room0">
    <h4 @click="modalOpen = true">{{ products[0] }}</h4>
    <p>50 만원</p>
    <button @click="reports[0]++">허위매물신고</button><span>신고 : {{ reports[0] }}</span>
  </div>
  <div>
    <img class="room-img" src="./assets/room1.jpg" alt="room1">
    <h4>{{ products[1] }}</h4>
    <p>70 만원</p>
    <button @click="reports[1]++">허위매물신고</button><span>신고 : {{ reports[1] }}</span>
  </div>
  <div>
    <img class="room-img" src="./assets/room2.jpg" alt="room2">
    <h4>{{ products[2] }}</h4>
    <p>80 만원</p>
    <button @click="reports[2]++">허위매물신고</button><span>신고 : {{ reports[2] }}</span>
  </div>

  
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      modalOpen : false,
      navs : ['Home', 'Products', 'About'],
      products : ['마포구 원룸', '용산구 원룸', '관악구 원룸'],
      prices : [50, 70, 60],
      reports: [0, 0, 0],
    }
  },
  methods : {
    increase(i){
      this.reports[i] += 1;
    },  
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
body {
  margin: 0;
}
.nav{
  background: royalblue;
  padding: 15px;
  border-radius: 5px;
}
.nav a{
  color: whitesmoke;
  padding: 10px;
  font-weight: bold;
  cursor: pointer;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: whitesmoke;
  border-radius: 8px;
  padding: 20px;
}
</style>

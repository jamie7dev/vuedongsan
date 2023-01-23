<template>
  <Modal @closeModal="modalOpen = false" :rooms="rooms" :clickedId="clickedId" :modalOpen="modalOpen"/>
  <div class="nav">
    <a v-for="(a, i) in navs" :key="i">{{a}}</a>
  </div>

  <Discount />

  <Card @openModal="modalOpen = true; clickedId=$event" :room="rooms[i]" v-for="(a, i) in rooms" :key="i"/>
  
  
  <!-- <Card :room="rooms[1]"/>
  <Card :room="rooms[2]"/>
  <Card :room="rooms[3]"/>
  <Card :room="rooms[4]"/>
  <Card :room="rooms[5]"/> -->
  
  
</template>

<script>

import data from './data/data.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data(){
    return{
      clickedId : 0,
      rooms : data, 
      modalOpen : false,
      navs : ['Home', 'Products', 'About'],
      reports: 0,
    }
  },
  methods : {
    // increase(){
    //   this.reports += 1;
    // }
  },
  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
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
.modal-close-btn {
  width: 50px;
  margin: 20px;
  padding: 5px 10px;
  cursor: pointer;
  display: block;
}


</style>

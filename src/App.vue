<template>

  <!-- <div class="start" :class="{end : modalOpen}">
    <Modal @closeModal="modalOpen = false" :rooms="rooms" :clickedId="clickedId" :modalOpen="modalOpen"/>
  </div> -->

  <transition name="modalTransition">
    <Modal @closeModal="modalOpen = false" :rooms="rooms" :clickedId="clickedId" :modalOpen="modalOpen"/>
  </transition>

  
  
  <div class="nav">
    <a v-for="(a, i) in navs" :key="i">{{a}}</a>
  </div>

  <Discount v-if="showDiscount === true"/>

  <button @click="priceSort">낮은 가격순</button>
  <button @click="higherPrice">높은 가격순</button>
  <button @click="titleSort">가나다순</button>
  <button @click="sortBack">되돌리기</button>
  <!-- <button @click="cheapItem">50만원 이하 상품</button> -->
  

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
      rooms_original : [...data],
      modalOpen : false,
      navs : ['Home', 'Products', 'About'],
      reports: 0,

      showDiscount : true,
    }
  },
  methods : {
    // increase(){
    //   this.reports += 1;
    // }
    priceSort(){
      this.rooms.sort(function(a, b){
        return a.price - b.price;
      });
    },
    
    higherPrice(){
      this.rooms.sort(function(a, b){
        return b.price - a.price;
      })
    },
    titleSort(){
      this.rooms.sort(function(a, b){
        if(a.title < b.title){
          return -1;
        }
        if(a.title > b.title){
          return 1;
        }
      });
    },
    cheapItem(){
      let cheap = this.rooms.filter( this.rooms.price <= 500000);
      return cheap;
    },
    sortBack(){
      this.rooms = [...this.rooms_original];
    },
  },

  created(){
    //서버에서 데이터 가져오는 코드 ajax
  },

  // mounted(){
  //   setTimeout(() => {
  //     this.showDiscount = false;
  //   }, 2000);
  // },

  components: {
    Discount: Discount,
    Modal: Modal,
    Card: Card,
  }
}
</script>

<style>
.start {
  opacity : 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}
.modalTransition-enter-from{
  opacity: 0;
}
.modalTransition-enter-active{
  transition: all 1s;
}
.modalTransition-enter-to{
  opacity: 1;
}
.modalTransition-leave-from{
  opacity: 1;
}
.modalTransition-leave-active{
  transition: all 1s;
}
.modalTransition-leave-to{
  opacity: 0;
}
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




</style>

<template>
  <div>
    <img class="room-img" :src="room.image">
    <h4 @click="openModal">{{ room.title }}</h4>
    <p>{{room.price}}원</p>
  </div>
  
  
 
</template>

<script>
export default {
  //eslint-disable-next-line
  name : 'Card',
  props : {
    room: Object,
  },
  methods : {
    openModal(){
      this.$emit('openModal', this.room.id)
    }
  },
}
</script>

<style>
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
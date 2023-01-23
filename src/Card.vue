<template>
  <div>
    <img :src="room.image">
    <h4 @click="$emit('openModal')">{{ room.title }}</h4>
    <p>{{room.price}}원</p>
  </div>
  
  
 
</template>

<script>
export default {
  //eslint-disable-next-line
  name : 'Card',
  props : {
    room: Object,
  }
}
</script>

<style>

</style>
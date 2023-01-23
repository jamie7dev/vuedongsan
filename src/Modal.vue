<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <div>
        <button class="modal-close-btn" @click="closeModal">닫기</button>
        <img :src="rooms[clickedId].image">
        <h4>{{ rooms[clickedId].title }}</h4>
        <p>{{ rooms[clickedId].content }}</p>
        <p>{{ rooms[clickedId].price }}원</p>
        <button @click="reports+=1">허위매물신고</button><span>신고 : {{ reports }}</span>
        <Discount />
      </div>      
    </div>
  </div>
</template>

<script>
export default {
  //eslint-disable-next-line
  name : 'Modal',
  props : {
    rooms : Array,
    clickedId : Number,
    modalOpen : Boolean,
  },
  methods: {
    closeModal() {
      this.$emit('closeModal')
    }
  },
}
</script>

<style>

</style>
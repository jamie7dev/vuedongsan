<template>
  <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <div>
        <button class="modal-close-btn" @click="closeModal">닫기</button>
        <img :src="rooms[clickedId].image">
        <h4>{{ rooms[clickedId].title }}</h4>
        <p>{{ rooms[clickedId].content }}</p>
        <!-- <input type="number" @input="month = $event.target.value"> -->
        <input v-model="month">
        <p>{{month}}개월 이용 금액 : {{ rooms[clickedId].price * month}}원</p>
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
  data() {
    return {
      month: 1,
    }
  },
  watch : {
    month(value){
      // const reg = /[ㄱ-ㅎ|ㅏ-ㅣ|가-힣|a-z]/;
      if ( isNaN(value) == true) {
        alert ('숫자만 입력하세요');
        this.month = 1;
      }
      if ( value < 1 || value > 12) {
        alert('1~12 사이 숫자를 입력하세요')
      }
      
    }
  },
  beforeUpdate(){
    if(this.month == 2){
      alert('2개월은 안 됩니다');
      this.month = 3;
    }
  }, 
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
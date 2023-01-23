<template>
  <div class="discount">
    <h4>지금 결제하면 {{discountRate}}% 할인</h4>
  </div>
</template>

<script>
export default {
  //eslint-disable-next-line
  name : 'Discount',
  data(){
    return{
      discountRate : 30,
    }    
  },
  mounted(){
    setInterval(() => {
      if(this.discountRate > 20){
        this.discountRate -= 1;
      }
      else{
        clearInterval();
      }
    }, 1000);
  },
}
</script>

<style>
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>
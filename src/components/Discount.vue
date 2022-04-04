<template>
    <div class="discount">
        <h4>지금 결제하면 {{ sale }}% 할인</h4>
  </div>
</template>

<script>
export default {
  name : 'Discount',
  data() {
    return {
      sale : 30
    }
  },
  mounted() {
    setInterval(()=>{
      this.sale = this.sale - 1
    }, 1000)
  }
}
</script>

<style>
.discount {
  background-color: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;

}
</style>
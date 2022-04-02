<template>

  <Modal :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니" />
  <div class="menu">
    <a v-for="item in menus" :key="item">{{ item }}</a>
  </div>
  <Discount :이름="오브젝트.name" :나이="오브젝트.나이" />

  <card @openModal="모달창열렸니 = true; 누른거 = $event" :원룸="원룸들[index]" v-for=" (원룸, index) in 원룸들" :key="index" />

  
  
    <!-- <div v-for="(item, index) in 원룸들" :key="index">
      <img :src="item.image" class="room-image">
      <h4 @click="close; 누른거 = index ">{{ item.title }}</h4>
      <p>{{ item.price }}원</p>
  </div> -->
</template>

<script>  
import data from './assets/oneroom.js';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/card.vue';

export default { 
  name: 'App',
  data() {
    return {
      오브젝트 : { name : 'kim', age : 20},
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      prices : ['50', '70', '80']
    }
  },

  methods : {
    increase(){
      this.신고수 += 1;
    },
    close() {
      this.모달창열렸니 = false;
    }
  },

  components: {
    Discount, Modal, Card
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

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-image {
  width: 100%;
  margin-top: 40px;
}

.body {
  margin : 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height: 100%;
  background: rbga(0,0,0,0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}


</style>

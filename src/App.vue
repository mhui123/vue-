<template>

  <!-- Modal -->
  <DetailModal @closeModal="modalState = false" :rooms = "rooms" :modalNumber = "modalNumber" :modalState = "modalState"/>

  <div class="menu">
    <a v-for="(a, i) in menus" :key="i">{{ menus[i] }}</a>
  </div>

  <Discount/>

  <Card @openModal="modalState = true; modalNumber = $event" :a = "rooms[i]" v-for="(a,i) in rooms" :key="i"/>

</template>

<script>

import roomData from "./assets/oneroom.js";
import Discount from "./components/Discount.vue";
import DetailModal from "./components/DetailModal.vue";
import Card from "./components/Card.vue";

export default {
  name: 'App',

  data(){
    return {
      object : { name: 'kim', age: 20},
      rooms: roomData,
      menus: ["Home", "Board", "About"],
      modalState : false,
      modalNumber : 0
    }
  },
  
  methods : {
  },

  components: {
    Discount : Discount,
    DetailModal : DetailModal,
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

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}

.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.closeModalBtn {
  width: 100%; height:50px;
  background:rgba(100, 100, 100, 0.5);
  border-radius: 5px;
}

.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius:5px;
}
</style>

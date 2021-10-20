<template>

  <!-- Modal -->
  <div class="black-bg" v-if = "modalState == true">
    <div class="white-bg">
      <h4>{{ rooms[modalNumber].title }}</h4>
      <img :src="rooms[modalNumber].image">
      <p>{{ rooms[modalNumber].price }}원</p>
      <p>{{ rooms[modalNumber].content }}</p>
      <button class="closeModalBtn" @click = "modalState = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a, i) in menus" :key="i">{{ menus[i] }}</a>
  </div>

  <div v-for="(a, i) in rooms" :key="i">
    <img :src="a.image" class="room-img">
    <h4 @click = " modalState = true; modalNumber = i ">{{ a.title }}</h4>
    <p>{{ a.price }} 원</p>
  </div>

</template>

<script>

import roomData from "./assets/oneroom.js"

export default {
  name: 'App',

  data(){
    return {
      rooms: roomData,
      menus: ["Home", "Board", "About"],
      modalState : false,
      modalNumber : 0
    }
  },
  
  methods : {
  },

  components: {
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
</style>

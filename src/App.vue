<template>
  
  <!-- modal UI-->
  <div class="black-bg" v-if = "modalState == true">
    <div class="white-bg">
      <h4>{{ onerooms[checkedNumber].title }}</h4>
      <img :src = "onerooms[checkedNumber].image">
      <p>{{ onerooms[checkedNumber].price }}원</p>
      <p>{{ onerooms[checkedNumber].content }}</p>
      <button id="modalClose" @click="modalState = false;">X</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a,i) in menus" :key="i">{{ a }}</a>
  </div>

  <div v-for="(e, i) in onerooms" :key = "i">
    <img :src = "onerooms[i].image" class="room-img">
    <h4 @click="modalState = true; checkedNumber = i;">{{ e.content }}</h4>
    <p>{{ e.price }}</p>
  </div>
</template>

<script>

import roomData from './assets/oneroom.js';

export default {
  name: 'App',
  //data저장함
  data(){
    return {
      checkedNumber : 0,
      onerooms : roomData,
      modalState : false,
      menus: ['Home', 'Shop', 'About'],
      reportCount : [0, 0, 0]
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
</style>

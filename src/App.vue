<template>
  
  <!-- modal UI-->
  <div class="black-bg" v-if = "modalState == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>내용</p>
      <button id="modalClose" @click="closeModal">X</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a,i) in menus" :key="i">{{ a }}</a>
  </div>

 <!-- 
   <div class="items" v-for=" (e, i) in products" :key="i">
    <h4 style="color: blue">{{ products[i] }}</h4>
    <p>33 만원</p>
    <button id="'reportBtn'+{{i}}" @click = "doReport">허위매물 신고</button> <span>신고수 : {{ reportCount }} </span>
  </div>


  <div>
    <img src = "./assets/room0.jpg" class="room-img">
    <h4 style="color: blue" id="roomName1" @click="modalState = true">{{ products[0] }}</h4>
    <p>33 만원</p>
    <button id="reportBtn" @click = "doReport">허위매물 신고</button>
    <span>신고수 : {{ reportCount[0] }} </span>
  </div>
 -->
  <div v-for="(e, i) in onerooms" :key = "i">
    <img :src = "onerooms[i].image" class="room-img">
    <h4>{{ onerooms[i].content }}</h4>
    <p>{{ onerooms[i].price }}</p>
  </div>
</template>

<script>
//박아넣기
//js: document.getElementById().innerHTML = ??

import roomData from './assets/oneroom.js';

export default {
  name: 'App',
  //data저장함
  data(){
    return {
      onerooms : roomData,
      modalState : false,
      menus: ['Home', 'Shop', 'About'],
      reportCount : [0, 0, 0]
    }
  },
  
  methods : {
    doReport() {
      this.reportCount[0] ++;
    },

    closeModal() {
      this.modalState = false;
    }
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

<template>
    <!-- Modal -->
  <div class="black-bg" v-if = "modalState == true">
    <div class="white-bg">
      <h4>{{ rooms[modalNumber].title }}</h4>
      <img :src="rooms[modalNumber].image">
      <p>{{ rooms[modalNumber].content }}</p>
      <!-- <input @input="month = $event.target.value"> -->
      <input v-model.number="month">
      <input type="range" min="1" max="12">
      <p>{{ month }}개월 선택함 : {{ month * rooms[modalNumber].price }}원</p>
      <button class="closeModalBtn" @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>

export default {
    name:'DetailModal',
    data(){
      return {
        month: 1,
      }
    },

    watch : {
      /*해당 이름의 변수가 변경될 때마다 해당 함수 실행*/
      month(after){
        if(isNaN(after)) {
          this.month = 1;
          alert("숫자를 입력해 주세요");
        }
      },
    },

    props: {
        rooms: Object,
        modalNumber: Number,
        modalState: Boolean,
    }
}
</script>

<style>

</style>
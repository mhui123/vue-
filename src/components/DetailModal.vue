<template>
    <!-- Modal -->
  <div class="black-bg" v-if = "modalState == true">
    <div class="white-bg">
      <h4>{{ rooms[modalNumber].title }}</h4>
      <img :src="rooms[modalNumber].image">
      <p>{{ rooms[modalNumber].content }}</p>
      <!-- <input @input="month = $event.target.value"> -->
      <!-- <input v-model.number="month">
      <input type="range" min="1" max="12"> -->
      <input @input="month = $event.target.value">
      <p>{{ month }}개월 {{ rooms[modalNumber].price * month }}원</p>
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
    //데이터 감시
    watch : {
      month(param) {
        if(isNaN(param)){
          alert("숫자를 입력하세요");
          this.month = 1;
        }
      }
    },

    props: {
        rooms: Object,
        modalNumber: Number,
        modalState: Boolean,
    },
    //lifeCycle hook

    //변경되고 나서 실행
    beforeUpdate(){
      if(this.month == 2){
        alert("2를 입력했습니다.");
      }
    }
}
</script>

<style>

</style>
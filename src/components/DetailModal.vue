<template>
    <!-- Modal -->
  <div class="black-bg" v-if = "modalState == true">
    <div class="white-bg">
      <h4>{{ rooms[modalNumber].title }}</h4>
      <img :src="rooms[modalNumber].image">
      <p>{{ rooms[modalNumber].price }}원</p>
      <p>{{ rooms[modalNumber].content }}</p>
      <button class="closeModalBtn" @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>

export default {
    name:'DetailModal',
    props: {
        rooms: Object,
        modalNumber: Number,
        modalState: Boolean,
    }
}
</script>

<style>

</style>
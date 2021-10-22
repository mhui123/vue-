<template>
  <div>
    <img :src="a.image" class="room-img">
    <h4 @click = "openModal">{{ a.title }}</h4>
    <p>{{ a.price }} 원</p>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props:{
        a: Object,
    },
    methods:{
        //여기서 $emit()을 쓰려면
    /*
    function1(){
      this.$emit('emitName', data);
    }
    */
        openModal(){
            this.$emit('openModal', this.a.id);
        }
        
    }
}
</script>

<style>

</style>
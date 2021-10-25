<template>
  <div>
    <img class="room-img" :src="a.image">
    <h4 @click = "openModal">{{ a.title }}</h4>
    <p>{{ a.price }}원</p>
  </div>
</template>

<script>
export default {
    name:'Card',
    props:{
        a: Object,
    },
    methods:{
        openModal(){
            this.$emit('openModal', this.a.id);
        }
    },
}
</script>

<style>

</style>
<template>
  <div class="discount">
    <h4>{{ discountRate }}% 할인 진행중</h4>
  </div>
</template>

<script>
export default {
    name:'Discount',
    props: {
      discountRate: Number,
    }
}
</script>

<style>

</style>
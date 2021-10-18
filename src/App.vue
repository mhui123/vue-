<template>
  
  <div class="menu">
    <a v-for="(a,i) in menus" :key="i">{{ a }}</a>
  </div>


  <div class="items" v-for=" (e, i) in products" :key="i">
    <h4 style="color: blue">{{ products[i] }}</h4>
    <p>33 만원</p>
  </div>
</template>

<script>

//박아넣기
//js: document.getElementById().innerHTML = ??



export default {
  name: 'App',
  //data저장함
  data(){
    return {
      //price data(object)
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      menus: ['Home', 'Shop', 'About']
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
</style>

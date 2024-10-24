<script setup>
  import NavBar from './components/NavBar.vue';
  import MainComp from './components/MainComp.vue';
  import { ref, onMounted } from 'vue';
  import { useStore } from 'vuex';
  import About from './components/About.vue';

  const store = useStore();
  

  
  // 앱이 실행되면 날씨 데이터 가져오기
  onMounted(() => {
    store.dispatch('getWeather');
    
  })
 const onSearchCity = (city) =>{

  weatherData.value.city=city;
  getWeather();
 }
</script>

<template>
 <button @click="$store.dispatch('getWeather')">getWeather</button>
 <NavBar />
 
  <div v-if="!$store.state.toggle">
    <MainComp />
  </div>
  <div v-else>
    <About />
  </div>

</template>

<style scoped lang="scss">

</style>
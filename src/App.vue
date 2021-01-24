<template>
  <div >
    <HomePage  />
    <Test v-for="(item,i) in posts" v-bind:key="i" :item="item.title" />  
    <HomeBanner></HomeBanner>
    <Qualities/>
    <HomeTiles></HomeTiles>
    <CarouselOne></CarouselOne>
  </div>
</template>

<script>
import HomePage from './components/HomePage.vue'
import Test from './components/Test.vue' 
import HomeBanner from './components/HomeBanner.vue' 
import HomeTiles from './components/HomeTiles.vue'
import Qualities from './components/Qualities.vue'
import CarouselOne from './components/CarouselOne.vue'
import { createApp } from "vue";
import axios from "axios";
import VueAxios from "vue-axios";

const app = createApp();
app.use(VueAxios, axios);

export default {
  name: 'App',
  components: {
    HomePage, Test, HomeBanner, Qualities,HomeTiles,CarouselOne
  },
  data(){
    return{
      posts:undefined,  
    }
  },
   mounted(){
    axios.get("http://localhost:8000/wp-json/wp/v2/posts").then(response=>{this.posts=response.data})
    
  }  
}
</script>



<style>
body{
  width: 100%;
  height: 100%;
  padding:0;
  margin:0;
}
</style>

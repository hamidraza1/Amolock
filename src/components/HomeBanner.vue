<template>
  <div class="HomeBannerWrapper">
    <div class="carousel-container">
        <div class="carousel-slide" id="carouselSlide" v-if="homebannerPosts.length">
            <div v-for="(item,i) in homebannerPosts" v-bind:key="i" class="carouselImagesWrapper">
                <img 
                id="carouselImages"
                v-bind:src="item.background_image.guid" 
                alt="homePage Banner">
                <span class="bannerDetails">
                    <div class="bannerDetailsInner">
                        <div class="bannerTitle">
                            AMOLOCK - {{item.banner_title}}
                        </div>
                        <div class="bannerDescription">
                            {{item.description}}
                        </div>
                    </div>
                    <button v-if="item.btn_1"  class="bannerButton1">
                        {{item.btn_1}}
                    </button>
                    <button v-if="item.btn_2" class="bannerButton2">
                        {{item.btn_2}}
                    </button>
                </span>
            </div>
        </div>
    </div>
    <div class="slideCntrlWrapper">
        <div v-for="(item,i) in homebannerPosts" v-bind:key="i" class="slideCntrl"  @click="SlidesCntrl($event,i)"></div>
    </div>
  </div>
</template>

<script>


import { createApp } from "vue";
import axios from "axios";
import VueAxios from "vue-axios";

const app = createApp();
app.use(VueAxios, axios);

export default {
  name: 'HomeBanner',
  data(){
    return{
      homebannerPosts:[],

      counter:0,
      idx:0,
      
      
     
    
    }
  },
  mounted(){
    axios.get("http://localhost:8000/wp-json/wp/v2/home_banner").then(response=>{this.homebannerPosts=response.data})
    
    
  },
  
 
  methods:{
      SlidesCntrl(e,i){
            let carouselSlide=document.getElementById("carouselSlide");
            let carouselImages=document.querySelectorAll(".carousel-slide img"); 
            let slideCntrlWrapper=document.querySelector(".slideCntrlWrapper");  
             slideCntrlWrapper.childNodes.forEach(node =>{
                 if(node.nodeType=="1" && node.classList.contains("active")){
                    node.classList.remove("active")
                 } 
            })
            e.target.classList.add("active")
            carouselSlide.style.transition="transform 0.4s ease-in-out"; 

            if(i>this.idx){  
                const size=(Array.from(carouselImages)[0].clientHeight) ;
                this.counter=(this.counter)+(i-this.idx);
                carouselSlide.style.transform='translateY('+(-size*this.counter)+'px)';  
                this.idx=i;
            }else if(i<this.idx){
                const size=(Array.from(carouselImages)[0].clientHeight);
                this.counter=(this.counter)-(this.idx-i);
                carouselSlide.style.transform='translateY('+(-size*this.counter)+'px)';  
                this.idx=i;
            }
            
        }
      },
  
}
</script>



<style>
.HomeBannerWrapper{
    position:relative;
}
.carousel-container{
    overflow: hidden; 
     
}
.carousel-slide{
    display:flex;
    flex-direction: column;
    height:400px;
    
}
.carouselImagesWrapper{
   position: relative;
   
}

img{    
   object-fit: fill;
   width: 100%;
   height: fit-content;
   
}
.bannerDetails{
    position: absolute;
    top:15%;
    left:6%;
    margin: auto;
}
.bannerDetailsInner{
    max-width: 600px;
}
.bannerTitle{
    font-size: 48px;
    font-weight:600;
    color: white;
    font-family: sans-serif;
    line-height:55px;
   
}
.bannerDescription{
    font-size: 18px;
    color: white;
     margin-bottom: 45px;
}

.bannerButton1{
  
    border:none;
    background-color: rgb(187,187,186);
    padding: 10px 25px;
    color:white;
    border-radius: 3px;
}
.bannerButton2{
    
    border:none;
    background-color: rgb(97,124,119);
    padding: 10px 25px;
    color:white;
    border-radius: 3px;
    margin-left:25px;
}





.slideCntrlWrapper{
    position:absolute;
    top:15%;
    right:0;
}
.slideCntrl{
    width:15px;
    height: 15px;
    background-color: rgb(226,162,168);
    margin:25px 25px;
    transform: rotate(45deg);
    cursor:pointer;
    box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
}
.active{
    background: white;
}

</style>

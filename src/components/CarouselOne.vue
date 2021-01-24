<template>
    <div class="CarouselImagesConatiner" v-if="CarouselImagesPosts.length">
        
        <div class="CarouselImagesWrapper" v-for="(item,i) in CarouselImagesPosts" v-bind:key="i">
            <div @click="CarouselSlidesPrev()" class="ArrowWrapper"><i class="fas fa-arrow-left"></i></div>
            <div class="CarouselImageInner">
                <div class="CarouselImage">
                     <img class="Image" v-bind:src="item.image1.guid">
                </div>
                <div class="CarouselImage">
                     <img class="Image" v-bind:src="item.image2.guid">
                </div>
                <div class="CarouselImage">
                     <img class="Image" v-bind:src="item.image3.guid">
                </div>
                <div class="CarouselImage">
                     <img class="Image" v-bind:src="item.image4.guid">
                </div>
                <div class="CarouselImage">
                     <img class="Image" v-bind:src="item.image5.guid">
                </div>
                <div class="CarouselImage">
                     <img class="Image" v-bind:src="item.image6.guid">
                </div>
                <div class="CarouselImage">
                     <img class="Image" v-bind:src="item.image7.guid">
                </div>   
            </div>
            <div class="ImageDesc">
            </div>
            <div @click="CarouselSlidesNext()" class="ArrowWrapper"><i class="fas fa-arrow-right"></i></div>
        </div>
        
    </div>
</template>

<script>


import { createApp } from "vue";
import axios from "axios";
import VueAxios from "vue-axios";
import '@fortawesome/fontawesome-free/css/all.css'
import '@fortawesome/fontawesome-free/js/all.js'

const app = createApp();
app.use(VueAxios, axios);

export default {
  name: 'CarouselOne',
  data(){
    return{
    CarouselImagesPosts:[],
    counter:0,
     
    
    }
  },
    mounted(){
    axios.get("http://localhost:8000/wp-json/wp/v2/carousel_image").then(response=>{this.CarouselImagesPosts=response.data}).then(()=>{console.log(this.CarouselImagesPosts)})
    
  },
   methods:{
        CarouselSlidesPrev(){

            
            let carouselImage=document.getElementsByClassName("CarouselImage");
            let carouselImg=document.querySelectorAll(".CarouselImage img"); 
            const size=(Array.from(carouselImg)[0].clientWidth)+10 ;
            carouselImage.forEach(element => {
                element.style.transition="transform 0.4s ease-in-out";
            });
            if(this.counter > 0){
                this.counter--;
                carouselImage.forEach(element => {
                element.style.transform='translateX('+(-size*this.counter)+'px)'; 
            });
            }
            
           console.log(this.counter)  
        },
        CarouselSlidesNext(){
            /* let ImagesLength=this.CarouselImagesPosts.length; */
            
            let carouselImage=document.getElementsByClassName("CarouselImage");
            let carouselImg=document.querySelectorAll(".CarouselImage img"); 
            const size=(Array.from(carouselImg)[0].clientWidth)+10 ;
            carouselImage.forEach(element => {
                element.style.transition="transform 0.4s ease-in-out";
            });
            let CarouselImageInner=document.getElementsByClassName("CarouselImageInner");              
            if(this.counter < (CarouselImageInner[0].children.length-4)){
                this.counter++;
                carouselImage.forEach(element => {
                element.style.transform='translateX('+(-size*this.counter)+'px)'; 
            }); 
            }
           
      
        }
    }
 
  
  
}
</script>


<style>
.CarouselImagesWrapper{
    display: flex;
}
.CarouselImageInner{
    display: flex;
    overflow: hidden;
    margin:auto;
    max-width: 1270px;

}
.CarouselImage{
    width:300px;
    height: 300px;
    margin-right:20px;
    
}
@media (min-width: 576px){
    .CarouselImage{
        width:110px;
        height: 110px;  
        margin-right:10px;
    }
}
 @media (min-width: 768px){
    .CarouselImage{
        width:185px;
        height: 185px;  
        margin-right:10px;
    }
} 
 @media (min-width: 992px){
    .CarouselImage{
        width:240px;
        height: 240px;  
        margin-right:10px;
    }
} 
 @media (min-width: 1200px){
    .CarouselImage{
      width:285px;
    height: 285px;
    margin-right:20px;
    }
} 

.Image{
     width:300px;
    height: 300px;
}
@media (min-width: 576px){
    .Image{
    width:110px;
    height: 110px;  
    }
}
 @media (min-width: 768px){
    .Image{
    width:185px;
    height: 185px;  
    }
} 
 @media (min-width: 992px){
    .Image{
    width:240px;
    height: 240px;  
    }
} 
 @media (min-width: 1200px){
    .Image{
    width:285px;
    height: 285px;  
    }
} 

.ArrowWrapper{
    display: flex;
    align-items: center;
    justify-content: center;
    margin:0 20px;
}
</style>

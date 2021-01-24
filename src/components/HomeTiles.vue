<template>
    <div v-if="homeTilesPosts.length">
        <div class="HomeTilesWrapper" v-for="(item,i) in homeTilesPosts" v-bind:key="i">
            <div :class="i%2 == 0 ? 'ImageWrapper': 'order'">
                <img v-bind:src="item.photo.guid"  intrinsicsize="400x300"
                    alt="homePage Banner">
            </div>
            <div class="DetailsWrapper">
                <div class="heading"> {{item.heading}}</div>
                <div class="subHeading">{{item.subheading}}</div>
                <div class="description">{{item.description}}</div>
                <button class="butn">{{item.button}}</button>
            </div>
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
  name: 'HomeTiles',
  data(){
    return{
    homeTilesPosts:[],
     
    
    }
  },
    mounted(){
    axios.get("http://localhost:8000/wp-json/wp/v2/home_tile").then(response=>{this.homeTilesPosts=response.data}).then(()=>{console.log(this.homeTilesPosts)})
    
  },
  
 
  
  
}
</script>


<style>
.HomeTilesWrapper{
    display:flex;
    width:100%;
}
.ImageWrapper{
    width:50%;    
}
.order{
    width:50%;
    order:2 ;
}
img{
    width: 100%;  
    height: 500px;  
}
.DetailsWrapper{
    width: 50%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding:40px;
}
.heading{
    font-size: 26px;
    font-weight: 800;
    padding: 20px  ;
    text-align: center;
}
.subHeading{
    font-size: 22px;
    font-weight: 600;
    padding-bottom: 20px  ;
    text-align: center;
}
.description{
    font-size: 14px;
    text-align: center;
    padding-bottom:30px ;
}
.butn{ 
    padding:15px 30px;
    border-radius: 3px;
    background: rgb(96,123,119);
    color: white;
    border: none;
}

</style>

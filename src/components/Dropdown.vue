<template>
    <div class="menu-item">
        <span class="menu-title" @mouseover="isOpen=true" @mouseout="isOpen=false">
            {{title}}
        </span>
        <transition name="fade" appear>
            <div class="sub-menu" v-if="isOpen" @mouseover="isOpen=true" @mouseout="isOpen=false">
                <div class="sub-section">
                    <div v-for="(item,i) in items" :key="i" class="menu-item">
                        <div :href="item.link" >{{item.title}}</div>
                    </div>
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
export default {
    name:"dropdown",
    props:["title","items"],
    data(){
        return{
            isOpen:false
        }
    },
}
</script>

<style>

.sub-menu{
    position: absolute; 
    z-index: 1000; 
    background-color: white;
    top:calc(100%+18px);
    left:0;
     width:99.8%; 
}
 .sub-section{
    width: fit-content;
    background-color: white;
   margin:auto;
    
} 
.sub-menu .menu-item{
    padding: 10px;
    width: max-content;
}
.sub-menu .menu-item:hover{
   cursor: pointer;
}


.fade-enter-active,
.fade-leave-active{
    transition: all 0.1s ease-out;
}
.fade-enter,
.fade-leave-to{
    transform: scale(0); 
    opacity:0
}

</style>
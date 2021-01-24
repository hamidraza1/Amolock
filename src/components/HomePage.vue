<template>
  <div>
    <div class="choose-language d-flex justify-content-end">
      <select name="language" id="language" class="dropdown">
        <option value="deutsch">Deutsch</option>
        <option value="english">English</option>
      </select>
    </div>
    <nav class="navbar navbar-expand-md navbar-light bg-light">
      <a href="#" class="navbar-brand">Amolock</a>
      <button class="navbar-toggler" data-toggle="collapse" data-target="#navbarMenu">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarMenu">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <a href="#" class="nav-link">Produkte</a>
          </li>
          <li class="nav-item Unternehmen">
            <Dropdown class="nav-link" title="Unternehmen" :items="unternehmen"/>
          </li>
          
          <li class="nav-item">
            <a href="#" class="nav-link">News</a>
          </li>
          <li class="nav-item">
            <Dropdown class="nav-link" title="Services" :items="serices"/>
          </li>
          <li class="nav-item">
          <a href="#" class="nav-link">Vertrieb</a>
          </li>
          <li class="nav-item">
          <a href="#" class="nav-link">Kontakt</a>
          </li>
        </ul>
      </div>     
    </nav>
   
  </div>
</template>

<script>

import Dropdown from "./Dropdown"


export default {
  name: "HomePage",
  props: {},
  components:{
    Dropdown
  },
  data(){
    return{
      unternehmen:[
        {
          title:"Über uns",
          link:"#"
        },
        {
          title:"Produktion",
          link:"#"
        },
        {
          title:"Neuigkeiten",
          link:"#"
        },
        {
          title:"Referenzen",
          link:"#"
        }
      ],
      serices:[
        {
          title:"Downloads",
          link:"#"
        },
        {
          title:"FAQ",
          link:"#"
        },
        {
          title:"Pflegeanleitung",
          link:"#"
        },
        {
          title:"Verlegeanleitung",
          link:"#"
        }
      ]
    }
  }
};
</script>

<style scoped>


.choose-language {
  background-color: rgb(247, 247, 247);
}
.dropdown {
  border: none;
  font-size: 12px;
  background-color: rgb(247, 247, 247);
  margin-right: 15px;
  font-weight: 600;
}
.dropdown:focus {
  outline: none;
}
.collapse{
  font-weight: 600;
}


</style>

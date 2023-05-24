<template>
  <div>
    <NavBar :logo="logo_src" :alt="app_name" />
    <RouterView/>
    <Footer/>

</div>
</template>


<script>
//import { RouterLink, RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'

export default{
components:{
  NavBar,
  Footer,
},

data(){
  return{
    logo_src: "/img/hamburguer.png",
    app_name: "Make Your Burguer"
  }
}


}
</script>
<style>

*{
  font-family: Arial, Helvetica, sans-serif;
  margin:0px;
  padding: 0px;
}

.main-container{
  margin: 50px;
  min-height:250px;
}

h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color:#222;
}

</style>

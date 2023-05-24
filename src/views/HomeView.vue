
<template>
<div class="home">
<Banner/>
<div class="main-container">
    <h1>Monte o seu burger:</h1>
    <Burguer_form/>
</div>

</div>
</template>

<script>
import Banner from "../components/Banner.vue"
import Burguer_form from "../components/Burguer_form.vue";

export default{
    name: "Home",
    components:{
        Banner,
        Burguer_form,
    },
}
</script>

<style scoped>


</style>


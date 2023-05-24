<template>
    <div id="nav">
        <RouterLink to="/" id="logo_url">
            <img :src="logo" id="logo" :alt="alt">
        </RouterLink>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/pedidos">Pedidos</RouterLink>
    </div>
</template>

<script>
export default {
    name: "NavBar",
    
    props: ["logo","alt"],
}
</script>

<style scoped>

img{
    height: 100px;
}

#nav{
    background-color: #222;
    border-bottom: 4px solid #111;
    padding: 15px 50px;
    display: flex;
    justify-content: flex-end;
    align-items: center;
}

#nav #logo_url{
    margin:auto;
    margin-left:0;
}

#logo{
    width: 40px;
    height: 40px;
}

#nav a{
    color: #FCBA03;
    text-decoration: none;
    margin: 12px;
    font-size: 20px;
    
}

#nav a:hover{
    color:#f2e4bf;
    transition: .6s;
}

</style>
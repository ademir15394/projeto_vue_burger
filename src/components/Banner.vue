<template>

    <div id="main-banner">
        <h1>Make Your Burger</h1>
    </div>

</template>

<script>
export default {
    name: "Banner",
}
</script>

<style scoped>

#main-banner{
    background-image: url('/img/burguer.jpg');
    background-position: 0 -150px;
    background-size: cover;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin:0;
    padding:0;
}

#main-banner h1{
    color:#FFF;
    text-align: cneter;
    font-size: 60px;
    background-color: #222;
    padding: 20px 40px;
}

</style>
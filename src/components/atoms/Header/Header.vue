<template>
 <section class="header-container">
    <h1 class="heading">Recipe Book App</h1>
 </section>
</template>


<style scoped>
.header-container{
    background-color: #0c2461;
    height: 80px;
    text-align: center;
    place-content: center;
}

.heading{
    color: white;
    font-weight: 600;
    font-size: 26px;
}

@media screen and (min-width:768px) {
    .heading{
        font-size: 30px;
    }
}

@media screen and (min-width:1024px) {
    .heading{
        font-size: 36px;
    }
}


</style>


<script setup>
import { ref, watchEffect } from 'vue';
import Header from './components/Header/Header.vue';
import Card from './components/Card/Card.vue';
import Loading from './components/Loading/Loading.vue';

const recipeData = ref([])

const url = 'https://dummyjson.com/recipes'

let isLoading = ref(false)

watchEffect(async()=>{
  try {
    isLoading.value = true
    const res = await fetch(url)
    const data = await res.json()
    recipeData.value  = data.recipes
    console.log(recipeData.value)
  } catch (error) {
    console.log(error)
  }
  finally{
    isLoading.value =false
  }
})

</script>

<template>
   <Header />
   <Loading v-if="isLoading"/>
   <div v-else class="all-cards">
    <Card v-if="recipeData.length > 0" v-for="recipe in recipeData" :key="recipe.id" :recipe="recipe"/>
   </div>

</template>

<style scoped>

.all-cards{
  display: grid;
  
}

@media screen and (min-width:768px) {
  .all-cards{
    grid-template-columns: repeat(2,1fr);
  }
}

@media screen and (min-width:1024px) {
  .all-cards{
    grid-template-columns: repeat(3,1fr);
  }
}

@media screen and (min-width:1440px) {
  .all-cards{
    grid-template-columns: repeat(4,1fr);
  }
}

</style>

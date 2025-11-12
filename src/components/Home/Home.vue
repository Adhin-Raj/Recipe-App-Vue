<script setup>
import { ref, watchEffect } from 'vue'
import Button from '../Button/Button.vue'
import Card from '../Card/Card.vue'
import Loading from '../Loading/Loading.vue'


const recipeData = ref([])

const url = 'https://dummyjson.com/recipes'

let isLoading = ref(false)
let lastIndex = ref(16)

watchEffect(async () => {
    try {
        isLoading.value = true
        const res = await fetch(url)
        const data = await res.json()
        recipeData.value = data.recipes
    } catch (error) {
        console.log(error)
    }
    finally {
        isLoading.value = false
    }
})


const handleSeeMore=()=>{
    isLoading.value = true
    setTimeout(() => {
       lastIndex.value = recipeData.value.length 
       isLoading.value = false
    }, 1000);
}

const handleFilter=()=>{
    console.log("filter")
}
</script>


<template>
    <main>
        <Button :handle-click="handleFilter" position="self-end">Sort</Button>
        <div v-if="!isLoading" class="all-cards">
            <Card  v-for="recipe in recipeData.slice(0,lastIndex)" :key="recipe.id" :recipe="recipe" />
        </div>
        <Loading v-else />
        <Button v-if="recipeData.length > 0 && lastIndex !== recipeData.length" :handle-click="handleSeeMore" position="center">See More</Button>
    </main>
</template>

<style scoped>
main {
    display: flex;
    flex-direction: column;
   padding: 10px;
}

.all-cards {
    display: grid;

}

@media screen and (min-width:768px) {
    .all-cards {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media screen and (min-width:1024px) {
    .all-cards {
        grid-template-columns: repeat(3, 1fr);
    }
}

@media screen and (min-width:1440px) {
    .all-cards {
        grid-template-columns: repeat(4, 1fr);
    }
}
</style>
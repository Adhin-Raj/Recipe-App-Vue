<script setup>
import { ref } from 'vue';


defineProps(['recipe'])

let isOpen = ref(false)

const handleToggle = () => {
    console.log(isOpen.value)
    isOpen.value = !isOpen.value
}

</script>

<template>
    <section class="card-container">
        <img class="recipe-image" :src="recipe.image" :alt="recipe.title" />
        <h3>{{ recipe.name }}</h3>
        <div v-if="!isOpen">
            <p class="recipe">Difficult of Cooking: <span class="recipe-details">{{ recipe.difficulty }}</span></p>
            <p class="recipe">Average Cooking Time: <span class="recipe-details">{{ recipe.cookTimeMinutes }}</span>
                Minutes</p>
            <p class="recipe">Calories Per Serving: <span class="recipe-details">{{ recipe.caloriesPerServing }}</span>
                kcal</p>
            <p class="recipe">Serving Size: <span class="recipe-details">{{ recipe.servings }}</span> people</p>
            <p class="recipe flex-parent ">Rating: <span class="recipe-details">{{ recipe.rating }}</span> <img
                    src="/public/star.png" width="13" height="13" /></p>
        </div>
        <p v-else class="ingredients"><strong>Ingredients:</strong> {{ `${recipe.instructions}` }} </p>
        <button @click="handleToggle">See Recipe</button>
    </section>
</template>


<style scoped>
.card-container {
    padding-inline: 10px;
    margin: 4px;
    border: 1px solid black;
    letter-spacing: -0.1px;
    border-radius: 8px;
    display: flex;
    flex-direction: column;
}

.recipe-image {
    width: 100%;
    margin-top: 10px;
    height: 350px;
}

h3 {
    text-align: center;
    margin-block: 10px;
}

.ingredients {
    font-size: 14px;
    margin-block: 8px;
    line-height: 130%;
    flex: 1;
}

.recipe {
    margin-block: 4px;
    font-size: 15px;
}

.recipe-details {
    font-weight: 600;
}

button {
    border: none;
    padding-inline: 5px;
    padding-block: 10px;
    width: 100%;
    margin-block: 10px;
    cursor: pointer;
    background: #0c2461;
    font-weight: 600;
    border-radius: 8px;
    color: white;
}

.flex-parent {
    display: flex;
    gap: 4px;
}
</style>
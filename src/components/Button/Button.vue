<script setup>

defineProps({
    handleClick:{
        type:Function
    },
    position:{
        type:String
    }
})


</script>

<template>
    <button @click="handleClick" :style="{ 'align-self': `${position}`  }">
        <slot></slot>
    </button>
</template>


<style scoped>
button {
    border: none;
    padding: 14px 26px;
    margin-block: 12px;
    border-radius: 8px;
    background-color: #FFE08F;
    font-size: 18px;
    font-weight: 600;
    color: #0C2461;
    cursor: pointer;
}

button:hover{
     background-color: #f5cf70;
}
</style>
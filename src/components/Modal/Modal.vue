<script setup>

defineProps({
    close:{
        type:Function
    }
})

</script>

<template> 
    <div class="modal-container">
        <div class="modal-overlay"></div>
        
        <slot></slot>
    </div>
</template>


<style scoped>

.modal-container{
    position: fixed;
    width: 100%;
    height: 100%;
    margin-inline: auto;
}

.modal-overlay{
    position: absolute;
    background-color: white;
    width: 100vw;
    opacity: 0.7;
    height: 100vh;
}

</style>

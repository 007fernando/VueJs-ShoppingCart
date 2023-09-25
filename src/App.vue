<script setup>
 import { ref } from 'vue';
 const header = ref('My Shoppin Cart')
</script>

<template>
   <h1> <i class="material-icons  Shopping-cart-icon"> local_mall</i>  {{ header }}  </h1>
    <TheWelcome />
 
</template>

<style scoped>
.Shopping-cart-icon{
    font-size: 3rem;
}
</style>

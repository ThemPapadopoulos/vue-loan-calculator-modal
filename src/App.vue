<script setup>

import Modal from './components/Modal.vue'


</script>

<template>

 <Modal class="unselectable"/>
 
</template>

<style>
body {
   font-family: 'Roboto', sans-serif;
   margin: auto 0; 
   text-align: center;
   overflow: hidden; 
 }
 .unselectable {
     -webkit-user-select: none; /* Safari */        
-moz-user-select: none; /* Firefox */
-ms-user-select: none; /* IE10+/Edge */
user-select: none; /* Standard */
 }

</style>
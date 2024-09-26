<script setup>
import photoImages from '@/components/photoImages.vue';
import { reactive, ref } from 'vue';

const photoList = reactive([]);

fetch("https://66ccd18b8ca9aa6c8cc8cbc0.mockapi.io/post")
   .then(response => response.json())
    .then(photoImages => {
      photoList.push(...photoImages)
      console.log(photoList)
    });


</script>

<template>
 <photoImages v-for="photo in photoList" :photoImages="photo"></photoImages>

</template>

<style scoped>



</style>

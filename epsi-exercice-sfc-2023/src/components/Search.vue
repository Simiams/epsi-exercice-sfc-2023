<script setup>
import { ref } from 'vue';
import axios from 'axios';

let searchQuery = ref('');

const searchAlbums = async () => {
  const response = await axios.get(`https://api.deezer.com/search/album?q=${searchQuery.value}`);
  emit('search-completed', response.data.data);
};

</script>

<template>
  <form @submit.prevent="searchAlbums">
    <input v-model="searchQuery" type="text" placeholder="Rechercher un album">
    <button type="submit">Rechercher</button>
  </form>
</template>
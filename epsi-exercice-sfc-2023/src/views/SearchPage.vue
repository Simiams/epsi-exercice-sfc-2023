<script setup>
import { ref } from 'vue';
import Search from "@/components/Search.vue";
import MusicCard from "@/components/MusicCard.vue";
let searchResults = ref([]);

const handleSearchCompleted = (results) => {
  searchResults.value = results;
};

</script>

<template>
  <main>
    <Search @search-completed="handleSearchCompleted" />
    <MusicCard v-for="album in searchResults" :key="album.id" :album="album" />
  </main>
</template>
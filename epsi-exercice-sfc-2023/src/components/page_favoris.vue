
<script setup>
import { ref, onMounted } from 'vue';

export default {
  props: ['album'],
  setup(props) {
    const isFavorite = ref(false);

    const ajoutFravoris = () => {
      localStorage.setItem('favoriteAlbum_' + props.album.id, JSON.stringify(props.album));
      isFavorite.value = true;
    };

    const supprimerDeFavoris  = () => {
      localStorage.removeItem('favoriteAlbum_' + props.album.id);
      isFavorite.value = false;
    };

    const checkIsFavorite = () => {
      if (localStorage.getItem('favoriteAlbum_' + props.album.id)) {
        isFavorite.value = true;
      }
    };

    onMounted(checkIsFavorite);

    return { isFavorite, ajoutFravoris, supprimerDeFavoris };
  }
};
</script>

<template>
  <div>
    <h3>Display Component</h3>
    <p>Titre de l'album: {{ album.title }}</p>
    <button v-if="!isFavorite" @click="ajoutFravoris">Ajouter aux favoris</button>
    <button v-else @click="removeFromFavorites">Retirer des favoris</button>
  </div>
</template>

<style scoped>

</style>
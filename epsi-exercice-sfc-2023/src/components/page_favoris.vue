<script>
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

<script>
export default {
  data() {
    return {
      favoriteAlbums: []
    };
  },
  mounted() {
    this.loadFavoriteAlbums();
  },
  methods: {
    loadFavoriteAlbums() {
      for (let i = 0; i < localStorage.length; i++) {
        const key = localStorage.key(i);
        if (key.startsWith('favoriteAlbum_')) {
          const album = JSON.parse(localStorage.getItem(key));
          this.favoriteAlbums.push(album);
        }
      }
    },
    removeFromFavorites(album) {
      this.favoriteAlbums = this.favoriteAlbums.filter(favorite => favorite.id !== album.id);

      localStorage.removeItem('favoriteAlbum_' + album.id);
    }
  }
};
</script>

<template>
  <div>
    <h3>Display Component</h3>
    <p>Titre de l'album: {{ album.title }}</p>
    <button v-if="!isFavorite" @click="ajoutFravoris">Ajouter aux favoris</button>
    <button v-else @click="supprimerDeFavoris">Retirer des favoris</button>
  </div>
  <div>
    <h2>Page des favoris</h2>
    <div v-if="favoriteAlbums.length === 0">
      <p>Aucun album favori pour le moment.</p>
    </div>
    <div v-else>
      <ul>
        <li v-for="album in favoriteAlbums" :key="album.id">
          <router-link :to="'/album/' + album.id">{{ album.title }}</router-link>
          <button @click="removeFromFavorites(album)">Supprimer des favoris</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>

</style>

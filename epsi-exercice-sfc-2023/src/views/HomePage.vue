<script>
import axios from 'axios';
export default {
  name: 'HomePage',
  components: {},
  data() {
    return {
      test: "ma donnée de test",
      albums: []
    }
  },
  methods: {
    getFiftyAlbums: async function () {
      let album = []
      for (let i = 0; i < 1; i++) {
         album.push(this.getRandomAlbums(Math.floor(Math.random() * (999999 - 100000 + 1)) + 100000))
      }
      return album
    },
    async getRandomAlbums(randomNumber) {
      console.log("getRandomAlbums")
      try {
        return await axios.get(`https://api.deezer.com/album/${randomNumber}`).data;
      } catch (error) {
        console.error('Erreur: ', error);
      }
    }
  },
  created() {
    this.albums.push(this.getFiftyAlbums())
  }
}
</script>

<template>
  <main>
    <div v-for="album in albums" :key="album.id">
      <MusicCard musicName="{{album.title}}" albumPhoto="{{album.small_cover}}" msg="bonjour" />
    </div>
  </main>
</template>

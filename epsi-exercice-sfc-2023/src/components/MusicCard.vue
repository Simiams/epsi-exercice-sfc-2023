<template>
  <div class="music-card">
    <div class="music-info">
      <img :src="albumPhoto" alt="Album Cover" class="album-cover">
      <h2>{{ musicName }}</h2>
    </div>
    <button @click="toggleLike" :class="{ 'liked': liked }">
      <i class="fas fa-heart"></i>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    musicName: String,
    albumPhoto: String
  },
  data() {
    return {
      liked: false
    };
  },
  methods: {
    toggleLike() {
      this.liked = !this.liked;
    }
  }
};
</script>

<style scoped>
.music-card {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 10px;
}

.music-info {
  display: flex;
  align-items: center;
}

.album-cover {
  width: 50px;
  height: 50px;
  margin-right: 10px;
}

button {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 20px;
}

button.liked {
  color: red;
}
</style>

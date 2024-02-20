<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import MusicCard from './components/HelloWorld.vue'

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <MusicCard musicName="Nom de la musique" albumPhoto="url_de_l_album.jpg" msg="bonjour" />

      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/search">Search</RouterLink>
        <RouterLink to="/favorites">Favorites</RouterLink>
        <RouterLink :to="{ name: 'album', params: { albumId: 1 }}">User</RouterLink>

      </nav>
    </div>
  </header>

  <RouterView />
</template>

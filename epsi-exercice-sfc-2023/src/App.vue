<script setup>
import { RouterLink } from 'vue-router'

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/search">Search</RouterLink>
        <RouterLink to="/favorites">Favorites</RouterLink>
        <RouterLink :to="{ name: 'album', params: { albumId: 1 }}">User</RouterLink>

      </nav>
    </div>
  </header>
</template>

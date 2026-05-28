<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <v-app>
    <v-app-bar flat density="compact" color="transparent">
      <v-btn to="/" variant="text" size="small">Home</v-btn>
      <v-btn to="/layouts" variant="text" size="small">Layout Showcase</v-btn>
    </v-app-bar>
    <v-main>
      <RouterView />
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
defineProps<{
  label: string
  url: string
  icon: string
}>()
</script>

<template>
  <v-list-item
    :href="url"
    :prepend-icon="icon"
    class="link-button mb-2"
    border
    rounded
  >
    <v-list-item-title class="text-uppercase font-weight-medium" style="letter-spacing: 0.08em;">
      {{ label }}
    </v-list-item-title>
  </v-list-item>
</template>

<style scoped>
.link-button {
  transition: background 0.15s, color 0.15s;
}

.link-button:hover {
  background: #000;
  color: #fff;
}
</style>

<script setup lang="ts">
const links = [
  { label: 'Portfolio', url: '#', icon: 'mdi-briefcase-outline' },
  { label: 'Dribbble', url: '#', icon: 'mdi-basketball' },
  { label: 'LinkedIn', url: '#', icon: 'mdi-linkedin' },
  { label: 'Email', url: 'mailto:hello@mattppenfield.com', icon: 'mdi-email-outline' },
]
</script>

<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" md="7">
        <h1 class="name">Matt<br />Penfield</h1>
        <v-divider class="my-4" thickness="2" length="280" color="black" />
        <p class="text-body-1 font-weight-light" style="letter-spacing: 0.02em; max-width: 280px;">
          Designer, builder, creative technologist.
        </p>
      </v-col>

      <v-col cols="12" md="5">
        <v-list lines="one" bg-color="transparent" class="pa-0">
          <v-list-item
            v-for="link in links"
            :key="link.label"
            :href="link.url"
            :prepend-icon="link.icon"
            class="link-item mb-2"
            border
            rounded
          >
            <v-list-item-title class="text-uppercase font-weight-medium" style="letter-spacing: 0.08em;">
              {{ link.label }}
            </v-list-item-title>
          </v-list-item>
        </v-list>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.name {
  font-size: clamp(4rem, 10vw, 9rem);
  font-weight: 700;
  line-height: 0.85;
  letter-spacing: -0.04em;
  text-transform: uppercase;
}

.link-item {
  transition: background 0.15s, color 0.15s;
}

.link-item:hover {
  background: #000;
  color: #fff;
}

@media (max-width: 680px) {
  .name {
    font-size: clamp(3rem, 14vw, 5rem);
  }
}
</style>

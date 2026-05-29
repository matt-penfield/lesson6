<script setup lang="ts">
import LinkButton from '@/components/LinkButton.vue'

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
          <LinkButton
            v-for="link in links"
            :key="link.label"
            :label="link.label"
            :url="link.url"
            :icon="link.icon"
          />
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
  margin-top: 0;
}

@media (max-width: 680px) {
  .name {
    font-size: clamp(3rem, 14vw, 5rem);
  }
}
</style>

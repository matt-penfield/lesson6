<script setup lang="ts">
import { ref } from 'vue'

const links = [
  { label: 'Portfolio', url: '#', icon: 'mdi-briefcase-outline' },
  { label: 'Dribbble', url: '#', icon: 'mdi-basketball' },
  { label: 'LinkedIn', url: '#', icon: 'mdi-linkedin' },
  { label: 'Email', url: 'mailto:hello@mattppenfield.com', icon: 'mdi-email-outline' },
]

const overlays = ref<Record<string, boolean>>({
  'layout1-grid': true,
  'layout1-hierarchy': true,
  'layout2-center': true,
  'layout2-cards': true,
  'layout3-nav': true,
  'layout3-asymmetry': true,
})

function dismiss(key: string) {
  overlays.value[key] = false
}

function resetOverlays() {
  Object.keys(overlays.value).forEach(k => overlays.value[k] = true)
}
</script>

<template>
  <v-container class="py-12">
    <div class="d-flex align-center mb-8">
      <div>
        <h2 class="text-h4 font-weight-bold">Layout Comparison</h2>
        <p class="text-body-2 text-medium-emphasis mt-1">Three approaches to the same content — hover overlays explain key decisions.</p>
      </div>
      <v-spacer />
      <v-btn variant="tonal" size="small" @click="resetOverlays" prepend-icon="mdi-restore">
        Reset Overlays
      </v-btn>
    </div>

    <!-- LAYOUT 1: Split Grid (current) -->
    <v-card class="mb-12" variant="outlined">
      <v-toolbar flat density="compact" color="grey-lighten-4">
        <v-toolbar-title class="text-body-1 font-weight-medium">Layout A — Split Grid</v-toolbar-title>
      </v-toolbar>

      <v-card-text class="pa-0">
        <div class="layout-preview layout-1">
          <!-- Overlay: Grid decision -->
          <v-overlay
            v-model="overlays['layout1-grid']"
            contained
            scrim="black"
            class="align-start justify-start pa-6"
            persistent
            no-click-animation
          >
            <v-card max-width="360" class="pa-4" color="white">
              <div class="d-flex align-start">
                <v-icon color="primary" class="mr-3 mt-1">mdi-grid</v-icon>
                <div>
                  <p class="text-body-2 font-weight-bold mb-1">Asymmetric Column Split (7 / 5)</p>
                  <p class="text-body-2 text-medium-emphasis">
                    A wider left column gives the name visual dominance while the narrower right column
                    creates a clear secondary zone. This ratio avoids the static feel of 50/50 splits and
                    creates natural reading flow from name → links.
                  </p>
                </div>
                <v-btn icon="mdi-close" size="x-small" variant="text" @click="dismiss('layout1-grid')" />
              </div>
            </v-card>
          </v-overlay>

          <!-- Overlay: Hierarchy decision -->
          <v-overlay
            v-model="overlays['layout1-hierarchy']"
            contained
            scrim="transparent"
            class="align-end justify-end pa-6"
            persistent
            no-click-animation
          >
            <v-card max-width="320" class="pa-4" color="grey-darken-4">
              <div class="d-flex align-start">
                <v-icon color="amber" class="mr-3 mt-1">mdi-format-size</v-icon>
                <div>
                  <p class="text-body-2 font-weight-bold mb-1 text-white">Scale-Based Hierarchy</p>
                  <p class="text-body-2 text-grey-lighten-1">
                    The name at 9rem vs. links at 1rem creates a ~9:1 size ratio — an extreme contrast that
                    instantly communicates what matters most. The divider acts as a visual "bridge" between scales.
                  </p>
                </div>
                <v-btn icon="mdi-close" size="x-small" variant="text" color="white" @click="dismiss('layout1-hierarchy')" />
              </div>
            </v-card>
          </v-overlay>

          <!-- Actual layout content -->
          <v-container fluid class="fill-height">
            <v-row align="center" justify="center">
              <v-col cols="12" md="7">
                <h1 class="name-display">Matt<br />Penfield</h1>
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
        </div>
      </v-card-text>
    </v-card>

    <!-- LAYOUT 2: Centered Stack -->
    <v-card class="mb-12" variant="outlined">
      <v-toolbar flat density="compact" color="grey-lighten-4">
        <v-toolbar-title class="text-body-1 font-weight-medium">Layout B — Centered Stack</v-toolbar-title>
      </v-toolbar>

      <v-card-text class="pa-0">
        <div class="layout-preview layout-2">
          <!-- Overlay: Center decision -->
          <v-overlay
            v-model="overlays['layout2-center']"
            contained
            scrim="black"
            class="align-start justify-center pa-6"
            persistent
            no-click-animation
          >
            <v-card max-width="380" class="pa-4" color="white">
              <div class="d-flex align-start">
                <v-icon color="deep-purple" class="mr-3 mt-1">mdi-format-align-center</v-icon>
                <div>
                  <p class="text-body-2 font-weight-bold mb-1">Centered Single-Column</p>
                  <p class="text-body-2 text-medium-emphasis">
                    Centering everything forces a focused, sequential reading order — name, then tagline,
                    then actions. This works well for mobile-first design and creates a calm, editorial feel.
                    The tradeoff: less visual tension and energy than asymmetric layouts.
                  </p>
                </div>
                <v-btn icon="mdi-close" size="x-small" variant="text" @click="dismiss('layout2-center')" />
              </div>
            </v-card>
          </v-overlay>

          <!-- Overlay: Card decision -->
          <v-overlay
            v-model="overlays['layout2-cards']"
            contained
            scrim="transparent"
            class="align-end justify-center pa-6"
            persistent
            no-click-animation
          >
            <v-card max-width="340" class="pa-4" color="grey-darken-4">
              <div class="d-flex align-start">
                <v-icon color="light-green" class="mr-3 mt-1">mdi-card-outline</v-icon>
                <div>
                  <p class="text-body-2 font-weight-bold mb-1 text-white">Inline Button Row</p>
                  <p class="text-body-2 text-grey-lighten-1">
                    Horizontal buttons reduce vertical scrolling and give equal visual weight to all actions.
                    This signals "choose one" rather than a ranked list, making each link feel equally important.
                  </p>
                </div>
                <v-btn icon="mdi-close" size="x-small" variant="text" color="white" @click="dismiss('layout2-cards')" />
              </div>
            </v-card>
          </v-overlay>

          <!-- Actual layout content -->
          <v-container fluid class="fill-height">
            <v-row align="center" justify="center">
              <v-col cols="12" md="8" class="text-center">
                <h1 class="name-display mb-4">Matt Penfield</h1>
                <p class="text-h6 font-weight-light mb-8" style="letter-spacing: 0.02em;">
                  Designer, builder, creative technologist.
                </p>
                <div class="d-flex flex-wrap justify-center ga-3">
                  <v-btn
                    v-for="link in links"
                    :key="link.label"
                    :href="link.url"
                    :prepend-icon="link.icon"
                    variant="outlined"
                    color="black"
                    size="large"
                    rounded="pill"
                  >
                    {{ link.label }}
                  </v-btn>
                </div>
              </v-col>
            </v-row>
          </v-container>
        </div>
      </v-card-text>
    </v-card>

    <!-- LAYOUT 3: Sidebar Navigation -->
    <v-card class="mb-12" variant="outlined">
      <v-toolbar flat density="compact" color="grey-lighten-4">
        <v-toolbar-title class="text-body-1 font-weight-medium">Layout C — Sidebar Navigation</v-toolbar-title>
      </v-toolbar>

      <v-card-text class="pa-0">
        <div class="layout-preview layout-3">
          <!-- Overlay: Nav decision -->
          <v-overlay
            v-model="overlays['layout3-nav']"
            contained
            scrim="black"
            class="align-start justify-start pa-6"
            persistent
            no-click-animation
          >
            <v-card max-width="340" class="pa-4" color="white">
              <div class="d-flex align-start">
                <v-icon color="teal" class="mr-3 mt-1">mdi-page-layout-sidebar-left</v-icon>
                <div>
                  <p class="text-body-2 font-weight-bold mb-1">Fixed Navigation Rail</p>
                  <p class="text-body-2 text-medium-emphasis">
                    A persistent sidebar with icon-only navigation keeps links always accessible without
                    competing with the main content. This pattern scales well — you can add pages without
                    redesigning the layout.
                  </p>
                </div>
                <v-btn icon="mdi-close" size="x-small" variant="text" @click="dismiss('layout3-nav')" />
              </div>
            </v-card>
          </v-overlay>

          <!-- Overlay: Asymmetry decision -->
          <v-overlay
            v-model="overlays['layout3-asymmetry']"
            contained
            scrim="transparent"
            class="align-center justify-end pa-6"
            persistent
            no-click-animation
          >
            <v-card max-width="320" class="pa-4" color="grey-darken-4">
              <div class="d-flex align-start">
                <v-icon color="orange" class="mr-3 mt-1">mdi-arrow-expand-horizontal</v-icon>
                <div>
                  <p class="text-body-2 font-weight-bold mb-1 text-white">Full-Bleed Content Area</p>
                  <p class="text-body-2 text-grey-lighten-1">
                    With navigation handled by the rail, the content area can use all available space.
                    This creates a dramatic, poster-like presentation that emphasizes the name as a brand mark.
                  </p>
                </div>
                <v-btn icon="mdi-close" size="x-small" variant="text" color="white" @click="dismiss('layout3-asymmetry')" />
              </div>
            </v-card>
          </v-overlay>

          <!-- Actual layout content -->
          <div class="d-flex fill-height">
            <v-navigation-drawer permanent width="72" class="layout-3-rail">
              <div class="d-flex flex-column align-center py-6 ga-4 fill-height">
                <v-btn
                  v-for="link in links"
                  :key="link.label"
                  :href="link.url"
                  :icon="link.icon"
                  variant="text"
                  size="large"
                />
                <v-spacer />
                <v-avatar size="36" color="black">
                  <span class="text-white text-body-2 font-weight-bold">MP</span>
                </v-avatar>
              </div>
            </v-navigation-drawer>

            <v-container fluid class="fill-height">
              <v-row align="center" justify="center" class="fill-height">
                <v-col cols="12" class="text-center">
                  <h1 class="name-display-lg">Matt<br />Penfield</h1>
                  <p class="text-body-1 font-weight-light mt-6" style="letter-spacing: 0.02em;">
                    Designer, builder, creative technologist.
                  </p>
                </v-col>
              </v-row>
            </v-container>
          </div>
        </div>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<style scoped>
.layout-preview {
  position: relative;
  min-height: 500px;
  overflow: hidden;
}

.name-display {
  font-size: clamp(3rem, 8vw, 7rem);
  font-weight: 700;
  line-height: 0.85;
  letter-spacing: -0.04em;
  text-transform: uppercase;
  margin-top: 0;
}

.name-display-lg {
  font-size: clamp(4rem, 10vw, 10rem);
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

.layout-3-rail {
  border-right: 1px solid rgba(0, 0, 0, 0.12);
}
</style>

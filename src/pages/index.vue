<template>
  <div class="index-page">
    <featureSlider class="mb-15" :projects="projects" />
    <v-container class="mb-15">
      <v-row>
        <v-col>
          <v-btn target="_blank" class="px-0 mx-0" color="white" elevation="0">
            <v-icon class="black--text">mdi-{{ page.icon }}</v-icon
            >&nbsp;
            <h2>{{ page.title }}</h2>
          </v-btn>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
          <nuxt-content :document="page" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import featureSlider from '~/components/featureSlider.vue'

export default {
  components: {
    featureSlider,
  },
  async asyncData({ $content }) {
    const page = await $content('hello').fetch()
    const projects = await $content('projects')
      .without(['body'])
      .sortBy('path')
      .fetch()

    return {
      page,
      projects,
    }
  },
  head() {
    return {
      title: 'Welcome to my site!',
    }
  },
}
</script>

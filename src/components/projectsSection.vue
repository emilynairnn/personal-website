<template>
  <div class="projects-section w-100 mb-15">
    <v-row>
      <v-col>
        <v-btn href="/projects/" class="px-0 mx-0" color="white" elevation="0">
          <v-icon class="black--text">mdi-apps</v-icon>&nbsp;
          <h2>Projects</h2>
        </v-btn>
      </v-col>
    </v-row>
    <v-row class="mb-5">
      <v-col cols="6" v-for="project in projects" :key="project.slug">
        <a
          :href="`/projects/${project.slug}`"
          class="black--text text-decoration-none"
        >
          <v-img
            :src="project.featuredImage"
            aspect-ratio="1.8"
            :contain="false"
            class="mb-3 grey lighten-3"
          ></v-img>
          <h3 class="text-h4 mb-5">
            {{ project.title }}
          </h3>
        </a>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import preloader from '~/components/preloader.vue'

export default {
  components: {
    preloader,
  },
  data() {
    return {
      projects: [],
    }
  },
  methods: {
    async loadProjects() {
      return this.$content('projects')
        .only(['title', 'featuredImage', 'slug'])
        .sortBy('path')
        .fetch()
        .catch((error) => console.error(error))
    },
    filterProjects(allProjects) {
      const slug = this.$route.params.slug
      return allProjects.filter((f) => f.slug !== slug)
    },
  },
  async fetch() {
    const allProjects = await this.loadProjects()
    this.projects = this.filterProjects(allProjects)
  },
  watch: {
    '$route.params.slug': function () {
      const vm = this
      this.loadProjects().then((allProjects) => {
        vm.projects = vm.filterProjects(allProjects)
      })
    },
  },
}
</script>

<style lang="scss">
</style>

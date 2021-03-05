<template>
  <v-app>
    <headerNav />
    <v-main>
      <transition name="fade">
        <nuxt />
      </transition>
    </v-main>
    <v-container>
      <projectsSection />
      <githubSection />
      <mediumSection />
    </v-container>
    <contactSection />
    <footerSection />
  </v-app>
</template>

<script>
import mediumSection from '~/components/mediumSection.vue'
import githubSection from '~/components/githubSection.vue'
import projectsSection from '~/components/projectsSection.vue'
import footerSection from '~/components/footerSection.vue'
import headerNav from '~/components/headerNav.vue'
import contactSection from '~/components/contactSection'

export default {
  components: {
    headerNav,
    mediumSection,
    githubSection,
    projectsSection,
    footerSection,
    contactSection
  },
  computed: {
    isContactVisible() {
      return this.$store.state.contact.isVisible
    },
  },
}
</script>

<style lang="scss">
@import 'assets/styles/index.scss';
</style>

<template>
  <v-container fluid class="feature-slider">
    <v-row>
      <v-col class="py-0 w-100">
        <v-carousel height="600" v-model="realIndex" class="black">
          <v-carousel-item
            v-if="!!projects.length"
            v-for="(project, index) in projects"
            :key="projects.slug"
          >
            <v-img
              :src="project.featuredImage"
              height="100%"
              tile
              class="d-flex"
            >
              <v-row class="fill-height">
                <v-col cols="12" md="6" class="fill-height py-0 mt-3 p-relative">
                  <v-sheet
                    class="color-block p-relative"
                    :color="project.color"
                    height="100%"
                    tile
                  />
                  <nuxt-link
                    :to="'/projects/' + project.slug"
                    class="align-center d-flex fill-height text-decoration-none white--text p-absolute w-100 full-screen"
                  >
                    <div class="mx-auto h-100 mx-auto text-center px-5">
                      <h2 class="text-h4 font-weight-bold mb-4 px-10">
                        {{ project.title }}
                      </h2>
                      <p class="text-h6 mb-15 px-10">
                        {{ project.description }}
                      </p>
                      <v-btn
                        :to="'/projects/' + project.slug"
                        color="white"
                        elevation="0"
                        class="text-h6 text-capitalize py-6"
                        text
                      >
                        Learn More
                      </v-btn>
                    </div>
                  </nuxt-link>
                </v-col>
              </v-row>
            </v-img>
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: {
    projects: {
      required: true,
      type: Array,
    },
  },
  created() {
    let vm = this
    if (process.client) {
      // Prevent rendering issues.
      document.fonts.ready.then(function () {
        vm.loaded = document.fonts.check('1em futura-pt') // true
      })
      setTimeout(function () {
        vm.loaded = true
      }, 2000)
    }
  },
  data() {
    return {
      realIndex: -1,
      loaded: false,
    }
  },
}
</script>

<style lang="scss">
@import 'assets/styles/variables.scss';

.feature-slider {
  .color-block {
    opacity: 0.7;
  }
  .full-screen {
    top: 0;
    left: 0;
    right: 0;
  }
}
</style>
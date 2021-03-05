<template>
  <div class="d-flex w-100">
    <v-container fluid class="white sticky-header">
      <v-row>
        <nuxt-link to="/" class="ma-0 pa-0 d-flex black--text">
          <v-col class="align-self-center">
            <h1 class="d-flex">My Portfolio</h1>
          </v-col>
        </nuxt-link>
        <v-spacer />
      </v-row>
    </v-container>
    <div class="sticky-padding">&nbsp;</div>
  </div>
</template>

<script>
export default {
}
</script>

<style lang="scss">
@import 'assets/styles/variables.scss';
.sticky-header {
  top: 0;
  position: fixed;
  z-index: 1;
  a {
    color: black;
    text-decoration: none;
  }
}
.sticky-padding {
  height: $header-height;
}
</style>
<template>
  <div class="d-flex white">
    <v-container fluid>
      <v-row>
        <v-col class="left-col black white--text py-15" cols="12" md="6">
          <v-row>
            <v-col cols="4" md="3" offset="0" offset-sm="1">
              <v-img
                class="w-100 rounded-circle mb-5"
                :src="$github.user.avatarUrl"
              ></v-img>
            </v-col>
            <v-col cols="8" md="5" offset="0" offset-sm="1">
              <h2 class="text-h3 mb-5">Let's Talk</h2>
              <p class="d-none d-sm-block">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                eiusmod tempor incididunt ut labore et dolore magna aliqua.
                Porttitor massa id neque aliquam vestibulum morbi blandit. Nam
                aliquam sem et tortor consequat id porta nibh. Lectus arcu
                bibendum at varius vel pharetra vel turpis. Diam ut venenatis
                tellus in metus vulputate.
              </p>
              <p class="d-none d-sm-block">
                Available for freelance and other opportunities.
              </p>
            </v-col>
          </v-row>
        </v-col>
        <v-col class="grey lighten-4 py-15">
          <v-row>
            <v-col cols="12" md="10" offset="0" offset-sm="1">
              <contactForm />
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import contactForm from './contactForm'
import socialLinks from './socialLinks'

export default {
  components: {
    contactForm,
    socialLinks,
  },
}
</script>

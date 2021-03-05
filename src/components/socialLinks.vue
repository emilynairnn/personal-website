<template>
  <v-row class="social-links">
    <v-col v-for="social in socials" :key="social.url" cols="4">
      <v-btn
        :href="social.url"
        target="_blank"
        fab
        small
        color="white"
        class="mr-5"
      >
        <v-icon color="black"> mdi-{{ social.icon }} </v-icon>
      </v-btn>
    </v-col>
  </v-row>
</template>

<script>
export default {
  computed: {
    socials() {
      const guthubUrl = this.$github.user.url
      const twitterUrl = this.$github.user.twitterUsername

      // icons from:
      // https://materialdesignicons.com/
      return [
        {
          icon: 'github',
          url: guthubUrl,
        },
        {
          icon: 'linkedin',
          url: 'https://www.linkedin.com/',
        },
        {
          icon: 'twitter',
          url: `http://twitter.com/${twitterUrl}`,
        },
      ]
    },
  },
}
</script>
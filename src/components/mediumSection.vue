<template>
  <div class="medium-section w-100 mb-15">
    <v-row>
      <v-col>
        <v-btn
          :href="`https://medium.com/${author}`"
          target="_blank"
          class="px-0 mx-0"
          color="white"
          elevation="0"
        >
          <v-icon class="black--text">mdi-book</v-icon>&nbsp;
          <h2>Blog Posts</h2>
        </v-btn>
      </v-col>
    </v-row>

    <v-row v-for="post in posts" :key="post.id" class="mb-5">
      <v-col cols="12" class="d-flex d-md-none">
        <v-img :src="post.image" aspect-ratio="1.8" :contain="false"></v-img>
      </v-col>
      <v-col cols="12" md="8">
        <v-row>
          <v-col cols="12">
            <a :href="post.url" class="black--text" target="_blank">
              <h3 class="text-h4 mb-5">
                {{ post.title }}
              </h3>
            </a>
          </v-col>
          <v-col cols="8">
            <p>
              {{ post.description }}
            </p>
          </v-col>
        </v-row>
      </v-col>
      <v-col cols="4" class="d-none d-md-flex">
        <v-img :src="post.image" aspect-ratio="1.8" :contain="false"></v-img>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      posts: [],
      author: 'td-lab',
    }
  },
  async fetch() {
    const author = this.author
    try {
      const response = await axios(
        `https://mediumpostsapi.herokuapp.com/?usermedium=${author}`
      )
      console.log(response)
      this.posts = response.data.dataMedium
    } catch (error) {
      console.error(error)
    }
  },
}
</script>

<template>
  <div class="project-page" :class="{ 'no-image-border': page.noImageBorder }">
    <v-container class="mb-15">
      <v-row>
        <v-col class="mt-15 text-xs-center">
          <h1
            class="font-weight-regular text-h2 text-center mb-3"
            :class="[`${page.color}--text`]"
          >
            {{ page.title }}
          </h1>
          <hr :class="[page.color]" class="mb-15" />
          <nuxt-content :document="page" />
          <hr :class="[page.color]" class="mb-15" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    console.log(params)
    const page = await $content('projects')
      .where({
        slug: params.slug,
      })
      .fetch()

    console.log(page)
    return {
      page: page[0],
    }
  },
  head() {
    return {
      title: this.page.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.page.longDescription,
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content: this.page.featuredImage,
        },
      ],
    }
  },
  computed: {
    longDescHTML() {
      if (!this.page['longDescription']) {
        return '<p></p>'
      }
      let longDesc = this.page.longDescription
      const searchRegExp = /\n\n/g
      longDesc = longDesc.replace(searchRegExp, '</p><p>')
      longDesc = '<p>' + longDesc + '</p>'
      return longDesc
    },
  },
}
</script>

<style lang="scss">
.project-page {
  hr {
    height: 5px;
    border: none;
  }
}
</style>

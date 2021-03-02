<template>
  <b-container>
    <b-row>
      <b-col class="text-center">
      <Logo />
      <h1 class="title">
        nuxt-blog-test
      </h1>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
      </b-col>
    </b-row>

    <b-row>

      <b-col md="4" lg="3" v-for="blogpost of blogposts" :key="blogpost.slug">

        <NuxtLink :to="{ name: 'blog-slug', params: { slug: blogpost.slug } }">
          <img :src="blogpost.img" />
          <div>
            <h2>{{ blogpost.title }}</h2>
            <p>{{ blogpost.description }}</p>
          </div>
        </NuxtLink>

      </b-col>

    </b-row>
  </b-container>
</template>


<script>
  export default {
    async asyncData({ $content, params }) {
      const blogposts = await $content('blog')
        .only(['title', 'description', 'img', 'slug'])
        .sortBy('createdAt', 'asc')
        .fetch()

      return {
        blogposts
      }
    }
  }
</script>

<style>

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

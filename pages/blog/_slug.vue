<template>
  <article>
    <b-container>
      <b-row class="justify-content-center my-5">
        <b-col md="10" lg="8">
          <b-img
            fluid
            rounded
            :src="require(`~/assets/img/${blogpost.img}`)"
            :alt="blogpost.alt"
          />
        </b-col>
      </b-row>

      <b-row class="justify-content-center text-center my-5">
        <b-col md="10" lg="8">
          <h1>{{ blogpost.title }}</h1>
          <p>{{ blogpost.description }}</p>
          <p>{{ formatDate(blogpost.createdAt) }}</p>
        </b-col>
      </b-row>

      <b-row class="justify-content-center my-5">
        <b-col md="10" lg="8">
          <nuxt-content :document="blogpost" />
        </b-col>
      </b-row>

      <b-row class="justify-content-center my-5">
        <b-col>
          <pre class="bg-secondary text-white rounded">{{ blogpost }}</pre>
        </b-col>
      </b-row>
    </b-container>
  </article>
</template>



<script>
export default {
  async asyncData({ $content, params }) {
    const blogpost = await $content('blog', params.slug).fetch();

    return { blogpost };
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' };
      return new Date(date).toLocaleDateString('en', options);
    },
  },
};
</script>

<style>
</style>

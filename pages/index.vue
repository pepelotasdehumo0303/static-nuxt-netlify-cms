<template>
  <section class="section">
    <ul>
      <li v-for="post in posts" :key="post.slug">
        <nuxt-link :to="`/blog/${post.slug}`">{{ post.title }}</nuxt-link>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'HomePage',
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  async asyncData({$content}) {
    const posts = await $content('blog').only(['title', 'description', 'slug']).fetch();
    return { posts }
  }
}
</script>

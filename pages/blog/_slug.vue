<template>
  <main>
    <nuxt-content :document="post"></nuxt-content>
  </main>
</template>

<script>
export default {
  async asyncData({$content, params}) {
    const post = await $content('blog', params.slug).fetch();
    return { post }
  }
}
</script>

<style>

</style>
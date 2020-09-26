<template>
  <div>
    <h1>Blog list</h1>
    <ul>
      <li v-for="item in blogList">
        <nuxt-link :to="'blog/' + item.slug">{{ item.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "index",
  async asyncData({ $content }) {
    const blogItems = await $content('blogs')
        .fetch()
        .catch(err => {
          error({ statusCode: 404, message: "Page not found" });
        });

    return {
      blogList: blogItems
    }
  }
}
</script>

<style scoped>

</style>
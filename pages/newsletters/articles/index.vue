<template>
  <main>
    <section v-if="post" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Articles</h1>
      <post post-type="articles" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let post;
    try {
      post = await $content("articles").fetch();
    } catch (e) {
      error({ message: "articles post not found" });
    }
    return { post };
  },
}
</script>

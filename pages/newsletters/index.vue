<template>
  <main>
    <section v-if="post" class="w-full max-w-5xl mx-auto">
      <h1 class="title">newsletters</h1>
      <post post-type="newsletters" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let post;
    try {
      post = await $content("newsletters").fetch();
    } catch (e) {
      error({ message: "news post not found" });
    }
    return { post };
  },
}
</script>

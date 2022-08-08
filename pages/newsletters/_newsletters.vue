<template>
  <main>
    <section v-if="post">
       <div class="container flex mx-auto">
          <nav class="py-3 px-6 my-2" aria-label="go back">
            <router-back class="" />
          </nav>
       </div>
      <article class="container mx-auto px-6">
        
          <!-- <h5
          v-if="post.createdAt"
          class="inline-block py-1 px-2 my-2 bg-gray text-black text-sm font-medium rounded-sm whitespace-no-wrap"
        >{{ formatDate(post.createdAt) }}</h5> -->
        
        <h1 class="">{{ post.title }}</h1>
        <p class="mt-1 mb-4 text-black dark:text-primary-400">{{ post.description }}</p>
        <nuxt-content :document="post" />
      </article>
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("newsletters", params.news).fetch();
    } catch (e) {
      error({ message: "newsletters post not found" });
    }
    return { post };
  },
  methods: {
    formatDate(dateString) {
      const date = new Date(dateString)
      return date.toLocaleDateString(process.env.lang) || ''
    }
  }
}
</script>
<style>
article {
  max-width: 100%;
  margin-top: 3rem;
}
.nuxt-content-container {
  z-index: -1;
}
.nuxt-content {
  max-width: 100%;
}
</style>

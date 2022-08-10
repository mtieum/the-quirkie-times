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
      post = await $content("articles", params.articles).fetch();
    } catch (e) {
      error({ message: "articles post not found" });
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
.wrap .left {
  float: right;
  margin: 0 0 0 25px;
}
.wrap .right {
  float: left;
  margin: 0 25px 0 0;
}
.size_sm .vertical {
  max-width: 100px;
}
.size_md .vertical {
  max-width: 200px;
}
.size_lg .vertical {
  max-width: 300px;
}
.size_full .vertical {
  max-width: 100%;
}

.size_sm .horizontal {
  max-height: 100px;
}
.size_md .horizontal {
  max-height: 200px;
}
.size_lg .horizontal {
  max-height: 300px;
}
.size_full .horizontal {
  max-height: 100%;
}
</style>

<template>
  <main>
    <section v-if="post" class="max-w-7xl w-full mx-auto">
       <div class="container flex mx-auto">
          <nav class="py-3 px-6 my-2" aria-label="go back">

            <div class="cursor-pointer" @click="$router.back()">
              <svg width="38" height="8" viewBox="0 0 38 8" xmlns="http://www.w3.org/2000/svg" class="inline">
                <path d="M0.646446 3.64644C0.451183 3.84171 0.451183 4.15829 0.646446 4.35355L3.82843 7.53553C4.02369 7.73079 4.34027 7.73079 4.53553 7.53553C4.7308 7.34027 4.7308 7.02369 4.53553 6.82842L1.70711 4L4.53553 1.17157C4.7308 0.976308 4.7308 0.659725 4.53553 0.464463C4.34027 0.269201 4.02369 0.269201 3.82843 0.464463L0.646446 3.64644ZM38 3.5L1 3.5L1 4.5L38 4.5L38 3.5Z" fill="currentColor"/>
              </svg> Go Back
            </div>
          </nav>
       </div>
      <article class="container mx-auto px-6">  
        <h1 class="mb-3">{{ post.title }}</h1>
        <p class="mt-1 mb-4 text-black dark:text-primary-400">{{ post.description }}</p>
        <nuxt-content :document="post" />
      </article>
    </section>
    <div v-if="post.searchwords === true" class="text-center">
      <WordSearch />
    </div>
  </main>
</template>

<script>
import WordSearch from '~/components/global/WordSearch.vue';
export default {
    async asyncData({ $content, params, error }) {
        let post;
        try {
            post = await $content("articles", params.articles).fetch();
        }
        catch (e) {
            error({ message: "articles post not found" });
        }
        return { post };
    },
    methods: {
        formatDate(dateString) {
            const date = new Date(dateString);
            return date.toLocaleDateString(process.env.lang) || "";
        }
    },
    components: { WordSearch }
}
</script>
<style>
/*! purgecss start ignore */
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
p {
  font-size: 1.15rem;
  margin: 15px 0;
}
img.wrap {
padding: 0;
}
.wrap.left {
  float: right;
  margin: 0;
  @media screen and (min-width: 768px) {
    margin: 0 0 15px 15px;
  }
}
.wrap.right {
  float: left;
  margin: 0;
  @media screen and (min-width: 768px) {
    margin: 0 15px 15px 0;
  }
}
.wrap.left.vertical {
  margin: 0 0 15px 15px !important;
}
.wrap.right.vertical {
  margin: 0 15px 15px 0 !important;
}
.size_sm.vertical {
  max-width: 100px;
}
.size_md.vertical {
  max-width: 200px;
}
.size_lg.vertical {
  max-width: 300px;
}
.size_full.vertical {
  max-width: 100%;
}

.size_sm.horizontal {
  max-height: 200px;
}
.size_md.horizontal {
  max-height: 300px;
}
.size_lg.horizontal {
  max-height: 400px;
}
.size_full.horizontal {
  max-height: 100%;
}
/*! purgecss end ignore */
</style>

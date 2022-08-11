<template>
  <div class="flex flex-col justify-content-start">
    <div v-if="posts.length > 0" class="grid grid-rows-6 sm:grid-rows-3 lg:grid-rows-2 grid-flow-col gap-4">
      <div v-for="(post, index) in posts" :key="index" class="border border-solid border-primary-200 p-4">
        <div v-if="(postType === 'articles') && (post.category === cat)" class="">
          <nuxt-link :to="`/newsletters/${postType}/${post.slug}`" class="card card--clickable article">
            <template>
              <span class="w-full">
                <span class="flex justify-between align-baseline">
                  <h3 class="card-title mb-3">{{ post.title }}</h3>
                </span>
                <p v-if="post.description" class="my-2 desc">{{ post.description }}</p>
                <p v-if="post.excerpt" class="my-2 excerpt">{{ post.excerpt }}</p>
              </span>
            </template>
          </nuxt-link>
        </div>
        <div v-else></div>
      
      </div>
    </div>
    <div v-else-if="loading" class="cards">
      <div v-for="placeholder in placeholderClasses" :key="placeholder.id" class="card">
        <content-placeholders :rounded="true" :class="placeholder">
          <content-placeholders-heading />
        </content-placeholders>
      </div>
    </div>
    <p v-else class="max-w-5xl mx-auto">
      {{ amount > 1 ? 'No posts found' : 'No post found' }}
    </p>
  </div>
</template>

<script>
  export default {
    name: 'Posts',
    props: {
      postType: {
        type: String,
        default: 'articles',
        validator: (val) => ['articles'].includes(val),
      },
      cat: {
        type: String,
        default: '',
      },
      amount: { // ? https://content.nuxtjs.org/fetching#limitn
        type: Number,
        default: 10,
        validator: (val) => val >= 0 && val < 100,
      },
      sortBy: { // ? https://content.nuxtjs.org/fetching#sortbykey-direction
        type: Object,
        default: () => ({
          key: 'slug',
          direction: 'asc' // you probably want 'asc' here
        }),
        validator: (obj) => typeof obj.key === 'string' && typeof obj.direction === 'string',
      }
    },
    data() {
      return {
        posts: [],
        //issue: this.cat,
        loading: true,
      }
    },
    computed: {
      placeholderClasses() {
        const classes = ['w-full'];
        return [...Array.from({ length: this.amount }, (v, i) => classes[i % classes.length])]; // repeats classes after one another
      }
    },
    async mounted() {
      this.loading = true;
      this.posts = await this.fetchPosts();
      this.loading = false;
    },
    methods: {
      formatDate(dateString) {
        const date = new Date(dateString)
        return date.toLocaleDateString(process.env.lang) || ''
      },
      async fetchPosts(
          postType = this.postType,
          amount = this.amount,
          sortBy = this.sortBy,
        ) {
        return this.$content(postType)
          .sortBy(sortBy.key, sortBy.direction)
          .limit(amount)
          .fetch()
          .catch((err) => console.error(err) || []);
      }
    },
  }
</script>

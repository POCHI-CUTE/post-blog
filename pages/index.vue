<template>
  <div>
    <label>
      blog title:
      <input v-model="article.title" placeholder="title" />
    </label>
    <post-component @catch="updateText" />
    <button @click="submit">submit</button>
  </div>
</template>

<script>
import postComponent from '~/components/post.vue'
export default {
  name: 'IndexPage',
  components: {
    postComponent,
  },
  data() {
    return {
      article: {
        title: '',
        body: '',
      },
    }
  },
  methods: {
    updateText(markupText) {
      this.article.body = markupText
    },
    async submit() {
      await this.$axios.$post('/', this.article, {
        headers: {
          'Content-Type': 'application/json',
          'X-MICROCMS-API-KEY': this.$config.apiKey,
        },
      })
    },
  },
}
</script>

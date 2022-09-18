<template>
  <div>
    <client-only>
      <mavon-editor
        v-model="text"
        placeholder="write here..."
        language="ja"
        @change="changeHtml"
      />
    </client-only>
  </div>
</template>

<script>
export default {
  name: 'PostComponent',
  data() {
    return {
      text: '',
      htmlText: '',
    }
  },
  methods: {
    changeHtml(value, reder) {
      this.htmlText = reder
      this.$emit('catch', this.text)
    },
  },
}
</script>

<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">nuxt-generate-test</h1>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Logo from '../../components/Logo.vue'

const URL = 'https://example.com/'

export default Vue.extend({
  components: {
    Logo,
  },
  asyncData({ payload }) {
    return {
      number: payload,
    }
  },
  data() {
    return {
      number: '',
    }
  },
  head(this: { number: string }) {
    return {
      title: this.number,
      meta: [
        {
          hid: 'og:title',
          property: 'og:title',
          content: this.number,
        },
        {
          hid: 'og:url',
          property: 'og:url',
          content: `${URL}share/${this.number}`,
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content: `${URL}share/${this.number}/ogp_allclear.jpg`,
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: `content No.${this.number}`,
        },
      ],
    }
  },
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

<template>
  <div id="app">
    <h3>Word Translator</h3>
    <h5>Powered By Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
  </div>
</template>

<script>

import TranslateForm from './components/translateForm'

export default {
  name: 'App',
  components: {
    'TranslateForm':TranslateForm
  },
  methods: {
    translateText: function (text) {
      this.$htto.get('yandex url');
    }
  }
}
</script>

<style>

</style>

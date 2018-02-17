<template>
  <div id="app" class="text-center">
    <h2 class="pt-5">Word Translator</h2>
    <h6>Powered By Vue.js</h6>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/translateForm'
import TranslateOutput from './components/translateOutput'

export default {
  name: 'App',
  components: {
    'TranslateForm':TranslateForm,
    'TranslateOutput':TranslateOutput
  },
  data () {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText: function (text, language) { // Listening to the event and getting the data
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180217T190755Z.f403b2fca14a879e.b14ad8a7f96066848e91fb1615d4373cfe4f7f5d&lang='+language+'&text='+text)
      .then( response => {
        this.translatedText = response.body.text[0];
      })
    }
  }
}
</script>

<style>

  body {
    background: #fefefe;
    height: 100vh;
  }

</style>

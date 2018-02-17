<template>
  <div class="mt-5" id="translateForm">
      <div class="col-md-6 offset-md-3 card card-body bg-light">
        <form class="form-inline" v-on:submit="formSubmit">
            <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word to translate">
            <!-- Using a for based on languages available and binding the object value to the <option> value -->
            <select class="form-control" v-model="language">
                <option v-bind:value="language.code" v-for="(language, index) in languageCode"  v-bind:key="index"> {{ language.language }} </option>
            </select>
            <input class="btn btn-primary ml-xl-3" type="submit" value="Translate">
        </form>
      </div>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data () {
      return {
          textToTranslate: '',
          language: '',
          languageCode: [
              {code:'ru', language: 'Russian'},
              {code:'es', language: 'Espanish'},
              {code:'fr', language: 'French'},
              {code:'pt', language: 'Portuguese'},
              {code:'it', language: 'Italian'},
              {code:'zh', language: 'Chinese'}
              // insert another language here
          ]
      }
  },
  created () {
      this.language = 'pt';
      this.languageCode.sort(this.compareObj); // Sorting the select box languages in alphabetic
  },
  methods: {
      formSubmit(e) {
          e.preventDefault();
          this.$emit('formSubmit', this.textToTranslate, this.language) // Emitting a event to the main App.vue
      },
      compareObj(a, b) { // Creating the compare function
          if (a.language < b.language) {
              return -1;
          } else if (a.language > b.language) {
              return  1;
          } else {
              return 0;
          }
      }
  }
}
</script>

<style scoped>

    .col-md-6 {
        border-radius: 3px;
    }

</style>

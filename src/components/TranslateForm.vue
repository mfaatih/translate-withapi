<template>
  <form @submit.prevent="translateIt" class="well">
    <b-form-textarea
      v-model="translateText"
      cols="50"
      rows="5"
      placeholder="Çevirmek için yaz"
    ></b-form-textarea>
    <strong>Çeviri yapacağınız dili seçiniz!</strong>
    <select v-model="translateTo" class="form-control">
      <option
        :key="alpha2Code"
        v-for="{alpha2Code, name} in languages"
        :value="alpha2Code"
        >{{ name }}</option
      >
    </select>
    <br />
    <div class="text-left">
      <strong>Tahmin edilen dil: {{ detectedLanguage }} </strong>
    </div>
    <br />
    <b-button variant="outline-primary" type="submit">Çevir !</b-button>
  </form>
</template>

<script>
import {setCORS} from 'google-translate-api-browser';
import axios from 'axios';
export default {
  data() {
    return {
      detectedLanguage: '',
      translated: '',
      translateText: '',
      translateTo: '',
      languages: {},
    };
  },
  methods: {
    translateIt() {
      const translate = setCORS('http://cors-anywhere.herokuapp.com/');
      translate(this.translateText, {to: this.translateTo})
        .then(response => {
          this.translated = response.text;
          this.detectedLanguage = response.from.lanuage.didYouMean;
        })
        .catch(e => (this.translated = e));
      this.$emit('translateText', this.translated);
    },
  },
  created() {
    axios
      .get('https://restcountries.eu/rest/v2/all')
      .then(response => {
        this.languages = response.data;
      })
      .catch(e => console.log(e));
  },
};
</script>

<style>
</style>

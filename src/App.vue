<template>
  <div id="container">
    <h1 class="text-center">Vue-Translater</h1>
    <h1 class="text-center">Vue js ile Translater</h1>
    <br />
    <div class="row">
      <div class="col-md-12 text-center">
        <TranslateForm @translateText="translateText = $event" />
        <h3 class="text-success text-center"></h3>
        <SearchHistory :translateText="translateText" />
      </div>
    </div>
  </div>
</template>

<script>
import SearchHistory from './components/SearchHistory';
import TranslateForm from './components/TranslateForm';
export default {
  name: 'App',
  components: {
    SearchHistory,
    TranslateForm,
  },
  data() {
    return {
      translateText: '',
    };
  },
};
</script>

<style>
</style>

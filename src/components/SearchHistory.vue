<template>
  <div class="well">
    <h3>Çeviri Sonucu</h3>
    <ul class="list-group text-left">
      <li class="list-group-item">
        <div>
          <strong>{{ translateText }} </strong>
        </div>
        <br />
        <div>
          <strong class="text-success"></strong>
          <span class="text-info"></span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['translateText'],
};
</script>

<style></style>

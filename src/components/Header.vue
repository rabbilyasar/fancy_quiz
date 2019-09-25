<template>
  <div id="header">
    <div class="bg-light">
      <b-nav>
        <b-nav-item disabled>Fancy Quiz App</b-nav-item>
        <b-nav-item disabled> Counter: {{numCorrect}}/{{numTotal}}</b-nav-item>
      </b-nav>
    </div>
  </div>
</template>

<script>
export default {
  props: [
    'numCorrect',
    'numTotal'
  ]

  // mounted: {

  // }
};
</script>

<style>
</style>
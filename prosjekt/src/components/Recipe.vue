<template>
  <div class="recipe">
    <h1>{{ title }}</h1>
    <a :href="url">{{ url }}</a>
    <li v-bind:key="ingredient" v-for="ingredient in ingredients">
      {{ ingredient }}
    </li>
    <br />
    <li v-bind:key="step" v-for="step in steps">
      {{ step }}
    </li>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  name: 'Recipe',
  props: {
    title: String,
    time: String,
    steps: [],
    ingredients: [],
    url: String,
  },
}
</script>

<style></style>

<template>
  <div class="recipe">
    <h1>{{ title }}</h1>
    <h2>{{ time }}</h2>
    <li v-bind:key="step" v-for="step in steps">
      {{ step }}
    </li>
    <br />
    <li v-bind:key="ingredient" v-for="ingredient in ingredients">
      {{ ingredient }}
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
  },
}
</script>

<style></style>

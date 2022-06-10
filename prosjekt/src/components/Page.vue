<template>
  <div>
    <h1>Press to get a random recipe</h1>
    <GetRecipeButton v-on:clicked="updateTitle($event)" />
    <Recipe
      :title="title"
      :time="time"
      :steps="steps"
      :ingredients="ingredients"
    />
  </div>
</template>

<script>
/* eslint-disable */
import GetRecipeButton from './GetRecipeButton.vue'
import Recipe from './Recipe.vue'
export default {
  name: 'Page',
  components: {
    GetRecipeButton,
    Recipe,
  },
  data() {
    return {
      title: '',
      time: '',
      steps: Array,
      ingredients: Array,
    }
  },
  methods: {
    updateTitle(object) {
      this.title = object.title
      this.time = object.time
      this.steps = object.steps
      this.ingredients = object.ingredients
    },
  },
}
</script>

<style></style>

<template>
  <button v-on:click="getRandom()">Get recipe</button>
</template>

<script>
import axios from 'axios'
/* eslint-disable */
export default {
  name: 'GetRecipeButton',
  methods: {
    stringify(path) {
      return JSON.stringify(path)
    },
    getRandom() {
      axios
        .get(
          'https://api.spoonacular.com/recipes/random?number=1&apiKey=886ff9b5d19b45e386d783d51618d5ce'
        )
        .then((res) => {
          let ingredients = []
          let instructions = []
          res.data.recipes[0].extendedIngredients.forEach((ingredient) => {
            ingredients.push(
              (
                this.stringify(ingredient.name) +
                ': ' +
                this.stringify(ingredient.measures.metric.amount) +
                ' ' +
                this.stringify(ingredient.measures.metric.unitLong)
              ).replaceAll('"', '')
            )
          })
          res.data.recipes[0].analyzedInstructions[0].steps.forEach(
            (element) => {
              instructions.push(
                this.stringify(element.step).replaceAll('"', '')
              )
            }
          )
          console.log(instructions)
          this.$emit('clicked', {
            title: this.stringify(res.data.recipes[0].title),
            ingredients: ingredients,
            steps: instructions,
            url: this.stringify(res.data.recipes[0].spoonacularSourceUrl),
          })
        })
    },
    testClick(event) {
      this.$emit('clicked', {
        title: 'Bakt Potet',
        time: '45 min',
        steps: [
          'ta poteten i folie',
          'Putt den i ovnen til den er bakt',
          'Klæsh på rømme',
          'Bon apeklitt',
        ],
        ingredients: ['Potet', 'røme'],
      })
    },
  },
}
</script>

<style></style>

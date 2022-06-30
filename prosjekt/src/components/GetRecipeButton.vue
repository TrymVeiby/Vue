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
          console.log(res.data.recipes[0].image)
          this.$emit('clicked', {
            title: this.stringify(res.data.recipes[0].title),
            image: this.stringify(res.data.recipes[0].image),
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

<style>
/* CSS */
button {
  background-color: #c2fbd7;
  border-radius: 100px;
  box-shadow: rgba(44, 187, 99, 0.2) 0 -25px 18px -14px inset,
    rgba(44, 187, 99, 0.15) 0 1px 2px, rgba(44, 187, 99, 0.15) 0 2px 4px,
    rgba(44, 187, 99, 0.15) 0 4px 8px, rgba(44, 187, 99, 0.15) 0 8px 16px,
    rgba(44, 187, 99, 0.15) 0 16px 32px;
  color: green;
  cursor: pointer;
  display: inline-block;
  font-family: CerebriSans-Regular, -apple-system, system-ui, Roboto, sans-serif;
  padding: 7px 20px;
  text-align: center;
  text-decoration: none;
  transition: all 250ms;
  border: 0;
  font-size: 16px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.button-33:hover {
  box-shadow: rgba(44, 187, 99, 0.35) 0 -25px 18px -14px inset,
    rgba(44, 187, 99, 0.25) 0 1px 2px, rgba(44, 187, 99, 0.25) 0 2px 4px,
    rgba(44, 187, 99, 0.25) 0 4px 8px, rgba(44, 187, 99, 0.25) 0 8px 16px,
    rgba(44, 187, 99, 0.25) 0 16px 32px;
  transform: scale(1.05) rotate(-1deg);
}
</style>

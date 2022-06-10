<template>
  <button v-on:click="testClick()">Get recipe</button>
</template>

<script>
import axios from 'axios'
/* eslint-disable */
export default {
  name: 'GetRecipeButton',
  methods: {
    getRandom() {
      axios
        .get(
          'https://api.spoonacular.com/recipes/random?number=1&apiKey=886ff9b5d19b45e386d783d51618d5ce'
        )
        .then((res) => {
          console.log(res.data)
          // parsedData = JSON.parse(res.data)
          // this.$emit('clicked', parsedData.
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

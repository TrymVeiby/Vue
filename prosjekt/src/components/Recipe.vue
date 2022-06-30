<template>
  <div class="recipe">
    <h1>{{ title }}</h1>
    <img :src="image" />
    <a :href="url">{{ url }}</a>
    <div class="lists">
      <li v-bind:key="ingredient" v-for="ingredient in ingredients">
        {{ ingredient }}
      </li>
      <br />
      <div class="steps">
        <h1>Steps</h1>
        <li v-bind:key="step" v-for="step in steps">
          {{ step }}
        </li>
      </div>
    </div>
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
    image: String,
  },
}
</script>

<style>
.recipe {
  margin-top: 200px;
}
li {
  text-align: left;
  font-size: 30px;
  margin-top: 20px;
  color: rgb(255, 255, 255);
  text-shadow: -1px -1px 0 #000, 1px -1px 0 #000, -1px 1px 0 #000,
    1px 1px 0 #000;
}

.lists {
  margin-left: 35%;
  margin-right: 35%;
}

.steps {
  margin-top: 50px;
}
@media only screen and (max-width: 600px) {
  .lists {
    margin-left: 5%;
    margin-right: 5%;
  }
}
</style>

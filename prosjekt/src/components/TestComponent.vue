<template>
  <h1>HELLO{{ msg }}</h1>
</template>

<script>
export default {
  name: 'TestComponent',
  props: {
    msg: String,
  },
}
</script>

<style></style>

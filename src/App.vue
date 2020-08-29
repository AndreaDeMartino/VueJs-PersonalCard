<template>
  <div class="cards">
    <my-card></my-card>
  </div>
</template>

<script>
import Card from './components/Card.vue'

export default {
  name: 'app',
  components: {
    'my-card' : Card,
  }
}
</script>

<style>

/****************************************************
* General Settings
****************************************************/

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.cards {
  height: 100vh;
  font-family: 'Roboto', sans-serif;
  font-weight: 400;
  background: radial-gradient(circle, rgb(167 167 167) 43%, rgb(16 16 16) 88%);
}

</style>

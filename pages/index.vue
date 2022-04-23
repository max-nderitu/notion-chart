<template>
  <Doughnut css-classes="dark-mode" />
</template>

<script>
import Doughnut from '../components/Doughnut'

export default {
  name: 'index',
  components: { Doughnut }
}
</script>

<style>
body, html {
  width: 100%;
  height: 100%;
  background-color: #191919;
}
</style>

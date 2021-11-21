<template>
  <div class="mid">
    <Dymamic/>
  </div>
</template>

<script>
import Dymamic from './components/dynamic.vue'

export default {
  name: 'App',
  components: {
    Dymamic
  }
}
</script>

<style>
  .mid{
    display: flex;
    justify-content: center;
  }
</style>

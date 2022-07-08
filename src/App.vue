<template>
  <div id="app">
    <header>
      <HeaderSpotify />
    </header>
  </div>
</template>

<script>
import HeaderSpotify from './components/HeaderSpotify.vue'

export default {
  name: 'App',
  components: {
    HeaderSpotify
  }
}
</script>

<style lang="scss">
@import '@/style/common.scss';
@import '@/style/variables.scss'

</style>

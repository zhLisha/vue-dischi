<template>
  <div id="app">
    <!-- Header -->
    <header>
      <HeaderSpotify />
    </header>

    <!-- Content -->
    <main>
      <CardList />
    </main>
    
  </div>
</template>

<script>
import HeaderSpotify from './components/HeaderSpotify.vue'
import CardList from './components/CardList.vue'

export default {
  name: 'App',
  components: {
    HeaderSpotify,
    CardList
  }
}
</script>

<style lang="scss">
@import '@/style/common.scss';
@import '@/style/variables.scss'

</style>

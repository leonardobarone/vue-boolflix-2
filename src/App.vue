<template>
  <div>
    <Header @searching="searchFilm" />
    <Main :query="query" />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Footer from './components/Footer.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Footer
  },
  data() {
    return {
      query: ''
    }
  },
  methods: {
    searchFilm(query) {  
        this.query = query;
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/common.scss';

</style> 

<template>
  <div id="app">
    <Header @Search="search" />
    <Main />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data() {
    return {
      research: '',
    }
  },
  methods: {
    search(name) {
      this.research = name;
    },

  },
}
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
@import './styles/general.scss';

</style>

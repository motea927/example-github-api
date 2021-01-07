<template>
  <app-header @setReposSize="setReposSize"/>
  <app-repo :reposSize="reposSize"/>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppRepo from './components/AppRepo'

export default {
  name: 'App',
  components: { AppHeader, AppRepo },
  methods: {
    setReposSize (reposSize) {
      this.reposSize = reposSize
    }
  },
  data () {
    return {
      reposSize: 0 
    }
  }
}
</script>

<style lang="scss">
body {
  background-color: #FAFAFA;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>

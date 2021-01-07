<template>
  <app-header />
  <div class="repo">
    <h2>-practice-project-note-application</h2>
    <p class="repo__desc">以實作筆記本程式入門並學習node.js基礎</p>
    <p>
      <img src="./assets/img/repo/url.svg" alt="" class="repo__urlImg">
      https://gith-ub.com/motea927/-practice-project-note-application
    </p>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'

export default {
  name: 'App',
  components: { AppHeader }
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

.repo {
  border: 1px solid #eee;
  margin-top: 30px;
  background-color: white;
  padding: 20px;
  width: 980px;
  &__urlImg {
    display: inline;
    width: 20px;
    height: 20px;
  }
  &__desc {
    font-size: 16px;
    line-height: 16px;
  }
}
</style>

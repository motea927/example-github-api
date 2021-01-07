<template>
  <div class="header">
    <div class="info">
      <h1>
        motea927's github
      </h1>
      <!-- https://api.github.com/users/motea927 -->
      <!-- /users/{username}/repos -->
      <p class="info__text">
        <img src="./assets/img/header/follower.svg" alt="followers" class="info__icon">
        Followers: 2, Following: 1
      </p>
      <p>
        <img src="./assets/img/header/stars.svg" alt="followers" class="info__icon">
        Stars: 12
      </p>
      <p>
        <img src="./assets/img/header/location.svg" alt="followers" class="info__icon">
        Location: Taiwan.Taipei
      </p>
      <p>
        <img src="./assets/img/header/time.svg" alt="followers" class="info__icon">
        created_at: 2017-02-22
      </p>

    </div>
    <img src="./assets/img/header/avatar.jpeg" alt="avatar" class="header__avatar">
  </div>
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
export default {
  name: 'App'
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
.header {
  border: 1px solid #eee;
  width: 980px;
  background-color: white;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  &__avatar {
    width: 150px;
    height: 150px;
    margin-top: 36px;
    border-radius: 5px;
  }
  & .info {
    &__icon {
      width: 20px;
      height: 20px;
    }
    &__text {
      line-height: 20px;
    }
  }
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

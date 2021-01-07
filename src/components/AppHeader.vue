<template>
  <div class="header">
    <div class="info">
      <h1>
        motea927's GitHub
      </h1>
      <div class="githubInfo" v-for="(info, index) in infoText" :key="index">
        <img :src="require(`../assets/img/header/${info}.svg`)" alt="info" class="githubInfo__img">
        <p class="githubInfo__text">{{ info }}: {{ infoData[info] }}</p>
      </div>
    </div>
    <img src="../assets/img/header/avatar.jpeg" alt="avatar" class="info__avatar">
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      infoText: ['followers', 'repos', 'location', 'created'],
      infoData: {
        followers: 0,
        repos: 0,
        location: '',
        created: ''
      }
    }
  },
  async created () {
    try {
      const response = await axios.get('https://api.github.com/users/motea927')
      this.infoData.followers = response.data.followers
      this.infoData.repos = response.data.public_repos
      this.infoData.location = response.data.location
      this.infoData.created = response.data.created_at.substring(0, 10)
      this.$emit('setReposSize', this.infoData.repos)
    } catch (err) {
      console.log(err)
    }
  }
}
</script>

<style lang="scss">
  .header {
    border: 1px solid #eee;
    width: 980px;
    background-color: white;
    padding: 20px;
    display: flex;
    justify-content: space-between;
  }
  .info {
    &__avatar {
      width: 150px;
      height: 150px;
      margin-top: 36px;
      border-radius: 5px;
    }
    & .githubInfo {
      display: flex;
      align-items: flex-end;
      margin-bottom: 20px;
      &__img {
        width: 20px;
        height: 20px;
        margin-right: 10px;
      }
      &__text {
        margin: 0;
        text-transform: capitalize;
      }
    }
  }
  @media (min-width: 768px) and (max-width: 990px){
    .header {
      width: 700px;
    }
  }
  @media (max-width: 768px){
    .header {
      width: 300px;
      flex-direction: column;
    }
    .info {
      &__avatar {
        order: -1;
        align-self: center;
      }
    }
  }
</style>
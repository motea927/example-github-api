<template>
  <div
    class="repo"
    v-for="(repoInfoList, index) in repoInfoLists"
    :key="index"
    :class="{ 'repo--last': index === repoInfoLists.length - 1 }"
  >
    <h2>{{ repoInfoList.name }}</h2>
    <p class="repo__desc">{{ repoInfoList.description }}</p>
    <div class="repo__url">
      <img src="../assets/img/repo/url.svg" alt="url">
      <a :href="repoInfoList.html_url">{{ repoInfoList.html_url }}</a>
    </div>
    <p>Created: {{ repoInfoList.created_at.substring(0, 10) }} </p>
  </div>
  <app-loading v-if="isLoading"/>
</template>

<script>
import axios from 'axios'
import AppLoading from './AppLoading.vue'

export default {
  components: { AppLoading },
  props: ['reposSize'],
  methods: {
    async getRepoInfo () {
      this.requestPages++
      this.isLoading = true
      const params = {
        per_page: 3,
        page: this.requestPages,
        sort: 'created'
      }
      try {
        const response = await axios.get(this.apiURL, { params })
        this.isLoading = false
        return response
      } catch (err) {
        console.log(err)
      }
    },
    async onScroll (e) {
      if ((this.isNoMore && !this.isInit ) || this.isLoading) return
      const { scrollTop } = e.srcElement.scrollingElement
      const { innerHeight } = window
      const { offsetHeight } = document.documentElement
      const isDown = (scrollTop + innerHeight + 1) > offsetHeight
      if (isDown) {
        const response = await this.getRepoInfo()
        this.repoInfoLists.push(...response.data)
      }
    }
  },
  data () {
    return {
      apiURL: 'https://api.github.com/users/motea927/repos',
      repoInfoLists: [],
      requestPages: 0,
      isLoading: false
    }
  },
  computed: {
    isNoMore () {
      const requestCount = this.requestPages * 3
      return requestCount > this.reposSize
    },
    isInit () {
      return this.reposSize === 0
    }
  },
  async created () {
    const response = await this.getRepoInfo()
    this.repoInfoLists.push(...response.data)
  },
  mounted () {
    document.addEventListener('scroll', this.onScroll)
  }
}
</script>

<style lang="scss">
  .repo {
    border: 1px solid #eee;
    margin-top: 30px;
    background-color: white;
    padding: 20px;
    width: 980px;
    &__url {
      display: flex;
      align-items: flex-end;
      & img {
        width: 20px;
        height: 20px;
        margin-right: 10px;
      }
      & a {
        opacity: .9;
        &:hover {
          opacity: 1;
        }
      }
    }
    &--last {
      margin-bottom: 60px;
    }
  }
  @media (min-width: 768px) and (max-width: 990px){
    .repo {
      width: 700px;
    }
  }
  @media (max-width: 768px){
    .repo {
      width: 300px;
      &__url a {
        word-break: break-all;
      }
    }
  }
</style>
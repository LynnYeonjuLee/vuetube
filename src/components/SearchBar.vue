<template>
  <div>
    <input class="searchBar" type="text" @keypress.enter="fetchVideos">
  </div>
</template>

<script>
import axios from 'axios'
// 모든 요청은 API 키(key 매개변수 포함)를 지정하거나 OAuth 2.0 토큰을 제공해야 합니다. 
// API 키는 APIs Console에서 프로젝트의 API Access 창에 있습니다.
const BASE_URL = 'https://www.googleapis.com/youtube/v3/search'
const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY

export default {
  name: 'SearchBar',
  data() {
    return {
      useInput: '',
    }
  },
  methods: {
    fetchVideos(e) {
      this.userInput = e.target.value
      const config = {
        params: {
          part: 'snippet',
          key: API_KEY,
          q: this.userInput,
        },
        // headers: 
      }
      axios.get(BASE_URL, config)
      .then(res => {
        console.log(res)
        this.$emit('selected-videos', res.data.items)
      })
      .catch(err => {
        console.log(err)
      })
    },
  },
}
</script>

<style scoped>
.searchBar {
  width: 100%;
  padding: 0.6rem;
  font-size: 1.25rem;
}
</style>
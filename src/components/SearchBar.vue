<template>
  <div class="search-bar">
    <input type="text" @keyup.enter="onKeywordEnter">
  </div>
</template>

<script>
import axios from 'axios'
// 전역 변수로 만들기
const YOUTUBE_API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY
const YOUTUBE_API_URL = 'https://www.googleapis.com/youtube/v3/search'

export default {
  name: 'SearchBar',
  methods: {
    async onKeywordEnter(event) {
      const keyword = event.target.value
      const config = {
        params: {
          part: 'snippet',
          type: 'video',
          q: keyword, // 검색어
          key: YOUTUBE_API_KEY,
      // YOUTUBE_API_URL + `?key = ${YOUTUBE_API_KEY}`
        },
      }

      const response = await axios.get(YOUTUBE_API_URL, config)
      const videoList = response.data.items
      this.$emit('on-keyword-enter', videoList)
      // console.log(response)
      // axios.get(YOUTUBE_API_URL, config)
      // .then()
      // .catch()
    },
  },
}
</script>

<style>
.search-bar > input {
  width: 100%;
  padding: 0.5rem;
  font-size: 2rem;
}
</style>
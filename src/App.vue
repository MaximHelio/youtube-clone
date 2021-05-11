<template>
  <div id="app">
    <h1>Youtube Clone App</h1>
    <header>
    <SearchBar
      @on-keyword-enter="onKeywordEnter"
    />
    </header>
    <section>
    <VideoListItemDetail
      :video="video"
    />
    <VideoList 
      :videoList="videoList"
      @on-select-video="onSelectVideo" 
    />
    </section>
  </div>
</template>

<script>
import SearchBar from '@/components/SearchBar'
import VideoList from '@/components/VideoList'
import VideoListItemDetail from '@/components/VideoListItemDetail'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoListItemDetail,
  },
  data() {
    return {
      videoList: [],
      video: null, //null, // 의도적으로 빈 값을 줄 때
    }
  },
  methods: {
    onKeywordEnter(videoList) {
      this.videoList = videoList
      console.log(videoList)
    },
    onSelectVideo(video) {
      this.video = video
    },
  },
}
</script>

<style>
section, header {
  width: 80%;
  /* 가운데 정렬 */
  margin: 0 auto;
  padding: 1rem 0; 
}

section {
  display: flex;
}
</style>

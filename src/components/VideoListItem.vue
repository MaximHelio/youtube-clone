<template>
  <div @click="onSelectVideo" class="video-list-item">
    <!-- 보간법  --> <!-- 디렉티브 -->
    <img :src="thumbUrl" alt="">
    <h3>{{ videoTitle | unescape }}</h3>
    <p>{{ videoDesc }}</p>
  </div>
</template>

<script>
import _ from 'lodash'


export default {
  name: 'VideoListItem',
  props: {
    video: Object,
  },
  computed: {
    videoTitle() {
      return this.video.snippet.title
    },
    videoDesc() {
      return this.video.snippet.description 
    },
    thumbUrl() {
      return this.video.snippet.thumbnails.medium.url
    },
  },
  filters: {
    unescape(rawText) {
      return _.unescape(rawText)
    },
  },
  methods: {
    onSelectVideo() {
      return this.$emit('on-select-video', this.video)
    },
  },
}
</script>

<style>
.video-list-item:hover {
  cursor: pointer;
  background-color: whitesmoke;
}
</style>
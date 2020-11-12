<template>
  <div class="videoDetail">
    <VideoListItem
      v-for="video in videoList" 
      :key="video.etag"
      :video="video"
      class="videoListItem"
      @select-video="selectVideo"
    />
    <!-- <div 
      v-for="video in videoList" 
      :key="video.etag"
      class="videoListItem"
    >
      <img width=360 :src="thumbnailUrl(video)" alt="img"> -->
      <!-- <div>
        <div class="videoListItem__title">{{ video.snippet.title | unescape }}</div>
        <div class="videoListItem__channelTitle">{{ video.snippet.channelTitle}}</div>
        <div class="videoListItem__description">{{ video.snippet.description}}</div>
      </div> -->
      
    <!-- </div> -->
  </div>
</template>

<script>
import VideoListItem from '@/components/VideoListItem'
// import _ from 'lodash'
export default {
  name: 'VideoList',
  components: {
    VideoListItem
  },
  props: {
    videoList: Array,
  },
  methods: {
    selectVideo(video) {
      this.$emit('select-video',video)
      console.log('selectedVideo from VideoList')
    },
  },
  // methods: {
  //   thumbnailUrl(video) {
  //     return video.snippet.thumbnails.high.url
  //   },
  // },
  // filters: {
  //   unescape(value) {
  //     return _.unescape(value)
  //   },
  // },
}
</script>

<style scoped>
  /* .videoListItem {
    display: flex;

  }
  .videoListItem__title {
    font-size: 1.25rem;
    font-weight: bold;
  } */
  .videoDetail {
    width: 30%;
  }
</style>

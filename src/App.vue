<template>
  <div id="app">
    <header>
      <SearchBar @selected-videos="selectedVideos"/></header>
    <section>
      <VideoListItemDetail v-if=" isVideoSelected" :video="selectedVideo"/>
      <VideoList :videoList="videoList" @select-video="selectVideo"/>
      <!-- <VideoListItem/> -->
    </section>
    
    
  </div>
</template>

<script>
// https://vuejs.org/v2/style-guide/#Component-instance-options-order-recommended
import SearchBar from '@/components/SearchBar'
import VideoList from '@/components/VideoList'
// import VideoListItem from '@/components/VideoListItem'
import VideoListItemDetail from '@/components/VideoListItemDetail'
export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    // VideoListItem,
    VideoListItemDetail,
  },
  data() {
    return {
      videoList: [],
      selectedVideo: {},
      isVideoSelected: false,
    }
  },
  methods: {
    selectedVideos(videoList) {
      // console.log(videoList)
      this.videoList = videoList
    },
    selectVideo(video) {
      this.selectedVideo = video
      this. isVideoSelected = true
      console.log(video)
      console.log('selectedVideo 호출 !')
    },
  },
}
</script>

<style>
header, section {
  width: 80%;
  margin: 0 auto;
  padding: 1rem 0;
}
section {
  display: flex;
}
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>

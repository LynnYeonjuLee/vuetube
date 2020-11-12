<template>
  <div v-if="video" @click="onSelectVideo" class="videoListItem">
    <img :src="thumbnailUrl(video)" alt="img">
    <div>
        <div class="videoListItem__title">{{ video.snippet.title | unescape }}</div>
        <div class="videoListItem__channelTitle">{{ video.snippet.channelTitle}}</div>
        <div class="videoListItem__description">{{ video.snippet.description}}</div>
      </div>
  </div>
</template>

<script>
import _ from 'lodash'
export default {
  name: 'VideoListItem',
  props: {
    video: Object,
  },
  methods: {
    thumbnailUrl(video) {
      return video.snippet.thumbnails.high.url
    },
    onSelectVideo() {
      this.$emit('select-video', this.video)
    },
  },
  filters: {
    unescape(value) {
      return _.unescape(value)
    },
  },
}
</script>

<style scoped>
/*scoped */
  .videoListItem {
    /* display: flex; */

  }
  .videoListItem__title {
    font-size: 1.25rem;
    font-weight: bold;
  }
  .videoListItem >img {
    width: 100%;
  }
</style>
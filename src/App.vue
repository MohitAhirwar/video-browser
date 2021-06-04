<template>
<!-- Only one root element is allowed -->
<div class="p-3 mb-2 bg-secondary text-white">
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo" />
      <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>
    </div>
    <!-- {{ videos.length }} -->
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = 'PutyourAPIkeyhere:)'; // Generate your API key from https://console.developers.google.com


export default {
  name:'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data(){
    return { videos: [], selectedVideo: null };
  },
  methods: {
    onVideoSelect(video) {
      // console.log(video);
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      // console.log(searchTerm);
      axios.get('https://www.googleapis.com/youtube/v3/search',{
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => {
        this.videos = response.data.items;
      });
    }
  }  
}
</script>

<style scoped>
div {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>
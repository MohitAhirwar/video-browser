<template>

  <li class="d-flex position-relative" @click="onVideoSelect">
    
    <img class="mr-3" :src="thumbnailUrl" />
      <div class="container">
     <h6 class="text-white text-wrap">{{ video.snippet.title }}</h6> 
    </div>

  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: ['video'],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
       this.$emit('videoSelect',this.video);
    }
  }
};
</script >

<style scoped>
  li {
    display: flex;
    cursor: pointer;
  }
  li:hover {
    background-color: darkslategray;
  }
</style>
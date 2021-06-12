<template>
  <div v-if="video" class="col-md-8">
    <div class="ratio ratio-16x9">
      <iframe :src="videoUrl" />
    </div>

    <div class="details">
      <div class="p-3 mb-2 bg-dark text-white">
       {{ video.snippet.title }}
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: ['video'],
  computed: {
    videoUrl() {
      const videoId = this.video.id.videoId;
      return 'https://www.youtube.com/embed/'+ videoId ; 
    }
  }
}
</script>

<style scoped>
  .details {
    margin-top: 10px;
  }
</style>
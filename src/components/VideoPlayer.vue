<template>
  <div id="VideoPlayer">
    <div v-if="video != undefined" :key="video.id.viedoId">
        <!-- <img :src="contents[0].snippet.thumbnails.high.url"/> -->
        <div>
        {{video.snippet.title}}
        </div>
        <div class="embed-responsive embed-responsive-16by9">
          <iframe class="embed-responsive-item" :src="`https://www.youtube.com/embed/${video.id.videoId}`">
          </iframe>
        </div>
    </div>

  </div>
</template>

<script>
export default {
    name: "VideoPlayer",
    props: {
        video: Object
    }
}
</script>

<style>

</style>
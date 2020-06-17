<template>
  <ul class="list-group">
    <li class="list-group-item" v-for="video in videos" :key="video.id.viedoId">
          <VideoItem :video="video" @imageClicked="imageClicked"/>
        <!-- <iframe width="560" height="315" :src="`https://www.youtube.com/embed/${content.id.videoId}`" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
        </iframe> -->
    </li>
  </ul>
</template>

<script>
import VideoItem from './VideoItem';
export default {
    name: "VideoList",
    components: {
      VideoItem
    },
    props: {
        videos: Array
    },
    methods:{
      imageClicked(video){
        this.$emit('imageClicked', video);
      }
    }
}
</script>

<style>

</style>
<template>
  <div>
      <div >{{video.snippet.title}}</div>
      <img :src="video.snippet.thumbnails.high.url" @click="imageClicked"/>
  </div>
</template>

<script>
export default {
    name: "VideoItem",
    props: {
        video:Object
    },
    methods:{
        imageClicked(){
            this.$emit('imageClicked', this.video);
        }
    }
}
</script>

<style>

</style>
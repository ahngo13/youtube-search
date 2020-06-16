<template>
  <div id="VideoList">
    <div v-for="content in contents" :key="content.id.viedoId">
        <img :src="content.snippet.thumbnails.high.url"/>
        <div>
        {{content.snippet.title}}
        </div>
        <!-- <iframe width="560" height="315" :src="`https://www.youtube.com/embed/${content.id.videoId}`" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
        </iframe> -->
    </div>

  </div>
</template>

<script>
export default {
    name: "VideoList",
    props: {
        contents: Array
    }
}
</script>

<style>

</style>
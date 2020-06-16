<template>
  <div id="VideoPlayer">
    <div v-if="contents.length > 0" :key="contents[0].id.viedoId">
        <!-- <img :src="contents[0].snippet.thumbnails.high.url"/> -->
        <div>
        {{contents[0].snippet.title}}
        </div>
        <iframe width="560" height="315" :src="`https://www.youtube.com/embed/${contents[0].id.videoId}`" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
        </iframe>
    </div>

  </div>
</template>

<script>
export default {
    name: "VideoPlayer",
    props: {
        contents: Array
    }
}
</script>

<style>

</style>
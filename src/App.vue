<template>
  <div id="app">
    <div id="container">
      <h1 class="text-center">Youtube Search</h1>
      <SearchBar @onInput="getVideos"/>
      <div class="row">
        <div class="col-9">
          <VideoPlayer :video="selectedVideo"/>
        </div>
        <div class="col-3">
          <VideoList :videos="videos" @imageClicked="imageClicked"/>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import SearchBar from './components/SearchBar.vue';
import VideoList from './components/VideoList.vue';
import VideoPlayer from './components/VideoPlayer.vue';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    SearchBar,
    VideoPlayer,
    VideoList,
  },
  data(){
    return{
      videos:[],
      selectedVideo:null
    }
  },
  methods:{
        getVideos(userInput){

            // 1.입력된 검색어를 가지고,
            const baseURL = 'https://www.googleapis.com/youtube/v3/search'; 
            const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY;
            // 2. Youtube API에 요청을 보내어 
            axios.get(baseURL, {params: {
                key: API_KEY,
                part: "snippet",
                q: userInput,
                type: "video",
                maxResults : "10"
            }})
            // 3. 검색어로 검색한 결과를 가져옴
            .then((result)=>{
                console.log(result.data.items);
                this.videos = result.data.items;
            })
        },
        imageClicked(video){
          this.selectedVideo = video;
          console.log(video);
        }
    }
}
</script>

<style>

</style>

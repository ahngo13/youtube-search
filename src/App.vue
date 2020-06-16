<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <SearchBar @inputEntered="input"/>
    <div id="VideoArea">
      <VideoPlayer :contents="contents"/>
      <VideoList :contents="contents"/>
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
      keyword:"",
      contents:[],
    }
  },
  methods:{
        input(message){

            // 1.입력된 검색어를 가지고,
            const baseURL = 'https://www.googleapis.com/youtube/v3/search'; 
            const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY;
            // 2. Youtube API에 요청을 보내어 
            axios.get(baseURL, {params: {
                key: API_KEY,
                part: "snippet",
                q: message,
                type: "video",
                maxResults : "10"
            }})
            // 3. 검색어로 검색한 결과를 가져옴
            .then((result)=>{
                console.log(result.data.items);
                this.contents = result.data.items;
            })
        },
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#VideoArea{
  width: 100%;
  display: flex;
}
</style>

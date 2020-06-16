<template>
  <div>
      <h1>Youtube Search</h1>
      <input v-model="keyword" @keypress.enter="inputEntered" type="text">
    <!--   <ul>
          <li v-for="content in contents" :key="content.id.viedoId">
              {{content.snippet.title}}
          </li>
      </ul> -->
  </div>
</template>
<script>
export default {
    name: "SearchBar",
    data(){
        return{
            keyword: ""
        }
    },
    methods:{
        inputEntered(){
            // this.$emit('dogButtonClicked') 전파될 변수명
            this.$emit('inputEntered', this.keyword);
        }
    }
}
</script>

<style>

</style>
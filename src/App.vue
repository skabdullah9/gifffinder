<template>
<div class="min-h-screen bg-black bg-opacity-95">
  <Search @giffdata="getGiffList" :tag="userTag" />
    <Tags v-if="giffList.length < 1" @tag-search="tagSearch" />
    <GiffList :giffList="giffList" />
  
  
</div>
</template>

<script>
import {ref} from 'vue'
import Search from './components/Search.vue'
import GiffList from './components/GiffList.vue'
import Tags from './components/Tags.vue'

export default {
  name: 'App',
  components: {
    Search, GiffList, Tags
  },
  setup() {
    const giffList = ref([])
    const userTag = ref(null)
    const tagSearch = (tag) => {
      
      userTag.value = tag
    }
    const getGiffList = (list) => {
      giffList.value = list
    }
   console.log(giffList.value);
    return { giffList, getGiffList, tagSearch, userTag}
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
  overflow-x: hidden;
  background-image: url(https://source.unsplash.com/random);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  /* padding-top: 60px; */
}

</style>

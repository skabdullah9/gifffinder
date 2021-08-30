<template>
  <div class="h-screen absolute w-full flex flex-col items-center justify-center gap-5 text-gray-300 font-mono italic">
      <h1 class="font-bold text-3xl md:text-6xl mb-2 md:mb-10 ">Trending Now</h1>
      <div class="tags flex flex-wrap justify-center items-center max-w-prose px-1 md:px-0 gap-2 md:gap-4">
        <div @click="tagSearch(tag)" class="rounded-2xl py-px px-0.5 cursor-pointer transform hover:-translate-y-1 transition-transform bg-gradient-to-r from-yellow-400 via-red-500 to-pink-500 text-xs md:text-sm font-semibold" v-for="tag in tags" :key="tag">
            <span class="bg-black  px-3 block py-1  rounded-2xl">#{{tag}}</span>
        </div>
      </div>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
    setup(props, {emit}) {
        const tags = ref(['thor','mr bean','dwayne johnson', 'michael jackson','happy birthday','dog','love','animal','weekend','minions','cat','thank you','friends','kid','hugs','reaction','christmas','kisses','sleep','pokemon','jim carrey','akshay kumar'])
        
        const tagSearch = (tag) => {
            
            emit('tag-search',tag)
        }
        return {tags, tagSearch, }
    }
}
</script>

<style>

</style>
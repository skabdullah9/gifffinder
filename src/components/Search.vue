<template>
  <div
    class="fixed left-1/2 transform -translate-x-1/2  z-10 w-full bg-gradient-to-r from-yellow-400 via-red-500 to-pink-500 pb-1"
  >
    <div class="bg-overlay bg-black py-3">
      <div
        class="flex w-full container mx-auto justify-center md:justify-between items-center flex-wrap gap-2"
      >
        <h1
          class="text-2xl font-mono text-gray-300 mr-5 bg-gradient-to-r from-yellow-400 via-red-500 to-pink-500 bg-clip-text text-opacity-0 tracking-wider font-bold"
        >
         <a href="/">🖼️ [Gifffinder]</a> 
        </h1>
        <div class="relative">
          <input
            type="text"
            placeholder="Search Giff's here"
            v-model="keyword"
            @input="onInput"
            class="text-2xl py-2 pl-6 font-mono rounded-lg  focus:outline-none bg-gray-900 bg-opacity-60 text-gray-200 text-center max-w-full"
          />
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-6 w-6 absolute top-3 left-2"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
            />
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, watchEffect } from "vue";
import api from "../env.js";


export default {
  name: "Search",
  props: { tag : String},
  setup(props, context) {
    const keyword = ref();
    
    let timeout = null;
    const onInput = () => {
      clearTimeout(timeout);
      timeout = setTimeout(() => {
        fetchResults(keyword.value);
      }, 500);
    };
    const fetchResults = async (input) => {
      const response = await fetch(api + input);
      const data = await response.json();
      
      context.emit("giffdata", data.data);
      
    };
    watchEffect(() => { 
      if(props.tag) {
        fetchResults(props.tag)
      }
    })
    
    
    return { keyword, onInput, };
  },
};
</script>

<style></style>

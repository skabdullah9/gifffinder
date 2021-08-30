<template>
  <div class="flex flex-wrap justify-center items-stretch pt-36 pb-10 md:pt-28 gap-3">
    <Giff v-for="giff in filteredGiffs" :key="giff.id" :giff="giff" />
  </div>
</template>

<script>

import Giff from './Giff.vue'
import {watchEffect, ref} from 'vue'
export default {
  components: {
    Giff
  },
  props: {
    giffList: Array
  },
  setup(props) {
    const filteredGiffs = ref([])
    watchEffect(() => {
      let list = props.giffList.slice()
      filteredGiffs.value = list.sort((a, b) => a.images.original.height - b.images.original.height)
    })
    
    
    return {filteredGiffs}
  }
}
</script>

<style>

</style>
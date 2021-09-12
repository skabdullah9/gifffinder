<template>
  <img
    loading="lazy"
    @load="isLoading = false"
    :src="giff.images.original.url"
    class="object-cover transform transition-transform hover:scale-125 object-center rounded-lg md:max-h-72 cursor-pointer w-40 md:w-auto md:max-w-72"
    alt=""
  />
  <img v-if="isLoading" src="@/assets/loader.gif" alt="" />
</template>

<script>
export default {
  props: {
    giff: Object,
  },
  data() {
    return {
      isLoading: true,
    };
  },
};
</script>

<style></style>

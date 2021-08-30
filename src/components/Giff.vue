<template>

        <img  :src="giff.images.original.url" class="object-cover transform transition-transform hover:scale-125 object-center rounded-lg md:max-h-72 cursor-pointer w-40 md:w-auto md:max-w-72"  alt="">
        
</template>

<script>
export default {
    props: {
        giff: Object
    }
}
</script>

<style>

</style>
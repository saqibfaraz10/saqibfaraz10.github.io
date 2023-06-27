<template>
    <div>
        <a :href= "href" target="_blank" 
          class="px-3 py-2 rounded border-2 bg-lime-500 text-white border-lime-500
          hover:bg-white hover:text-black transition-colors">
            Youtube
          </a>
    </div>
</template>

<script setup>
const props = defineProps({
    href: String
})
</script>
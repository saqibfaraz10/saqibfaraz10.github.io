<template >
     <div class="flex justify-center mt-2 gap-2">
        <router-link 
            :to="{name: 'byLetter' , params: {letter}}" 
            v-for="letter in letters" 
            :key="letter"
            class="hover:text-lime-500 hover:scale-150 transition-all"
        >
            {{ letter }}
        </router-link>
    </div>
    
    <Meals :meals="meals" />

 </template>
 
<script setup>
import { computed, watch } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';
import { onMounted } from 'vue';
import Meals from '../components/Meals.vue';

const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
const meals = computed(() => store.state.mealsByLetter);
const route = useRoute();

watch(route, () => {
    store.dispatch("searchMealsByLetter", route.params.letter);
})

onMounted(() =>{
    store.dispatch("searchMealsByLetter", route.params.letter);
})
</script>
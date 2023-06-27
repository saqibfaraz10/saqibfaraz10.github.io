<template >
    <div class="p-8 pb-0">
        <h1 class="text-4xl font-bold mb-4 text-lime-500">
            Meals for {{ ingredient.strIngredient }}
        </h1>
    </div>
   <Meals :meals = "meals" />
</template>
 
 <script setup>
import { computed, onMounted } from "vue"
import axiosClient from "../axiosClient"
import { ref } from "vue";
import { useRoute } from "vue-router";
import store from "../store";
import Meals from "../components/Meals.vue";

const route = useRoute();
const ingredient = computed(() => store.state.ingredient)
const meals = computed(() => store.state.mealsByIngredients)

onMounted(() => {
    store.dispatch('searchMealsByIngredients' , route.params.ingredients)
})
</script>
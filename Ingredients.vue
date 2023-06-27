<template >
  <div class="p-8">
    <h1 class="text-4xl font-bold mb-4 text-lime-500">Search Meals By Ingredients</h1>
    <input
      type="text"
      v-model="keyword"
      class="w-full text-black/[0.7] rounded border-2 border-lime-500 
      focus:ring-lime-500 mb-4"
      placeholder="Search for Ingredients"
    />
    <div class="grid grid-cols-1 md:grid-cols-3 gap-3">
        <a href="#"
        @click.prevent="openIngredient(ingredient)"
        v-for="ingredient of computedIngredients" 
        :key="ingredient.idIngredient"
        class="block bg-white rouned p-3 mb-3 shadow"
        >
        <h3 class="text-2xl font-bold mb-2">
            {{ ingredient.strIngredient }}
        </h3>
    </a>
    </div>
  </div>
</template>
 
 <script setup>
import { computed, onMounted } from "vue";
import axiosClient from "../axiosClient";
import { useRouter } from "vue-router";
import store from "../store";
import { ref } from "vue";

const router = useRouter();
const keyword = ref('')
const ingredients = ref([]);
const computedIngredients = computed(() => {
    if (!computedIngredients) return ingredients
    return ingredients.value.filter((i) => 
        i.strIngredient.toLowerCase().includes(keyword.value.toLowerCase())
        );
});

function openIngredient(ingredient){
    store.commit('setIngredients', ingredient)
    router.push({
        name: "byIngredients",
        params: {ingredients: ingredient.strIngredient}

    });
}

onMounted(() => {
  axiosClient.get("list.php?i=list").then(({ data }) => {
    ingredients.value = data.meals;
  });
});
</script>
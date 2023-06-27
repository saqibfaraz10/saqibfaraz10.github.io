<template>
  <header
    class="bg-lime-500 px-8 shadow h-14 flex justify-between items-center"
  >
    <router-link
      :to="{ name: 'home' }"
      class="inline-flex items-center h-full text-white hover:underline font-bold text-lg"
    >
      Home
    </router-link>
    <div class="hidden sm:block items-center">
      <router-link
        :to="{ name: 'byName' }"
        class="inline-flex items-center px-2 h-full text-black hover:bg-lime-500 hover:text-white transition-colors"
      >
        Search Meals
      </router-link>
      <router-link
        :to="{ name: 'byLetter' }"
        class="inline-flex items-center px-2 h-full text-black hover:bg-lime-500 hover:text-white transition-colors"
      >
        By Letter
      </router-link>
      <router-link
        :to="{ name: 'ingredients' }"
        class="inline-flex items-center px-2 h-full text-black hover:bg-lime-500 hover:text-white transition-colors"
      >
        By Ingredients
      </router-link>
    </div>

    <div class="relative flex sm:hidden">
      <button
        @click="toggleMenu"
        class="flex cursor-pointer hover:text-white items-center space-x-1 focus:outline-none"
      >
        <fa icon="bars" />
      </button>
      <div
        :class="{ hidden: isHidden }"
        class="absolute right-0 mt-6 bg-white border border-gray-300 
        rounded-md shadow-md"
        >
          <router-link 
          :to="{ name: 'byName' }"
          class="block px-4 py-2 text-gray-800 hover:bg-gray-200">
            Search by Name
          </router-link>

          <router-link
          :to="{ name: 'byLetter' }" 
          class="block px-4 py-2 text-gray-800 hover:bg-gray-200">
            Search by Letter
          </router-link>
 
          <router-link
          :to="{ name: 'ingredients' }" 
          class="block px-4 py-2 text-gray-800 hover:bg-gray-200">
            Search by Ingredient
          </router-link>

      </div>
    </div>
  </header>
</template>


<script setup>
import { onMounted, ref } from "vue";

const isHidden = ref(true);
const toggleMenu = () => {
  isHidden.value = !isHidden.value;
};

onMounted(() =>{
  const isHidden = ref(true);
})
</script>

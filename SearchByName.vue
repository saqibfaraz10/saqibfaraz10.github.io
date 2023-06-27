<template >
  <div class="p-8 pb-0">
    <input
      type="text"
      v-model="keyword"
      class="w-full text-black/[0.7] rounded border-2 
      border-lime-500 focus:ring-lime-500"
      placeholder="Search for Meal"
      @change="searchMeals"
    />
  </div>
  <Meals :meals = "meals" />
</template>
 
 <script setup>
import { computed, ref, onMounted} from "vue";
import store from "../store";
import { useRoute } from "vue-router";
import Meals from "../components/Meals.vue";

const keyword = ref("");
const meals = computed(() => store.state.searchedMeals);
const route = useRoute();

function searchMeals() {
  if(keyword.value){
    store.dispatch("searchMeals", keyword.value);
  }else{
    store.commit("setSearchedMeals", []);
  }
  
}

onMounted(() =>{
    keyword.value = route.params.name
    if(keyword.value){
        searchMeals()
    }
})
</script>
<template>
  <div id="app">
    <h1>Pizza Recipes</h1>
    <pagination-box :currentPage="currentPage" :totalPages="totalPages" @page-changed="onPageChanged" />
    <div class="Menu">
      <recipe-card v-for="recipe in paginatedRecipes" :key="recipe.id" :recipe="recipe" />
    </div>
  </div>
</template>

<!-- <script>
import axios from 'axios';
import RecipeCard from './components/RecipeCard.vue';
import PaginationBox from './components/PaginationBox.vue';

export default {
  components: {
    RecipeCard,
    PaginationBox
  },
  data() {
    return {
      recipes: [],
      currentPage: 1,
      itemsPerPage: 6
    };
  },
  computed: {
    paginatedRecipes() {
      const startIndex = (this.currentPage - 1) * this.itemsPerPage;
      return this.recipes.slice(startIndex, startIndex + this.itemsPerPage);
    },
    totalPages() {
      return Math.ceil(this.recipes.length / this.itemsPerPage);
    }
  },
  async created() {
    await this.fetchRecipes();
  },
  methods: {
    async fetchRecipes() {
      try {
        const response = await axios.get('https://dummyjson.com/recipes');
        this.recipes = response.data.recipes;
        console.log(this.recepies)
      } catch (error) {
        console.error('Error fetching recipes:', error);
      }
    },
    onPageChanged(page) {
      this.currentPage = page;
    }
  }
};
</script> -->
<script setup>
import { ref, computed, onMounted } from 'vue';
import axios from 'axios';
import RecipeCard from './components/RecipeCard.vue';
import PaginationBox from './components/PaginationBox.vue';

const recipes = ref([]);
const currentPage = ref(1);
const itemsPerPage = 6;

const paginatedRecipes = computed(() => {
  const startIndex = (currentPage.value - 1) * itemsPerPage;
  return recipes.value.slice(startIndex, startIndex + itemsPerPage);
});

const totalPages = computed(() => {
  return Math.ceil(recipes.value.length / itemsPerPage);
});

onMounted(async () => {
  await fetchRecipes();
});

const fetchRecipes = async () => {
  try {
    const response = await axios.get('https://dummyjson.com/recipes');
    recipes.value = response.data.recipes;
  } catch (error) {
    console.error('Error fetching recipes:', error);
  }
};

const onPageChanged = (page) => {
  currentPage.value = page;
};
</script>

<style>
#app {
  font-family: 'Inter Variable', sans-serif;
  margin-top: 50px;
}
h2,h1{
  text-align: center;
}
.Menu{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 20px;
}
</style>

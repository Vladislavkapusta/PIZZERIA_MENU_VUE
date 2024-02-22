<template>
    <div class="recipe-card">
    <img :src="recipe.image" alt="pizza_pic">
      <h2>{{ recipe.name }}</h2>
      <p>Difficulty: {{ recipe.difficulty }}</p>
      <p>Cuisine: {{ recipe.cuisine }}</p>
      <p>Calories per Serving: {{ recipe.caloriesPerServing }}</p>
      <b>ingredients:</b>
      <ul class="ingredients">
        <li v-for="ingredient in recipe.ingredients" :key="ingredient">{{ ingredient }}</li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      recipe: Object
    }
  };
  </script>
  
  <style scoped>
  h2{
    color: rgb(0, 0, 0);
    font-size: 16px;
    line-height: 19px;
    letter-spacing: 0%;
  }
  p{
    margin: 0 0 10px 10px;
    text-align: left;

    font-size: 12px;
    line-height: 15px;
    letter-spacing: 0%;
  }
  b{
    text-align: left;
    margin: 0 0 0 10px;

    font-size: 12px;
  }
  img{
    width: 224px;
    height: 176px;
    border-radius: 25px 25px 0px 0px;
  }
  .recipe-card {
    border: 1px solid #ccc;
    padding-bottom: 7px;
    margin-bottom: 20px;
    width: 224px;
    margin: 0 auto;

    box-sizing: border-box;
    border: 1px solid rgb(228, 228, 228);
    border-radius: 25px;
    box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
    background: rgb(255, 255, 255);


  }
  .ingredients{
    margin-top: 0;
    text-align: start;

    font-size: 12px;
    font-weight: 400;
    line-height: 15px;
    letter-spacing: 0%;
  }
  </style>
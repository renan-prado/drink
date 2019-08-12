
<script>

/* eslint-disable */

export default {
  name: 'SearchResultItem',
  props: ['drink'],

};
</script>

<template>
  <div class="search-result-item">

    <div class="search-result-item__left grid-5">
      <img :src="drink.strDrinkThumb" :alt="drink.strDrink">
    </div>

    <div class="search-result-item__right grid-7">
      <h2> {{ drink.strDrink }} </h2>

      <h3> Ingredientes </h3>

      <ul>
        <li :key="ingredient" v-for="ingredient in drink.ingredients"> {{ ingredient }} </li>
      </ul>

      <div class="search-result-item__description--desktop">
        <h3> Modo de preparo </h3>
        <label> {{ drink.strInstructions }} </label>
      </div>

    </div>

    <div class="search-result-item__description--mobile">
      <h3> Modo de preparo </h3>
      <label> {{ drink.strInstructions }} </label>
    </div>

  </div>
</template>

<style scoped lang="scss">
@import "@/assets/sass/components/searchResultItem.scss";
</style>

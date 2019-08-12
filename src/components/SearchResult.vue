
<script>
/* eslint-disable */
import SearchResultItem from '@/components/SearchResultItem.vue';

export default {
  name: 'SearchResult',
  props: ['drinks'],
  components: {
    SearchResultItem,
  },
};

</script>

<template>
  <div class="search-result">
    <div class="container">

      <div v-if="drinks.length > 0">
        <search-result-item :drink="drink" :key="drink.idDrink" v-for="drink in drinks"></search-result-item>
      </div>

      <div class="search-result__empty" v-else>
        <label> Nenhum Resultado encontrado </label>
      </div>

    </div>
  </div>
</template>

<style scoped lang="scss">
  .search-result__empty {
    text-align: center;
  }
</style>
